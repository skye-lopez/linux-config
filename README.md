# Linux config
# 1 - Linux install:
- Install popos
- Install i3
`sudo apt install i3`

On startup on the bottom left click the settings icon and select i3.

#2 - Basic terminal setup

Zsh + OhMyZsh

```
ZSH:
sudo apt install zsh

OHMYZSH:
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sudo apt install zsh-autosuggestions zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
git clone https://github.com/jeffreytse/zsh-vi-mode \$ZSH_CUSTOM/plugins/zsh-vi-mode

REPLACE PLUGINS:
nvim ~/.zshrc
plugins=(git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-autocomplete zsh-vi-mode)
```
