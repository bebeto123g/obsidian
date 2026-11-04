## 📋 Подготовка системы

### Обновление пакетов

```bash
sudo apt update
```
```bash
sudo apt upgrade -y
```
```bash
sudo apt full-upgrade -y
```

### Установка необходимых зависимостей

Установите основные пакеты для работы с графикой и необходимые библиотеки:

```bash
sudo apt install -y build-essential git wget curl vulkan-tools mesa-vulkan-drivers libvulkan1 libvulkan-dev
```

---

## 🎮 Настройка Steam

### Включение 32-битной поддержки

> **Важно!** Многие игры требуют 32-битные библиотеки. Это обязательный шаг.

Добавьте архитектуру:

```bash
sudo dpkg --add-architecture i386
```
```bash
sudo apt update
```

### Установка Steam

#### Метод 1: Через официальный репозиторий Debian

```bash
sudo apt install -y steam-devices
```
```bash
sudo apt install -y steam
```

### Первый запуск Steam, для Niri сработал запуск только через терминал

```bash
steam
```

Для запуска GUI
```bash
steam &
```

> При первом запуске Steam автоматически установит необходимые компоненты Proton.

---

## ⚙️ Установка и настройка Proton

### Что такое Proton?

**Proton** — это compatibility layer, который позволяет запускать Windows-игры на Linux через Steam. Это автоматизированная версия Wine с оптимизациями для игр.
### Включение Proton в Steam

1. Откройте **Steam** → **Параметры** (Settings)
2. Перейдите в **Стимдек** (Steamdeck)
3. Включите **"Включить Proton"** (Enable Proton for unsupported titles)
4. Выберите версию Proton (рекомендуется последняя стабильная версия)

### Установка Proton-Plus-GE (улучшенная версия)

Для получения последних версий с дополнительными исправлениями:

```bash
# Создайте директорию, если её нет
mkdir -p ~/.steam/root/compatibilitytools.d/

# Перейдите в неё
cd ~/.steam/root/compatibilitytools.d/

# Загрузите последнюю версию
wget https://github.com/GloriousEggroll/proton-ge-custom/releases/download/LATEST/Proton-GE-latest.tar.gz

# Распакуйте
tar -xzf Proton-GE-latest.tar.gz

# Удалите архив
rm Proton-GE-latest.tar.gz
```

> Перезагрузите Steam — новая версия Proton появится в списке.

---

## 🖥️ Установка видеодрайверов

### Для NVIDIA

```bash
# Установка драйвера
sudo apt install -y nvidia-driver nvidia-utils

# 32-битные библиотеки
sudo apt install -y libglvnd0:i386 libglvnd-dev:i386

# Перезагрузка
sudo reboot
```

**Проверка установки:**
```bash
nvidia-smi
```

### Для AMD (AMDGPU)

Убедитесь, что подключены репозитории `non-free non-free-firmware`:

```bash
# Отредактируйте sources.list
sudo nano /etc/apt/sources.list
```

Строки должны содержать `non-free non-free-firmware`:

```
deb http://deb.debian.org/debian/ trixie main contrib non-free-firmware non-free
deb-src http://deb.debian.org/debian/ trixie main contrib non-free-firmware non-free
```

Сохраните (Ctrl+O, Enter, Ctrl+X)

### Обновите список пакетов

```bash
sudo apt update
```

### Правильная установка для AMD

 Основной пакет прошивок
```bash
sudo apt install -y firmware-linux-nonfree
```

AMD GPU драйверы (открытые)
```bash
sudo apt install -y libdrm-amdgpu1 libdrm-amdgpu1:i386
```

Vulkan поддержка
```bash
sudo apt install -y mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

Дополнительно (если нужна новая версия Mesa)
```bash
sudo apt install -y libvulkan1 libvulkan1:i386
```

Перезагрузка
```bash
sudo reboot
```

### Проверка установки

```bash
# Проверить, установлена ли прошивка
ls /lib/firmware/amdgpu/

# Проверить Vulkan
vulkaninfo | grep "AMD"

# Проверить драйвер
lspci -k | grep -A 2 "VGA compatible controller"
```
### Для Intel

```bash
sudo apt install -y intel-media-driver
sudo apt install -y mesa-vulkan-drivers:i386
```

---

### VKD3D (DirectX 12). Не делал.

Для игр на DirectX 12:

```bash
sudo apt install -y libvkd3d1 libvkd3d-dev
sudo apt install -y libvkd3d1:i386
```

### Включение FSYNC (снижает задержки). Не делал.

**Для ядер с патчем fsync:**

```bash
# Добавьте параметр в sysctl
echo "vm.max_map_count = 2147483642" | sudo tee -a /etc/sysctl.conf

