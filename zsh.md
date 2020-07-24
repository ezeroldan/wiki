# Zsh

## Instalar
```BASH
sudo apt update -y
sudo apt install -y zsh
sudo usermod -s /usr/bin/zsh $(whoami)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Adicionales
```BASH
sudo apt install -y zsh-theme-powerlevel9k
sudo apt install -y zsh-syntax-highlighting

echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc

nano ~/.zshrc
ZSH_THEME="agnoster"
```

## Eliminar usuario prompt
```BASH
prompt_context() {
  if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
    prompt_segment black default ""
  fi
}
```
