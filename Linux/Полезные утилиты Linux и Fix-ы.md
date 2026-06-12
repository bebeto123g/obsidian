
###  Терминальные утилиты:

Debian/Ubuntu установка сложнее, что-то есть только в snap.

Arch:
```bash
sudo pacman -S lsd bat mc git lazygit kitty zellij yazi fastfetch zoxide fzf fd ripgre vim nsuperfileeovim 
```

### Медиа, преимещественно для GTK:

Debian/Ubuntu:
```bash
sudo apt update && sudo apt install vlc smplayer smplayer-skins smplayer-themes rhythmbox
```

Arch:
```bash
sudo pacman -S vlc smplayer smplayer-skins smplayer-themes rhythmbox
```

### Для Ubuntu иногда ломаются preview картинок и видео, fix:

```bash
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0

rm ~/.cache/thumble
```