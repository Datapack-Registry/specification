# Naming Conventions & Recommendations
## Documentation
The [documentation format](./documentation_format.md) is recommended for maintaining well-documented functions.

## Files
### Name
The name of function files and folders should only contain the following characters: `a-z`, `0-9`, `_` and `.`. The reason for this is that different operating systems treat file and folder names differently due to casing or certain special characters.
The restriction to this set of characters ensures that files and folders are treated the same on all operating systems and that it is universally readable.

Globally predefined function file names:
- `load.mcfunction` This file is called at every start
- `tick.mcfunction` This file is called every tick

### Structure
Function files and folders should be written in [snake_case](https://en.wikipedia.org/wiki/Snake_case). Numbers within the function or folder name should not be used for numbering in order to enforce a certain structure.

Try to organize your files into "modules". Modules are folders which contain either/or a `tick.mcfunction` and `load.mcfunction` function file.
The `tick.mcfunction` function file serves as the "entry point" for the module and the `load.mcfunction` function file serves as the "setup".

## Content
### User Interaction
