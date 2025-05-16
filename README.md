# devenv

A tool to manage your Linux installation and manage config files etc.

## Development

To set devenv up for development run `./local-setup` to symlink `devenv` to `~/.local/bin/devenv`

## Usage

Use `devenv --help` to get an overview over the available subcommands. All subcommands support the `--dry-run` flag to only show what would be done without actually modifying your system.

### apply

Will use GNU stow to apply all config files from your devenv config directory (e.g. `~/.devenv/home/`). You can use `devenv apply --help` for more info.

### install

Will install all packages defined in your devenv config directory (e.g. `~/.devenv/packages/`). A package file has the following format:
```
[arch]
# You can start a line with a '#' to write a comment
# All names mentioned below '[arch]' will be installed using `pacman`.

# Desktop Environment
hyprland
uwsm
gdm

# Audio
easyeffects

# ...

[aur]
# The AUR category is the same but packages will be installed using `yay` instead.

# Theme
adwaita-qt5-git
```

Sample output (every file you created inside `<devenv dir>/packages` will be one group below):
```
danksa@localhost:~$ devenv install
┌── Installing packages from /home/danksa/.devenv/packages ─
│┌── audio ─
││ Installing: pipewire 🗸 (already installed)
││ Installing: wireplumber 🗸 (already installed)
││ Installing: pavucontrol 🗸 (already installed)
││ Installing: spotify-launcher 🗸 (already installed)
││ Installing: easyeffects 🗸 (already installed)
││ Installing: lsp-plugins 🗸 (already installed)
│└─
│┌── base ─
││ Installing: btop 🗸 (already installed)
││ Installing: git 🗸 (already installed)
││ Installing: noto-fonts-cjk 🗸 (already installed)
││ Installing: noto-fonts-emoji 🗸 (already installed)
││ Installing: ttf-iosevka-nerd 🗸 (already installed)
││ Installing: ttf-jetbrains-mono 🗸 (already installed)
││ Installing: ttf-jetbrains-mono-nerd 🗸 (already installed)
│└─
└─
```

For more info you can type `devenv install --help`.

