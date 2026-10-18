1. Поставить VirtualBox через Cachy Installer.
2. Получить ошибку # [VirtualBox: Kernel driver not installed (rc=-1908)](https://unix.stackexchange.com/questions/796535/virtualbox-kernel-driver-not-installed-rc-1908).
3. Выполнить последовательно команды:

```bash
sudo pacman -S virtualbox
```

```bash
sudo pacman -S virtualbox-host-dkms
```

```bash
sudo pacman -S virtualbox-guest-iso
```

```bash
sudo reboot
```

