
## 1. Подключение репозиториев RPM Fusion
По умолчанию Fedora содержит только свободное ПО. Для доступа к драйверам NVIDIA, Steam и кодекам необходимо подключить сторонние репозитории.

```bash
sudo dnf install https://rpmfusion.org\((rpm -E \%fedora).noarch.rpm https://rpmfusion.org\)(rpm -E %fedora).noarch.rpm -y
sudo dnf check-update
```

---

## 2. Установка драйверов видеокарты

### Вариант А: Для видеокарт NVIDIA
Установка официального проприетарного драйвера и поддержка 32-битных библиотек (необходимы для старых игр и Wine/Proton).
```bash
sudo dnf install akmod-nvidia xorg-x11-drv-nvidia-cuda xorg-x11-drv-nvidia-libs.i686 -y
```
> [!WARNING] Важно
> После выполнения команды подождите 3–5 минут перед перезагрузкой компьютера, чтобы модуль ядра успел скомпилироваться.

### Вариант Б: Для видеокарт AMD / Intel
Драйверы уже встроены в ядро Linux. Необходимо установить только 32-битную поддержку Vulkan:
```bash
sudo dnf install mesa-vulkan-drivers.i686 -y
```

---

## 3. Установка кодеков и мультимедиа
Замена базового пакета кодеков на полноценный из RPM Fusion для корректной работы звука и видеороликов внутри игр:
```bash
sudo dnf swap ffmpeg-free ffmpeg --allowerasing -y
sudo dnf update @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin -y
```

---

## 4. Игровые платформы и лаунчеры

### Steam (Основная площадка)
* **Установка через DNF:** `sudo dnf install steam -y`
* **Альтернатива (Flatpak):** Можно установить через магазин приложений (Software Center) с Flathub.
* **Обязательная настройка:** После запуска зайдите в *Настройки -> Compatibility (Совместимость)* и включите **Proton для всех остальных продуктов** (Enable Proton for all other titles).

### Lutris и Heroic Games Launcher
Используются для запуска игр из Epic Games Store, GOG, Amazon, а также сторонних установщиков (включая файлы `.exe`).
```bash
sudo dnf install lutris heroic-games-launcher -y
```

### Дополнительно: ProtonUp-Qt
* Утилита для легкой установки кастомных версий Proton (например, **GE-Proton**), которые повышают FPS и чинят совместимость в новых играх.
* **Как установить:** Доступна для скачивания в формате Flatpak через стандартный менеджер приложений (Software Center).
