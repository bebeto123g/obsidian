
###  Install

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