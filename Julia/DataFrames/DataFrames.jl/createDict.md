# Create Dictionary from DataFrame (julia)

```julia
using DataFrames
df = DataFrame(id=[1, 2, 3, 4], value=["Rajesh", "John", "Jacob", "sundar"], other=[0.43, 0.42,0.54, 0.63])

│ Row │ id    │ value  │ other   │
│     │ Int64 │ String │ Float64 │
├─────┼───────┼────────┼─────────┤
│ 1   │ 1     │ Rajesh │ 0.43    │
│ 2   │ 2     │ John   │ 0.42    │
│ 3   │ 3     │ Jacob  │ 0.54    │
│ 4   │ 4     │ sundar │ 0.63    │
```

To make a dictionary from a data frame you could write:
```julia
julia> Dict(pairs(eachcol(df)))
Dict{Symbol,AbstractArray{T,1} where T} with 3 entries:
  :value => ["Rajesh", "John", "Jacob", "sundar"]
  :id    => [1, 2, 3, 4]
  :other => [0.43, 0.42, 0.54, 0.63]
```

However, what you ask for is making a dictionary from a vector (that just happens to be stored in a data frame), which you can do in the following way (the pattern is very similar, but just applied to a vector):
```julia
julia> Dict(pairs(df.value))
Dict{Int64,String} with 4 entries:
  4 => "sundar"
  2 => "John"
  3 => "Jacob"
  1 => "Rajesh"
```
and if you want a mapping from :id to :value write (assumming :id is unique; again - it is just two vectors, the fact that they are stored in a data frame is not important here):
```julia
julia> Dict(Pair.(df.id, df.value))
Dict{Int64,String} with 4 entries:
  4 => "sundar"
  2 => "John"
  3 => "Jacob"
  1 => "Rajesh"
```

## References:
- [stackoverflow](https://stackoverflow.com/questions/63752067/how-to-create-dictionary-from-julia-dataframe)