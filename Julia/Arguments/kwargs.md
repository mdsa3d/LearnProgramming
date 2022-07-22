# Keyword Arguments (kwargs)

## Why kwargs?
**kwargs are good if you don't know in advance the name of the parameters. For example the dict constructor uses them to initialize the keys of the new dictionary. It is often used if you want to pass lots of arguments to another function where you don't necessarily know the options.

## Sample Codes
```julia
julia> function som(a,b)
           println(a + b)
           end
som (generic function with 1 method)
```
When kwargs are supplied as dictionary
```julia
julia> kwarg = Dict(:a=>arg1, :b=>arg2)
Dict{Symbol, Int64} with 2 entries:
  :a => 1
  :b => 2

julia> som(;kwarg...)
3
```
When supplied as `tuple`
```julia
julia> kwarg = (arg1,arg2)
(1, 2)

julia> som(kwarg...)
3
```
When supplied as `vector`
```julia
julia> kwarg = [arg1;arg2]
2-element Vector{Int64}:
 1
 2

julia> som(kwarg...)
3
```
## References:
- [Why kwargs](https://stackoverflow.com/questions/1415812/why-use-kwargs-in-python-what-are-some-real-world-advantages-over-using-named)