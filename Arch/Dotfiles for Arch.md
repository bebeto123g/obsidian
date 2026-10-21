
###  1. Установить Stow и Git

Arch:
```bash
sudo pacman -S stow
```

###  2. Настроить SSH

[[Настройка SSH в Linux]]

###  3. Скачать конфиги из репозитория в /home/$USER

```bash
git clone git@github.com:bebeto123g/dotfiles.git
```

### 4. Перейти в директорию

```bash
cd ./dotfiles
```

###  5. Выполнить команду

```bash
stow .
```