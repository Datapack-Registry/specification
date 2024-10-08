# Function Documentation Format
## Function Headers
A function always begins with a function header, which is a series of comments that describe its purpose, context, and interface:

```mcfunction
#> namespace
# This description should always reflect what the function should do.
#
# Not what the function is doing.
#
# @param {string} macroName Description of macroName
```

The first line of the function header is preceded by `>` and contains nothing but the namespace of the function:
```mcfunction
#> namespace
```

The next section of the function header is a description of the function's purpose. This can be split into multiple paragraphs:
```mcfunction
# This description should always reflect what the function should do.
#
# Not what the function is doing.
```
> Use the default Markdown syntax for additional styling.

Following the description is a series of annotation tags that define the function's interface:

```mcfunction
# @param {string} macroName Description of macroName
```

## Function Annotations
### `@api`
#### Description
Declares that the function is an API function. API functions are based on public functions, but are usually exposed as part of a versioned API that attempts to abstract the core logic to remain backward compatible where possible. API functions are otherwise virtually identical to public functions.

#### Syntax
```
@api
```

#### Example
```mcfunction
#> namespace
# This function is part of an API.
#
# @api

scoreborad players set $api.internal api 42
```

---

### `@deprecated`
#### Description
Declares that this function should no longer be used and may be removed in a future version of the datapack.
It is always recommended to specify a replacement function that should be used instead.

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

```mcfunction
#> namespace
# This function loggs the current player in the chat.
#
# @depricated This function is obsolete now.

say @s
```

---

### `@param`
#### Description
The `@param` annotation specifies the name, type and description of a function parameter.

#### Syntax
```
@param {<type>} <name> <description>
```

#### Example
```mcfunction
#> namespace
# This function greets a user.
#
# @param {string} user The name of the user.

$say Hey, $(user).
```

```mcfunction
#> namespace
# This function displays an array of numbers.
#
# @param {int[]} numbers List of numbers to display.

$say These are the numbers: $(numbers)
```

---

### `@public`
#### Description
Declares that this function should/may be called outside the datapack. For example, by the player or in a command block. These functions should be simple and clearly structured so that they can be used easily from the outside.

#### Syntax
```
@public
```

#### Example
```mcfunction
#> namespace
# This function can be called from a command block.
#
# @public

say Hey, @s.
```

---

### `@reads`
#### Description
Declares that this value is being read by the function. The syntax is identical to [`@writes`](#writes).

#### Syntax
```
@reads {storage|scoreboard} <id> [<path>|<entity>]
```

#### Example
```mcfunction
#> namespace
# This function reads from a storage and returns that value.
#
# @reads {storage} namespace:example path

return run data get storage namespace:example path
```

```mcfunction
#> namespace
# This function reads from a scoreboard and returns that value.
#
# @reads {scoreboard} namespace.example @s

return run scoreboard players get @s namespace.example
```

---

### `@returns`
#### Description
Declares the return value of the function. The return value can either be a boolean value, such as `fail` (falsy) or an integer (truthy), or just an integer (int).

#### Syntax
```
@returns {boolean|int} <description>
```

#### Example
```mcfunction
#> namespace
# This function always fails.
#
# @returns {boolean} The failed function 

return fail
```

```mcfunction
#> namespace
# This function always returns 42.
#
# @returns {int} The number 42.

return 42
```

---

### `@see`
#### Description
Declares a reference to refer to another function that may be related to the one being documented.

#### Syntax
```
@see <path>
```

#### Example
```mcfunction
#> namespace
# This function references an other function.
#
# @see namespace:path/to/other/function
```

---

### `@this`
#### Description
Declares what the keyword this refers to when it is used within the function. It is often necessary to mark an entity with the "this" tag in order to be able to refer to it later.

#### Syntax
```
@this <entity> [<description>]
```

#### Example
```mcfunction
#> namespace
# This function says who is 'this'.
#
# @this player The player that triggered the advancement.

say @a[tag=this] is the current 'this' reference.
```

---

### `@writes`
#### Description
Declares that this value is being written by the function. The syntax is identical to [`@reads`](#reads).

#### Syntax
```
@writes {storage|scoreboard} <id> [<path>|<entity>]
```

#### Example
```mcfunction
#> namespace
# This function writes to a storage.
#
# @writes {storage} namespace:example path

data modify storage namespace:example path set value 42
```

```mcfunction
#> namespace
# This function writes to a scoreboard.
#
# @writes {scoreboard} namespace.example @s

scoreboard players set @s namespace.example 42
```
