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
### `@deprecated`
The `@deprecated` annotaion marks a function as being deprecated. Always provide a reference to the new function if there is one.

#### Syntax
```
@deprecated [<text>]
```

#### Example
```mcfunction
#> namespace
# This function loggs the current player in the chat.
#
# @depricated Use `namespace:path/to/new/function` instead.

say @s
```

### `@event`
The `@event` annotation provides a way of describing that this function gets called by an advancement.

#### Syntax
```
@event <path>
```

#### Example
```mcfunction
#> namespace
# This function gets triggered whenever a player is jumping.
#
# @event <namespace:path/to/advancement>

say @s Jumped!
```

