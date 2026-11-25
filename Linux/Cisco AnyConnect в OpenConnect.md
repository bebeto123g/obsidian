---
tags:
  - linux
  - arch
  - vpn
  - openconnect
  - cisco
---
## Установите OpenConnect:

```bash
sudo pacman -S openconnect
```

> Подключитесь к корпоративному VPN одной командой в терминале:
```bash
sudo openconnect --protocol=anyconnect vpn.intdigital.ru
```

# Автоматизация подключения к Cisco AnyConnect через OpenConnect

Инструкция по созданию защищенного скрипта для быстрого запуска рабочего VPN без ручного ввода адреса сервера, логина и первого пароля.

#### 1. Установка `libsecret`:

```bash
sudo pacman -S libsecret
```

#### 2. **Сохраните пароль, логин и сервер в связку ключей** (выполняется один раз в терминале):


```bash
secret-tool store --label="Intdigital VPN Password" service intdigital-vpn key password
```

```bash
secret-tool store --label="Intdigital VPN User" service intdigital-vpn key username
```

```bash
secret-tool store --label="Intdigital VPN Server" service intdigital-vpn key server
```


#### 3. **Добавьте функцию в ваш `.bashrc`** (теперь этот код полностью безопасен для Git):

Для BASH\ZSH:

```bash
intd_vpn() {
    local USER=$(secret-tool lookup service intdigital-vpn key username)
    local PASS=$(secret-tool lookup service intdigital-vpn key password)
    local SERVER=$(secret-tool lookup service intdigital-vpn key server)

    if [[ -z "$PASS" || -z "$USER" || -z "$SERVER" ]]; then
        echo "Ошибка: данные VPN не найдены в связке ключей."
        return 1
    fi

    read -rp "Введите OTP код: " OTP

    printf "%s\n%s\n" "$PASS" "$OTP" | sudo openconnect --protocol=anyconnect -u "$USER" --passwd-on-stdin "$SERVER"
}
```

Для FISH:
```bash
function intd_vpn
    set -l USER (secret-tool lookup service intdigital-vpn key username)
    set -l PASS (secret-tool lookup service intdigital-vpn key password)
    set -l SERVER (secret-tool lookup service intdigital-vpn key server)

    if test -z "$PASS" -o -z "$USER" -o -z "$SERVER"
        echo "Ошибка: данные VPN не найдены в связке ключей."
        return 1
    end

    read -P "Введите OTP код: " OTP

    printf "%s\n%s\n" "$PASS" "$OTP" | sudo openconnect --protocol=anyconnect -u "$USER" --passwd-on-stdin "$SERVER"
end
```

#### 4. Запуск:

```bash
sudo intdigital_vpn
```