# Примените изменения
sudo sysctl -p
```

**Проверка FSYNC в игре:**
```bash
export PROTON_NO_FSYNC=0
```

---
### Переменные окружения для оптимизации. Не делал.

Создайте скрипт `~/.steam_launch.sh`:

```bash
#!/bin/bash

# Путь к Proton tools
export STEAM_COMPAT_TOOL_PATHS="/home/$USER/.steam/root/compatibilitytools.d"

# Отключить DirectX 11.2
export PROTON_NO_D3D11_2=1

# Включить DirectX 12
export PROTON_NO_D3D12=0

# Показывать FPS
export DXVK_HUD=fps

# Топология CPU (4 ядра, 2 потока на ядро)
export WINE_CPU_TOPOLOGY=4:2

# Запуск Steam
steam "$@"
```

**Сделайте скрипт исполняемым:**

```bash
chmod +x ~/.steam_launch.sh
```

**Запуск:**

```bash
~/.steam_launch.sh
```

### Дополнительные переменные окружения. Не делал.

```bash
# Основные переменные
PROTON_NO_FSYNC=0              # Включить FSYNC
PROTON_WAIT_FOR_SERVER=1       # Ждать сервера перед запуском
DXVK_HUD=fps                   # Показать FPS
DXVK_HUD=memory                # Показать использование памяти
DXVK_HUD=fps,memory            # Оба показателя
WINE_CPU_TOPOLOGY=4:2          # Конфигурация CPU

# Отладка
PROTON_LOG=1                   # Включить логирование
PROTON_LOG_FILE=/tmp/proton.log # Сохранить лог
```

---

## 🛠️ Дополнительные инструменты. По желанию.

### Lutris (универсальный запускатель)

Позволяет запускать игры вне Steam, включая GOG, itch.io и прочие.

```bash
sudo apt install -y lutris
```

**Использование:**
- Скачайте игру в Lutris
- Нажмите "Install"
- Нажмите "Play"

### Heroic Games Launcher (Epic Games, GOG)

Клиент для запуска игр из Epic Games Store и GOG:

```bash
sudo apt install -y heroic
```

### MangoHUD (оверлей FPS и системной информации)

Показывает FPS, температуру, использование CPU/GPU в реальном времени:

```bash
sudo apt install -y mangohud
```

**Включение в Steam:**

В свойствах игры добавьте в "Параметры запуска":
```bash
mangohud %command%
```

### GameMode (оптимизация ресурсов для игр). Уже был сам установлен.

```bash
sudo apt install -y gamemode
```

**Использование:**
```bash
gamemoderun /path/to/game
```

---

## 🔧 Решение частых проблем

### Библиотеки и зависимости

| Проблема                          | Решение                                                    |
| --------------------------------- | ---------------------------------------------------------- |
| "Не найдены 32-битные библиотеки" | `sudo dpkg --add-architecture i386 && sudo apt update`     |
| Отсутствуют шрифты                | `sudo apt install -y fonts-liberation fonts-liberation2`   |
| Проблемы с OpenGL                 | `sudo apt install -y libgl1-mesa-glx libgl1-mesa-glx:i386` |
### Переключение на PipeWire (современный аудиосервер)

```bash
# Установка
sudo apt install -y pipewire pipewire-pulse pipewire-alsa

# Включение сервиса
systemctl --user enable pipewire pipewire-pulse
systemctl --user start pipewire pipewire-pulse

# Проверка
pactl info | grep "Server Name"
```

---

## 🔍 Мониторинг и отладка

### Просмотр информации о системе

```bash
# Информация о GPU
glxinfo | grep "OpenGL version"

# Vulkan информация
vulkaninfo | grep apiVersion

# Информация о CPU
lscpu

# Информация о памяти
free -h
```

### Профилирование производительности

```bash
# Использование MangoHUD
mangohud steam

# Запись к лог-файлу
mangohud --output=/tmp/mangohud.log steam
```

---

## 📊 Рекомендуемые конфигурации по типам ПК

### Низкопроизводительный ПК (интегрированная графика)

```bash
# Переменные окружения
export PROTON_USE_WINED3D=1        # Использовать WineD3D вместо DXVK
export STAGING_SHARED_MEMORY=1     # Общая память
export DXVK_HUD=fps
```

### Среднего уровня ПК (дискретная карта)

```bash
export PROTON_NO_FSYNC=0           # FSYNC включён
export DXVK_HUD=fps,memory
export WINE_CPU_TOPOLOGY=4:2       # Автоопределение
```

### Высокопроизводительный ПК (GeForce RTX/Radeon RX)

```bash
export PROTON_NO_FSYNC=0
export PROTON_NO_ESYNC=0
export DXVK_HUD=fps,memory,memory_usage
export WINE_CPU_TOPOLOGY=8:2
export STAGING_SHARED_MEMORY=1
```
