# Zsh
```
sudo apt-get update -y
sudo apt-get install -y zsh
sudo usermod -s /usr/bin/zsh $(whoami)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

sudo reboot

sudo apt-get install -y powerline fonts-powerline
sudo apt-get install -y zsh-theme-powerlevel9k
sudo apt-get install -y zsh-syntax-highlighting

echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc

nano ~/.zshrc
ZSH_THEME="agnoster"
```
