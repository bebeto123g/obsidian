
###  1. Установить Stow и Git

Debian/Ubuntu:
```bash
sudo apt update && sudo apt install stow git
```

###  2. Настроить SSH

[[Настройка SSH в Linux]]

###  3. Скачать конфиги из репозитория в /home/$USER

```bash
git clone git@github.com:bebeto123g/debian_dms.git
```

### 4. Перейти в директорию

```bash
cd ./dotfiles
```

###  5. Выполнить команду

```bash
stow .
```