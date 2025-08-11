trizen
======

trizen is a lightweight wrapper for AUR, written in Perl.

Main features include:

* Installation of packages from the AUR
* Search support for AUR packages
* Reading AUR comments for packages
* Upgrade support for AUR packages
* Recursive resolver of AUR dependencies
* Built-in interaction with 'pacman'
* Edit support for text files
* Input/output UTF-8 support

# INSTALLATION

* Tagged version:
```bash
git clone https://aur.archlinux.org/trizen.git
cd trizen
makepkg -si
```

* `-git` version:

```bash
git clone https://aur.archlinux.org/trizen-git.git
cd trizen-git
makepkg -si
```

# Screenshots

#### Search results

![trizen -Ss youtube](https://user-images.githubusercontent.com/614513/32417050-f5e5a310-c25b-11e7-8598-056431ce9a1d.png)

#### Package info

![trizen -Si sidef](https://user-images.githubusercontent.com/614513/32417040-d137a68a-c25b-11e7-89f3-362b084b8873.png)

#### Options

![trizen -h](https://user-images.githubusercontent.com/614513/34314381-d7e4df12-e77b-11e7-84f3-322444c17824.png)

![trizen -Sh](https://user-images.githubusercontent.com/614513/34314382-d98a810a-e77b-11e7-9df0-64af9f5f3633.png)

# Usage

```
usage: trizen [options] [pkgname] [pkgname] [...]

Main options:

    -S, --sync         : install packages (see: trizen -Sh)
    -C, --comments     : display AUR comments for a package
    -G, --get          : clones a package in the current directory
    -R, --remove       : remove packages from the system (see: pacman -Rh)
    -Q, --query        : query the package database (see: pacman -Qh)
    -F, --files        : query the files database (see: pacman -Fh)
    -D, --database     : operate on the package database (see: pacman -Dh)
    -T, --deptest      : check dependencies (see: pacman -Th)
    -U, --upgrade      : install built packages from '--clone-dir' or `pwd`

Other options:

    -q, --quiet        : do not display any warnings
    -r, --regular      : use only the regular repositories
        --stats        : show stats about the installed packages
        --nocolors     : disable text colors
        --forcecolors  : force colors when not writing to STDOUT
        --debug        : activate the debug/verbose mode
        --help         : print this message and exit
        --version      : print version and exit

See also:

    trizen -Sh
    trizen -Gh

:: Each configuration key is a valid option when preceded with '--'
```

# Sync options (`-S`)

```
usage: trizen {-S --sync} [options] [package(s)]

Main options:

  -s, --search        : search for packages
  -i, --info          : show info for packages
  -m, --maintainer    : show packages maintained by <username>
  -p, --pkgbuild      : show PKGBUILD only
  -l, --local         : build and install packages from `pwd`
  -u, --sysupgrade    : upgrade installed packages
  -y, --refresh       : refresh package databases (with: -u)
  -c, --clean         : clean the cache directory of `trizen` and `pacman`
  -a, --aur           : only AUR operations (with: -c, -u, -s, -i)

Other options:

      --devel         : update VCS packages during -Su
      --show-ood      : show out-of-date flagged packages during -Su
      --noinfo        : do not display package info after cloning
      --nopull        : do not `git pull` new changes
      --noedit        : do not prompt to edit files
      --nobuild       : do not build packages (implies --noedit)
      --noinstall     : do not install packages after building
      --nocheck       : do not check() packages or install check dependencies
      --needed        : do not reinstall up-to-date packages
      --asdeps        : install packages as non-explicitly installed
      --asexplicit    : install packages as explicitly installed
      --skipinteg     : pass the `--skipinteg` argument to `makepkg`
      --noconfirm     : do not ask for any confirmation
      --movepkg       : move built packages into pacman's cache directory
      --movepkg-dir=s : move built packages in this directory (implies --movepkg)
      --clone-dir=s   : directory where to clone and build packages
      --editor=s      : editor command used to edit build files
      --pager-mode    : display the build files of a package in pager mode
      --pager=s       : pager command used to display the build files
      --ignore=s      : space-separated list of packages to ignore during -Su

Examples:

    trizen -S  <package>     # install <package>
    trizen -Ss <keyword>     # search for <keyword>
    trizen -Si <package>     # show info about <package>
```

# Get options (`-G`)

```
usage: trizen {-G --get} [options] [package(s)]

Main options:

    -d, --with-deps     : clones a package with all needed AUR dependencies

Examples:

    trizen -G  <package>     # clones <package>
    trizen -Gd <package>     # clones <package> along with its AUR dependencies
```

A configuration file is automatically generated at: `~/.config/trizen/trizen.conf`
