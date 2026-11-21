---
tags:
  - linux
  - fedora
  - wayland
  - noctalia
  - setup-guide
aliases:
  - Установка Noctalia Shell
created: 2026-11-21
---

# Установка Noctalia Shell на Fedora

> [!info] Источник и требования
> Инструкция основана на [официальной документации Noctalia Docs](https://noctalia.dev). 
> **Noctalia** — это оболочка (панель, лаунчер, уведомления), поэтому для её работы требуется установленный Wayland-композитор (**Niri**, **Hyprland** или **Sway**).

---

## Шаг 1. Установка Wayland-композитора

Выберите и установите один из поддерживаемых композиторов (пропустите этот шаг, если он уже установлен):

- [ ] **Вариант А: Niri** (рекомендуется для максимальной совместимости)
  ```bash
  sudo dnf install niri
  ```

- [ ] **Вариант Б: Hyprland** (через репозиторий COPR)
  ```bash
  sudo dnf copr enable lionheartp/Hyprland
  sudo dnf install hyprland
  ```

---

## Шаг 2. Установка Noctalia Shell

- [ ] **Для Fedora 44 и новее** (стабильная версия из официальных репозиториев):
  ```bash
  sudo dnf install noctalia
  ```

- [ ] **Для Fedora 42/43 или получения свежей git-версии** (через COPR):
  ```bash
  sudo dnf copr enable lionheartp/Hyprland
  sudo dnf install noctalia-git
  ```

> [!tip] Опционально: фирменный экран входа (Greeter)
> Если вы хотите заменить стандартный GDM на лёгкий `greetd` с темой от Noctalia, выполните:
> ```bash
> sudo dnf install greetd noctalia-greeter
> sudo systemctl disable --now gdm
> sudo systemctl enable --now greetd
> ```

---

## Шаг 3. Настройка автозапуска

Добавьте команду запуска оболочки в конфиг вашего композитора.

> [!warning] Конфликт утилит
> Перед запуском отключите в конфиге композитора другие панели и демоны уведомлений (например, `waybar`, `mako`, `swaync`), чтобы они не перекрывали интерфейс Noctalia.

- [ ] **Если используете Niri** — добавьте в `~/.config/niri/config.kdl`:
  ```kdl
  spawn-at-startup "noctalia"
  ```

- [ ] **Если используете Hyprland** — добавьте в `~/.config/hypr/hyprland.conf`:
  ```ini
  exec-once = noctalia
  ```

---

## Шаг 4. Первый запуск

- [ ] Завершите текущий сеанс (**Logout**).
- [ ] На экране входа в систему выберите сессию **Niri** или **Hyprland**.
- [ ] Войдите в систему — при первом запуске откроется мастер первоначальной настройки (Setup Wizard), который создаст базовые файлы конфигурации в директории `~/.config/noctalia/`.
