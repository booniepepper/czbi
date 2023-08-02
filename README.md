# czbi

## Clone, Zig Build, Install

Install Zig-built executables.

It works best for projects with standalone executables, simple dependencies,
and no other better way documented on how to install them.

I made this because there are many interesting executables being created that
are Zig projects (or use build.zig) and I want to try them out before they
stabilize or land in a Linux distro or something.

## Usage

```
czbi 1.0

USAGE: czbi REPO
       czbi home
       czbi uninstall EXE

czbi is a script for installing Zig-built executables. To customize it, edit
the script or fork the repository yourself.

czbi REPO
    Clone, zig build, and install whatever is produced by REPO. The clone
    and zig build happens in a directory prefixed by $XDG_DATA_HOME/czbi/$REPO
    or if XDG_DATA_HOME is unset/empty then $HOME/.local/share/czbi/$REPO

    If the REPO is in the format name/project then it's expanded as a github
    https url like https://github.com/name/project -- Other formats are passed
    to git clone directly.

    After a build, czbi will produce symbolic links in $HOME/.local/bin for any
    binaries found in a project-local zig-out/bin/ directory.

    Any conflicts are replaced with a warning.

czbi home
    Prints the directory czbi will use for cloning repositories.

czbi uninstall EXE
    Uninstall EXE by deleting a symlink at $HOME/.local/bin/$EXE
```

## Requirements

1. [bash](https://www.gnu.org/software/bash/)
2. [git](https://git-scm.com/)
3. [zig](https://ziglang.org/)

## Installing

The recommended way to install czbi is to run something like this in bash:

```
CZBI_HOME="${XDG_DATA_HOME:-"$HOME/.local/share"}/czbi"
CZBI_REPO="booniepepper/czbi"

mkdir -p "$CZBI_HOME"
cd "$CZBI_HOME"


```

## Notes on safety and being excellent

The czbi project makes zero guarantees of safety. Please be sure that you trust
a project before compiling it and executing it on your machine.

By using this software, you agree to not be a jerk. If someone has publically
shared their project on the internet, for you to use free of charge, but for
some reason or another that project cannot support czbi, please treat them with
respect. (For intentionally malicious stuff, then sure, report it or whatev.)

Some projects will have requirements that are not compatible with czbi, and
prevent the naive logic in this script from working. _(Examples: zigmod or
another package manager, using a different version of Zig than what you have
installed, requiring dependencies that aren't modeled, or having some difficult
to understand build process.)_

## Etc

Released under the terms of the [BSD 3-Clause license]()

A 2023 side quest of [J.R. Hill](https://so.dang.cool).

