# JSON versions
- **JSON.jl** <br> It has been around the longest; takes a very simple, straightforward approach to json parsing/writing, nothing fancy or custom for native Julia objects

- **JSON2.jl** <br> It was started w/ an idea to use generated functions for custom Julia types to generate specialized JSON parsing/writing code that could be much faster than JSON.jl; it was an experiment that worked fairly well, but can incur expensive compilation costs for complex/highly nested objects

- **JSON3.jl** <br> It is a successor of JSON2.jl that took some similar ideas (support for custom object serialization/deserialization), but aims to fix the compilation cost issue by being smarter, and also provides a hybrid lazy parsing approach for generic objects/arrays that is faster than any other solution