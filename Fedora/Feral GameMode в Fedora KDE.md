
Краткое руководство по установке и использованию утилиты GameMode для оптимизации процессоров Intel (включая гибридные архитектуры с энергоэффективными ядрами).

## 1. Установка
Откройте **Konsole** (или вашу оболочку `fish`) и выполните команды:

```bash
# Установка основной утилиты
sudo dnf install gamemode -y

# Установка 32-битных библиотек (нужно для старых игр и платформеров)
sudo dnf install gamemode.i686 -y
```

## 2. Активация в играх

### В Steam
1. Нажмите правой кнопкой мыши на игру -> **Свойства (Properties)**.
2. В поле **Параметры запуска (Launch Options)** вставьте:
   ```text
   gamemoderun %command%
   ```

### В сторонних лаунчерах
* **Lutris:** *Preferences -> System options ->* включить тумблер **Enable Feral GameMode**.
* **Heroic Games Launcher:** *Settings -> Game Defaults ->* поставить галочку **Use GameMode**.

## 3. Проверка статуса (для Fish / Bash)
Запустите игру, сверните её (`Alt + Tab`) и введите в терминал команду:

```fish
busctl --user get-property com.feralinteractive.GameMode /com/feralinteractive/GameMode com.feralinteractive.GameMode ClientCount
```

### Значения ответа:
* `i 0` (или `u 0`) — режим не активен.
* `i 1` / `i 2` — **всё работает!** Цифра показывает количество процессов под управлением GameMode (для Skyrim через Proton значение `2` является нормой).
