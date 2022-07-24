# **Working with DataFrame and JSON**
Here we are going to discuss few approaches to work with DataFrames and JSON hand-in-hand.
## Convert JSON string to DataFrame
```julia
# json source can be array of objects, or object of arrays
using JSONTables, DataFrames
df = DataFrame(jsontable(json_source))
```

## Write out a DataFrame as an array of objects
```julia
using JSONTables
arraytable(df)
```
## Write out a DataFrame as an object of arrays
```julia
using JSONTables
objecttable(df)
```

## **References:**
- [Import DataFrame from JSON File](https://discourse.julialang.org/t/dataframes-best-way-to-import-from-json-format-file/29946)