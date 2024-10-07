# Function Documentation Format
## Function Headers
A function always begins with a function header, which is a series of comments that describe its purpose, context, and interface:

```mcfunction
#> namespace
# This description should always reflect what the function should do.
#
# Not what the function is doing.
#
# @param {string} macroName - Description of macroName
```

The first line of the function header is preceded by > and contains nothing but the namespace of the function:
```mcfunction
#> namespace
```

The next section of the function header is a description of the function's purpose. This can be split into multiple paragraphs:
```mcfunction
# This description should always reflect what the function should do.
#
# Not what the function is doing.
```
> Newlines can be achived by adding two spaces (`  `) at the end of the line.

Following the description is a series of annotation tags that define the function's interface:

```mcfunction
# @param {string} macroName - Description of macroName
```

## Function Annotations
