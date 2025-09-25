# TARBS - Tmpstpdwn's Auto-Rice Bootstrapping Script

**TARBS** is a simple, extensible script to automatically set up a minimal Linux environment, including your dotfiles and essential packages.

## What Does TARBS Do?

TARBS automates the process of:

- Installing your dotfiles (via the **bare Git method**).
- Installing packages based on a configurable `.packages` list.

This is particularly useful for quickly setting up new systems with your environment.

## Dotfiles Management

TARBS uses the [Git bare repository method for dotfile management](https://www.atlassian.com/git/tutorials/dotfiles), which keeps your home directory clean and version-controlled.

By default, it clones [my dotfiles repo (voidrice)](https://github.com/tmpstpdwn/.dotfiles). You can easily change this by editing the `dotfilesrepo` variable in the script.

## Package List: `.packages`

The script expects a `.packages` file located at:

```
$HOME/.packages
```

This file is part of the dotfiles repo and contains a list of packages to install, formatted as a **CSV with two columns**:

| Tag | Package Name |
|-----|--------------|
| V | `neovim` |

- **Column 1:** _Tag_ – Specifies the installation method.
  - V for packages from void official repo.
- **Column 2:** _Package name_ / _Link_ – The exact name or link for the package based on installation mode.

During installation, TARBS prints the description.

The `.packages` files is expected to be at `$HOME` of the dotfiles git repo, this works
as package installations comes after dotfiles setup.

[here](https://raw.githubusercontent.com/tmpstpdwn/.dotfiles/refs/heads/main/.packages) is my `.packages` file for reference.

This format allows for easy parsing, editing, and expansion of the package list.

## Dependencies

- Git
- xbps-install (Void Linux default package manager)

Ensure you run the script as a **regular user** with `sudo` privileges — not as root. The script will request sudo access when needed.

## Customization

Want to use your own dotfiles or packages?

- **Use your own dotfiles**: Change the `dotfilesrepo` variable in the script.
- **Customize your package list**: Modify the `.packages` file inside your dotfiles repo.

You can also extend the script to support additional tags (e.g., for AUR, flatpak, custom builds, etc.).

## License

TARBS is licensed under the **GNU GPLv3**.  
See the [LICENSE](LICENSE) file for more details.
