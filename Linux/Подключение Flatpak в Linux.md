
### 1. Debian

```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install flatpak
```

If you are running GNOME:
```bash
sudo apt install gnome-software-plugin-flatpak
```

If you are running KDE:
```bash
sudo apt install plasma-discover-backend-flatpak
```

Flathub is the best place to get Flatpak apps:
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

### 2. Arch

```bash
sudo pacman -S flatpak
```
```bash
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
