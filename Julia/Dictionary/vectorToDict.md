# Create Dictionary from vectors


```julia
using DataFrames
df = DataFrame(id=[1, 2, 3, 4], value=["Rajesh", "John", "Jacob", "sundar"], other=[0.43, 0.42,0.54, 0.63])

function method1(data)
        return Dict(names(data) .=> eltype.(eachcol(data)))
end
```
```julia
function method2(data)
        return Dict(zip(names(data), eltype.(eachcol(data))))
end
```

Testigng both methods using BenchmarkTools
```julia
julia> using BenchmarkTools
julia> @benchmark method1(data)
BenchmarkTools.Trial: 10000 samples with 1 evaluation.
 Range (min … max):  37.200 μs …  5.942 ms  ┊ GC (min … max): 0.00% … 98.36%
 Time  (median):     40.100 μs              ┊ GC (median):    0.00%
 Time  (mean ± σ):   45.177 μs ± 82.349 μs  ┊ GC (mean ± σ):  2.51% ±  1.38%

  ▂▇█▇▆▅▅▅▄▃▃▂▁▁▁▁               ▂▂▂▁                         ▂
  ██████████████████▇▇▇▇▇▆▇▇▇▇▆▇▇██████▆▇▆▇█▇▆▇▇▆▇▆▅▆▇▅▆▆▆▅▆▆ █
  37.2 μs      Histogram: log(frequency) by time      85.2 μs <

 Memory estimate: 8.42 KiB, allocs estimate: 107.

julia> @benchmark method2(data)
BenchmarkTools.Trial: 10000 samples with 4 evaluations.
 Range (min … max):  7.200 μs …  1.637 ms  ┊ GC (min … max): 0.00% … 98.28%
 Time  (median):     7.525 μs              ┊ GC (median):    0.00%
 Time  (mean ± σ):   8.408 μs ± 20.745 μs  ┊ GC (mean ± σ):  3.41% ±  1.39%

  ▅█▆▅▄▄▄▄▃▃▂▂▁▁                                             ▁
  █████████████████▇████▇█▇█▇▇▇▇▇▇▇▇█▇▇▇▆▅▆▇▆▆▆▆▅▅▅▅▄▅▄▄▅▄▃▅ █
  7.2 μs       Histogram: log(frequency) by time     15.2 μs <

 Memory estimate: 3.66 KiB, allocs estimate: 54.
 ```