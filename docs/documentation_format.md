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
The [`@deprecated`](#deprecated) annotaion marks a function as being deprecated. Always provide a reference to the new function if there is one.

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
Describing that this function gets called by an advancement.

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

### `@example`
Provide an example on how to use the function.

#### Syntax
````
@example
```mcfunction
code
```
````

#### Example
```mcfunction
#> namespace
# This is an example function.
#
# @example
# ```mcfunction
# execute as @a run function namespace:example
# ```

say Hey it's me, @s!
```

### `@generator`
The [`@generator`](#generator) annotation indicates that this function generates something.

#### Syntax
```
@generator [<text>]
```

#### Example
```mcfunction
#> namespace
# This function generates a random number.
#
# @generator Generates a random number.

return run random
```

### `@param`
The [`@param`](#param) annotation provides the name, type, and description of a function parameter. The [`@param`](#param) annotation requires you to specify the name, type, and description of the parameter you are documenting.

#### Syntax
```
@param {type} <name> <description>
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

### `@public`
The [`@public`](#public) annotation indicates that a function should be documented as if it were public. That means that this function can be called from outside (ex. in-game).

#### Syntax
```
@public
```

#### Example
```mcfunction
#> namespace
# This function can be called from in-game.
#
# @public

say Hey, @s.
```

### `@returns`
The [`@returns`](#returns) annotation documents the value that the function returns.

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

### `@see`
The [`@see`](#see) annotation allows you to refer to another function that may be related to the one being documented.

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

### `@this`
The [`@this`](#this) annotation indicates what the this keyword refers to when used within the function. Often times you need to tag an entity with the `this` tag in order to reference it later.

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
