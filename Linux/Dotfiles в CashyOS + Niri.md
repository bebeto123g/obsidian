
### Настроить SSH по [инструкции](Настройка%20SSH%20в%20Linux.md)

### Установить Stow

Debian/Ubuntu:
```bash
sudo apt update && sudo apt install stow
```

Arch:
```bash
sudo pacman -S stow
```

### Скачать конфиги из репозитория в /home/$USER

```bash
git clone git@github.com:bebeto123g/dotfiles.git
```

### Перейти в директорию

```bash
cd ./dotfiles
```

### Выполнить команду

```bash
stow .
```