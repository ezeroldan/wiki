# Zsh

## Instalar
- `sudo apt install -y zsh` Debian
- `sudo dnf install -y zsh` Fedora
- `sudo usermod -s /usr/bin/zsh $(whoami)` Setear por defecto

### oh my zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### Powerlevel10k

#### Meslo Nerd Font
- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

#### Installation
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

vim ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"

p10k configure
```

#### Plugins
```bash
sudo git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
sudo git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

```bash
vim ~/.zshrc
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## Configuracion
- `man zsh` Ver manual
- `vim ~/.zshrc` Editar el archivo

### env vars
- `HISTSIZE=1000` Lineas del historial
- `HISTFILE=~/.histofile` Archivo del historial
- `SAVEHIST=1000` Numero de lineas de $HISTFILE
- `export PATH=$HOME/bin:$PATH` Usar mu carpeta propia de scripts
- `ZSH_THEME="powerlevel10k/powerlevel10k"` Theme
- `CASE_SENSITIVE="true"` Uncomment the following line to use case-sensitive completion.
- `HYPHEN_INSENSITIVE="true"` Uncomment the following line to use hyphen-insensitive completion.# Case-sensitive completion must be off. _ and - will be interchangeable.
- `DISABLE_AUTO_UPDATE="true"` Uncomment the following line to disable bi-weekly auto-update checks.
- `DISABLE_UPDATE_PROMPT="true"` Uncomment the following line to automatically update without prompting.
- `export UPDATE_ZSH_DAYS=13` Uncomment the following line to change how often to auto-update (in days).
- `DISABLE_MAGIC_FUNCTIONS="true"` Uncomment the following line if pasting URLs and other text is messed up.
- `DISABLE_LS_COLORS="true"` Uncomment the following line to disable colors in ls.
- `DISABLE_AUTO_TITLE="true"` Uncomment the following line to disable auto-setting terminal title.
- `ENABLE_CORRECTION="true"` Uncomment the following line to enable command auto-correction.
- `COMPLETION_WAITING_DOTS="true"` Uncomment the following line to display red dots whilst waiting for completion.
- `DISABLE_UNTRACKED_FILES_DIRTY="true"` Uncomment the following line if you want to disable marking untracked files under VCS as dirty. This makes repository status check for large repositories faster.
- `ZSH_CUSTOM=/path/to/new-custom-folder` Would you like to use another custom folder than $ZSH/custom?
- `export MANPATH="/usr/local/man:$MANPATH"` User configuration
- `export LANG=en_US.UTF-8` You may need to manually set your language environment

### Opts
- `setopt` Listar opciones habilitadas
- `setopt name` Habilitar la opcion
- `unsetopt` Listar opciones deshabilitadas
- `unsetopt name` Deshabilitar la opcion

## Functions
- `$fpath` Paths de funciones
- `/usr/share/zsh/functions/Misc` Funciones de zsh