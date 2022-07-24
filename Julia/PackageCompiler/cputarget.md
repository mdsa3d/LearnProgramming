# CPU target
```julia
create_sysimage(packages::Vector{String}; kwargs...)
```
Create a system image that includes the package(s) in `packages` (given as a
string or vector). If the `packages` argument is not passed, all packages in the
project will be put into the sysimage.
An attempt to automatically find a compiler will be done but can also be given
explicitly by setting the environment variable `JULIA_CC` to a path to a
compiler (can also include extra arguments to the compiler, like `-g`).
### Keyword arguments:
- `sysimage_path::String`: The path to where the resulting sysimage should be saved.
- `project::String`: The project that should be active when the sysimage is created,
  defaults to the currently active project.
- `precompile_execution_file::Union{String, Vector{String}}`: A file or list of
  files that contain code from which precompilation statements should be recorded.
- `precompile_statements_file::Union{String, Vector{String}}`: A file or list of
  files that contain precompilation statements that should be included in the sysimage.
- `incremental::Bool`: If `true`, build the new sysimage on top of the sysimage
  of the current process otherwise build a new sysimage from scratch. Defaults to `true`.
- `filter_stdlibs::Bool`: If `true`, only include stdlibs that are in the project file.
  Defaults to `false`, only set to `true` if you know the potential pitfalls.
- `include_transitive_dependencies::Bool`: If `true`, explicitly put all
   transitive dependencies into the sysimage. This only makes a difference if some
   packages do not load all their dependencies when themselves are loaded. Defaults to `true`.
### Advanced keyword arguments
- `base_sysimage::Union{Nothing, String}`: If a `String`, names an existing sysimage upon which to build
   the new sysimage incrementally, instead of the sysimage of the current process. Defaults to `nothing`.
   Keyword argument `incremental` must be `true` if `base_sysimage` is not `nothing`.
- `cpu_target::String`: The value to use for `JULIA_CPU_TARGET` when building the system image. Defaults
  to `native`.
- `script::String`: Path to a file that gets executed in the `--output-o` process.
- `sysimage_build_args::Cmd`: A set of command line options that is used in the Julia process building the sysimage,
  for example `-O1 --check-bounds=yes`.


-----------
`default cpu_target` in PackageCompiler is `native`, so it will build the image specific to your exact CPU. You can change it to different target, using the following below:

```julia
cpu_target="x86-64"
# or
cpu_target = PackageCompiler.default_app_cpu_target()

PackageCompiler.create_sysimage(;cpu_target=cpu_target)
```
```julia
# See https://github.com/JuliaCI/julia-buildbot/blob/489ad6dee5f1e8f2ad341397dc15bb4fce436b26/master/inventory.py
function default_app_cpu_target()
    Sys.ARCH === :i686        ?  "pentium4;sandybridge,-xsaveopt,clone_all"                        :
    Sys.ARCH === :x86_64      ?  "generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)"  :
    Sys.ARCH === :arm         ?  "armv7-a;armv7-a,neon;armv7-a,neon,vfp4"                          :
    Sys.ARCH === :aarch64     ?  "generic"   #= is this really the best here? =#                   :
    Sys.ARCH === :powerpc64le ?  "pwr8"                                                            :
        "generic"
end
```

## References
- [Define cpu target](https://github.com/JuliaLang/PackageCompiler.jl/issues/488)
- [working with cpu target](https://github.com/NHDaly/ApplicationBuilder.jl/commit/54dd856c05c408a59cf59408fdfb7938a224db23)
- [Application builder](https://github.com/NHDaly/ApplicationBuilder.jl/issues/30)
- [Unable to find compatible target in system image](https://discourse.julialang.org/t/unable-to-find-compatible-target-in-system-image/52879/6)
- [Unable to find compatible target in system image 01](https://github.com/JuliaLang/julia/issues/30001)