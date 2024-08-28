### Linux install:
- Install popos

Install i3:

`sudo apt install i3`

On startup on the bottom left click the settings icon and select i3.

#2 - Basic terminal setup

### Nvim default install (setup later)
```
sudo apt install vim
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
sudo rm -rf /opt/nvim
sudo tar -C /opt -xzf nvim-linux64.tar.gz

THEN add this stuff:
vim ~/.zshrc
alias vim="nvim"
alias vi="nvim"
alias oldvim="vim"
export PATH="$PATH:/opt/nvim-linux64/bin"

AND RESTART!
```

### Zsh + OhMyZsh

`sudo apt install neovim`

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

### Tmux
```
sudo apt install tmux

nvim ~/.tmux.conf
# Set the control character to Ctrl+Spacebar (instead of Ctrl+B)
set -g prefix C-space
unbind-key C-b
bind-key C-space send-prefix

# Set new panes to open in current directory
bind c new-window -c "#{pane_current_path}"
bind '"' split-window -c "#{pane_current_path}"
bind % split-window -h -c "#{pane_current_path}"
```

### Languages / Tools

pip:
```
sudo apt install python3-pip -y
```

NodeJS:
```
sudo apt install nodejs
sudo apt install npm
```

Golang:
```
download linux version: https://go.dev/doc/install

install:

sudo tar -C /usr/local -xzf go1.23.0.linux-amd64.tar.gz

Set path:

export PATH=$PATH:/usr/local/go/bin

also set it zshrc
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:$GOPATH/bin

```

GCC + Tooling:
```
sudo apt install gcc
sudo apt install build-install
```

Postgres
```
sudo apt install postgresql

Then 
sudo vim /etc/postgresql/*/main/postgresql.conf
* is just the version so for version 14 it would be: sudo vim /etc/postgresql/14/main/postgresql.conf

and change the commented #listen_addresses = ‘localhost’ to #listen_addresses = ‘*’ 

Log into template and create a test password for local dev stuff.:
sudo -u postgres psql template1
ALTER USER postgres with encrypted password 'test';


Then edit the conf 
sudo vim /etc/postgresql/*/main/pg_hba.conf
local   all             postgres                                peer
Should be
local   all             postgres                                md5

sudo systemctl restart postgresql.service

```

Pgcli
```
sudo pip install pgcli
```

Docker
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

### NVIM Setup

```
DEFAULT LAZYVIM:

git clone https://github.com/LazyVim/starter ~/.config/nvim
nvim

ADD PRIMES INIT.LUA:

curl -LO https://github.com/BurntSushi/ripgrep/releases/download/14.1.0/ripgrep_14.1.0-1_amd64.deb
sudo dpkg -i ripgrep_14.1.0-1_amd64.deb


```

# I3 config

To get transparent windows for a background image:

TODO: Automatically load this
using a background image:
`sudo apt-get install feh
feh --bg-scale --zoom fill ~/Pictures/background.jpg`

Install picom
`apt install picom`

Add this to ~/.config/i3/config
`exec --no-startup-id picom -CGb`
