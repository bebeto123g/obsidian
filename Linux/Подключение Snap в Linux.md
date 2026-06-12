
### 1. Debian

```bash
sudo apt update
```
```bash
sudo apt install snapd
```
```bash
sudo snap install snapd
```

### 2. Fedora

```bash
sudo dnf install snapd
```
```bash
sudo ln -s /var/lib/snapd/snap /snap
```

### 3. Manjaro

```bash
sudo pacman -S snapd
```
```bash
sudo systemctl enable --now snapd.socket
```
```bash
sudo ln -s /var/lib/snapd/snap /snap
```

### 4. Arch Linux

```bash
git clone https://aur.archlinux.org/snapd.git
```
```bash
cd snapd
```
```bash
makepkg -si
```
```bash
sudo systemctl enable --now snapd.socket
```
```bash
sudo systemctl enable --now snapd.apparmor.service
```

если будет ошибка с доступами, попробовать:
```bash
sudo ln -s /var/lib/snapd/snap /snap
```



## Полная  [документация](https://snapcraft.io/docs/tutorials/install-the-daemon/manjaro-linux/)