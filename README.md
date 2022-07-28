# apktoys

personal collection of packaging helpers

## usage

1. edit `apktoys` to change the `APORTS_DIRECTORY` variable to your aports directory. (you can also pass a custom APORTS_DIRECTORY by setting the variable when calling any of these tools.)
2. add `source /path/to/apktoys` to your bashrc. alternatively, run `apktoys <tool>`.

## tools

**note**: `<package>` takes either `repository/pkgname` (e.g. `community/xfce4-weather-plugin`) or just `pkgname` as an argument.

* `at-newpkg <package> [<package> <package> ...]` - takes package names and commits the packages with the given names.
* `at-upgrade <package> <version>` - shorthand for `at-commit upgrade <package> <version>`, you still need to do everything else manually.
* (TODO) `at-move <source-repository>/<package> <target-repository>` - moves a package from one repository to another.
* `at-commit <template> <package> [data] [--amend/-m]` - runs a git commit from a given template. `<template>` is one of `upgrade`, `move`. `[data]` is used differently depending on the template: for `upgrade` it's the new version, for `move` it's the old repository.
* (TODO) `at-lint [<package>]` - lints a package and checks for common errors. if no package is provided, assumes current directory. reccomended to set as a pre-commit hook.
* (TODO) `at-commit-lint [<commit>]` - checks if the commit is correct, i.e. only contains what needs to be contained. if commit is not provided, assumes latest commit. reccomended to set as a post-commit hook.
* `at-install-makedepends [<package>]` - installs depends, makedepends and checkdepends for the package. if package name is not provided, assumes name from current working directory.
* `at-uninstall-makedepends [<package>]` - uninstalls makedepends installed with `at-install-makedepends`.
* `at-repoforpkg <package>` - returns a string like `repository/pkgname`. usually used internally for the other commands, but may be useful in other cases.
