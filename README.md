# Nix Darwin Setup

This README outlines the steps to set up Nix and Nix Darwin on macOS, allowing for declarative package management and system configuration.

## Prerequisites

- **macOS Version**: Ensure your system is running macOS 10.15 (Catalina) or later.
- **Command Line Tools**: Install Xcode Command Line Tools by running:

```bash
xcode-select --install
```

## Installation Steps

1.  Install Nix:

    ```bash
    curl -L https://nixos.org/nix/install | sh
    ```

    This command fetches and executes the official Nix installation script. The curl command transfers the script from the URL, and the -L flag ensures any redirects are followed.
    Follow the on-screen prompts to complete the installation.

2.  Configure the Shell Environment:

    Add Nix to your shell profile:

    For bash (`~/.bash_profile`) or zsh (`~/.zshrc`):

    ```bash
    if [ -e /nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh ]; then
        . /nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh
    fi
    ```

3.  Verify the Installation:

    ```bash
    # Source your profile
    source ~/.bash_profile  # for bash
    source ~/.zshrc        # for zsh

    # Verify installation
    nix --version
    ```

    at the time of writing this, the version is 2.24.10

4.  Enabling and Using Flakes
    Flakes are a modern way of managing reproducible environments and configurations in Nix.

    | Action                        | Command                             |
    | ----------------------------- | ----------------------------------- |
    | Clone a Flake                 | `nix flake clone github:owner/repo` |
    | Run a Flake                   | `nix run github:owner/repo`         |
    | Enter Development Environment | `nix develop`                       |
    | Update Flake Dependencies     | `nix flake update`                  |

## Using Nix

| Action                  | Command                              |
| ----------------------- | ------------------------------------ |
| Search for Packages     | `nix search <package-name>`          |
| Install a Package       | `nix-env -iA nixpkgs.<package-name>` |
| List Installed Packages | `nix-env -q`                         |
| Upgrade Packages        | `nix-env -u`                         |
| Uninstall a Package     | `nix-env -e <package-name>`          |

## Additional Resources

- [NixOS Manual](https://nixos.org/manual/nix/stable/)
- [Nix Packages Search](https://search.nixos.org/packages)
- [Nix Website](https://nixos.org/)
- [Nix Darwin](https://github.com/LnL7/nix-darwin)
- [Nix Homebrew](https://github.com/zhaofengli/nix-hom...)
