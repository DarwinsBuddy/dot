
# dot
A simple bash script for managing my dotfiles with stow

## Dependencies
`stow`

## Usage
###  Commands
#### Listing packages
* `dot l | list` **List all available packages** for installing into your environment if no packages are given
* `dot l | list <package1> <package2> <...>` **Lists contained files of all given packages**
* `dot i | install [-a|--all] [-f | --force] <package1> <package2> <...>` **Install provided packages** from your dotfiles repository into `$HOME`. When given `-a`or `--all` installs all available packages from `$HOME` (except packages which start with `_`, see: _Device specific packages_). When given `-f | --force` force install of _Device specific packages_
* `dot r | remove [-a|--all] [-f | --force] <package1> <package2> <...>` **Remove provided packages** from your `$HOME`repository (Note: your config files in your dotfiles repository won't be touched. It's a fancy alias for un-stowing). When given `-a`or `--all` remove all available packages from `$HOME` (except packages which start with `_`, see: _Device specific packages_). When given `-f | --force` force remove of _Device specific packages_
* `dot c | create <package_name>` **Create a package** with name `<package_name>` if it doesn't yet exist (Will not overwrite existing packages) (See _Device specific packages_ for special use cases)
* `dot a | add <package_name> <file1> <file2> <...>` **Add given files to package** `<package_name>` (This is an alias for moving the file incl. respective folder structure relative to `$HOME` into package `<package_name>` and reinstalling the whole package in order to create corresponding symlinks with stow)

### Options
* `dot -h |--help` Show help Usage: _standalone_²
* `dot -d | --dry-run` Dry-Run¹ Usage: All _commands_
* `dot -f | --force`  When given `-f | --force` force install/remove of _Device specific packages_ Usage: `install | remove`
* `dot -v | --verbose` Logs verbosely (If something doesn't work out as intended use it with every _command_ to get more information about what went wrong

### Device specific packages
Packages starting with a leading `_` are _device specific_ packages. In some cases, you want to install all your loved configs and packages at once, but there may be some issues, which are hardware/device dependent. For this use-case you can create packages with leading `_` which you can install/uninstall manually using the `-f` or `--force` flags.  

#### TODO
- [ ] Add AUR package and setup procedure (atm included in `install`)
- [ ] Add check for dependencies at start of script invocation
- [ ] ¹ Improve dry-run feature (as this is currently for development only and may not work with every command)
- [ ] ² Add command-specific help