# Naming Conventions & Recommendations
## Documentation
The [documentation format](./documentation_format.md) is recommended for maintaining well-documented functions.

## Files
### Name
The name of function files and folders should only contain the following characters: `a-z`, `0-9`, `_` and `.`. The reason for this is that different operating systems treat file and folder names differently due to casing or certain special characters.
The restriction to this set of characters ensures that files and folders are treated the same on all operating systems and that it is universally readable.

Globally predefined function file names:
- `load.mcfunction` This function is called at every start
- `tick.mcfunction` This function is called every tick

### Structure
Function files and folders should be written in [snake_case](https://en.wikipedia.org/wiki/Snake_case). Numbers within the function or folder name should not be used for numbering in order to enforce a certain structure.

Try to organize your files into "modules". Modules are folders which contain either/or a `tick.mcfunction` and `load.mcfunction` function file.
The `tick.mcfunction` function file serves as the "entry point" for the module and the `load.mcfunction` function file serves as the "setup".

## Content
### Uninstall or Removal
Your datapack should always provide a `namespace:uninstall` function for the user. This function is responsible for calling all the remove functions to leave no artifacts of the datapack behind. This function should also disable the datapack after calling all remove functions.

### Advancements
If your datapack creates advancements, the following functions should exist:

```yml
Datapack
├─ pack.mcmeta
└─ data
   └─ <namespace>
      ├─ advancement
      │  └─ <...>
      │     └─ <advancement name>.json
      └─ functio
         └─ app
            └─ advancement
               ├─ reset.mcfunction
               └─ <...>
                  └─ <advancement name>
                     └─ trigger.mcfunction
```

- `reset.mcfunction` This function should be called by the `load.json` file when the Datapack is started. All advancements for each player will get reset by this function.
- `trigger.mcfunction` This function should be called by the `<advancement name>.json` when the advancement triggers. The folder structure to this function should mimic the folder sructure to te actual advancement.

### Scoreboards
If your datapack creates scoreboards, the following functions should exist:

- `namespace:app/scoreboards/add` This function should be called by the `load.json` when the datapack is started. All scoreboards are created in this file and initial values are set for the scoreboards.
- `namespace:app/scoreboards/remove` This function should be called by the [`namespace:uninstall`](#uninstall-or-removal) function when the datapack is removed. In this file, all scoreboards that were previously created are removed so that no artifacts are left behind.

### Storages
If your datapack creates storages, the following functions should exist:

- `namespace:app/storage/add` This function should be called by the `load.json` file when the Datapack is started. All initial values for a storage are set in this file.
- `namespace:app/storage/remove` This function should be called by the [`namespace:uninstall`](#uninstall-or-removal) function when the datapack is removed. In this file, all storages that were previously created are removed so that no artifacts are left behind. It is also recommended to inform the user that after removing the storages the `storage_<namespace>.dat` inside the `saves/<world>` folder can be deleted, because Minecraft doesn't remove empty storage files by itself.

### Items
If your Datapack provides items for a player, the following functions should be available to the player:

- `namespace:items/give` Gives the player all available items provided by the datapack.
- `namespace:.../<module>/give` Gives the player all/the available items for the respective module. For example, `namespace:blocks/glowing_dirt/give` would give the player the items for the module `glowing_dirt`.

### ...
...
