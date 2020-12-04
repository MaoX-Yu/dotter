# What is Dotter?
Dotter is a dotfile manager and templater.

Dotfiles are *configuration* files that usually live in the home directory and start with a dot.
Often times, it is desirable to have a backup of all the configurations on your system, which is why a lot of users have their dotfiles saved in a git repository, then symlinking them to their target locations using `ln -s`.

However, there are several issues with that barebones approach:
- Hard to keep track of what comes from where once you have more than a handful of dotfiles
- Tedious to setup on a new machine - you need to manually create every single link
- No real way to handle differences between machines - say you want the battery meter on your bar to not appear on your desktop machine

Dotter aims to solve all those problems by providing a flexible configuration and automatic templating or symlinking to the target locations.

⚠️ **THIS PROJECT IS UNDER HEAVY DEVELOPMENT**. I use it regularly myself so it's reasonably tested, but expect bugs to happen.
If you find a bug, please open an issue describing how to reproduce it, and it will get fixed.\
I create Releases often so make sure you check whether the bug was fixed in the latest one!

# Installation
## Arch Linux
The following AUR packages are available:
- [dotter-rs-bin](https://aur.archlinux.org/packages/dotter-rs-bin) for a precompiled version of the latest release
- [dotter-rs](https://aur.archlinux.org/packages/dotter-rs) for the latest release's source that is built on your machine
- [dotter-rs-git](https://aur.archlinux.org/packages/dotter-rs-git) for the latest commit on master that is built on your machine

All of those are maintained by [orhun](https://github.com/orhun/) - huge thanks to him!

## Others

Download the binary for your platform from the latest release and then put it in your `$PATH` or in your dotfile repository (then you'd run it with `./dotter`).
Alternatively, Dotter is on [crates.io](https://crates.io/crates/dotter), so if you have Rustup installed, run `cargo install dotter`.

# Wiki
Check out [the wiki](https://github.com/SuperCuber/dotter/wiki) for more information.
Among other things, it explains how to setup and configure Dotter, as well as giving insight on how the templating and deployment works.

# Usage
Now that you've configured all the global and local file sections, you can simply run `dotter` from within your repository.\
All the files will be deployed to their target locations.

Check out `dotter -h` for the command-line flags that Dotter supports:

```
Dotter 0.10.4
A small dotfile manager. Note that flags and options have to come BEFORE subcommands

USAGE:
    dotter.exe [FLAGS] [OPTIONS] [SUBCOMMAND]

FLAGS:
        --dry-run    Dry run - don't do anything, only print information. Implies RUST_LOG=info unless specificed
                     otherwise
        --force      Force - instead of skipping, overwrite target files if their content is unexpected. Overrides
                     --dry-run and implies RUST_LOG=warn unless specified otherwise
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
        --cache-directory <cache-directory>    Directory to cache into [default: .dotter/cache]
        --cache-file <cache-file>              Location of cache file [default: .dotter/cache.toml]
    -g, --global-config <global-config>        Location of the global configuration [default: .dotter/global.toml]
    -l, --local-config <local-config>          Location of the local configuration [default: .dotter/local.toml]

SUBCOMMANDS:
    deploy      Deploy the files to their respective targets. This is the default subcommand
    diff        Print the differences that will result when running a deploy (in templates only). Does not actually
                execute the deploy
    help        Prints this message or the help of the given subcommand(s)
    init        Initialize global.toml with a single package containing all the files in the current directory
                pointing to a dummy value and a local.toml that selects that package
    undeploy    Delete all deployed files from their target locations. Note that this operates on all files that are
                currently in cache
    watch       Run continuously, watching the repository for changes and re-deploying as soon as they happen
```

Dotter uses the `env_logger` rust library for displaying errors and warnings. To configure logging level, use the `RUST_LOG` environment variable. The options are, in order of least verbose to most verbose: `error`, `warn`, `info`, `debug`, `trace`. The default is `error`.

# Contributing
Contributions to Dotter are welcome, whether in the form of a pull request or an issue (for bug repots, feature requests, or other helpful comments)

# Support
Like what I do and want to encourage me to continue?\
You can donate a small amount via [Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=329HKDXK9UB84).\
Donations are not expected but greatly appreciated.
