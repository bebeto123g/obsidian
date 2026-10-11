
###  Терминальные утилиты:

Debian/Ubuntu установка сложнее, что-то есть только в snap.

Arch:
```bash
sudo pacman -S stow bat mc git lazygit kitty zellij yazi fastfetch vim neovim mpv fish zsh vlc rhythmbox gedit evince baobab snapshot loupe 7zip ffmpeg
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
```
```bash
rm ~/.cache/thumble
```

### Гайд по настройке терминала + полезный программы

[Как сделать терминал в Linux красивым, быстрым и удобным](https://www.youtube.com/watch?v=UzWOX7-Tye8)

### Гайд по tmux

[tmux — Как Стать Терминальным Чадом](https://www.youtube.com/watch?v=GnP_SsMPNro)

### Гайд по zellij

[Обзор на zellij: Убийца tmux?](https://www.youtube.com/watch?v=OnmaBi9TjIk)

