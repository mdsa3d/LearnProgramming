# Pandas DataFrame to Julia native DataFrame

## Get Julia DataFrame from Pandas DataFrame
```julia
using Pandas
df = read_csv(filepath)
dictPandas = Pandas.to_dict(data, orient="records")
juliaDF = reduce(vcat, DataFrame.(dictPandas), cols=:union) #julia DataFrame
```


## Working with pandas operations
This can be used if you want to select a subdataframe from pandas for julia operations.
```julia
using Pandas
df = read_csv(filepath)
r,c = size(df)
data=iloc(df)[1:10,2:c]
```