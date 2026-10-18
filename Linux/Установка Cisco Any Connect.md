

1. Откройте терминал и перейдите в папку с архивом. Например, если он лежит в `Загрузки`:

```bash
cd ~/Downloads
```

```bash
mkdir -p ~/anyconnect-install
```

```bash
tar -xzf anyconnect-linux64-4.10.05111-predeploy-k9.tar_new.gz -C ~/anyconnect-install
```

Суффикс `_new` в имени сам по себе не мешает распаковке, если файл действительно является gzip-архивом.


2. Найдите установочный скрипт:

```bash
find ~/anyconnect-install -type f -name vpn_install.sh
```

3. Перейдите в каталог `vpn`, указанный в результате поиска, и запустите установку. Например:

```bash
cd ~/anyconnect-install/anyconnect-linux64-4.10.05111/vpn
```

```bash
sudo sh ./vpn_install.sh
```

Введите пароль пользователя и подтвердите лицензию, введя `y`. Скрипт установки требует прав администратора. <citation src="12"></citation>

4. Запустите клиент из меню приложений или командой:

```bash
/opt/cisco/anyconnect/bin/vpnui
```

В клиенте введите адрес VPN-сервера вашей организации и пройдите аутентификацию.


Если `tar` сообщит, что файл не является gzip-архивом, проверьте тип файла:

```bash
file anyconnect-linux64-4.10.05111-predeploy-k9.tar_new.gz
```
