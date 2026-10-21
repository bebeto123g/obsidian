## Удаление старой версии

1. **Удалите старый пакет и его зависимости:**

```bash
sudo apt purge -y nodejs npm
```
_(Команда `purge` вместо `remove` удаляет не только программу, но и её конфигурационные файлы)._

2. **Очистите систему от ненужных остаточных пакетов:**

```bash
sudo apt autoremove -y
```
    
3. **Вручную удалите скрытые папки конфигураций и кэша:**  
    Удаление системных каталогов (если они остались):
    
```bash
sudo rm -rf /usr/local/bin/node /usr/local/bin/npm /usr/local/lib/node_modules
```
```bash
sudo rm -rf /usr/bin/node /usr/include/node /usr/share/man/man1/node.1
```
    
    Удаление пользовательских папок (выполняется **без sudo**):

```bash
rm -rf ~/.npm ~/.node-gyp ~/.nv
```

4.  Проверка очистки

Убедитесь, что система больше не видит старые исполняемые файлы. Команды должны выдать ошибку или пустой ответ:

```bash
node -v
```
```bash
npm -v
```
```bash
which node
```

## Установка LTS-версии NodeJS

Вариант 1: Системная установка через NodeSource (Рекомендуется)

Этот способ обновляет системный менеджер пакетов `apt` и устанавливает актуальную версию Node.js глобально

1. Обновите индекс пакетов и установите `curl`, если он еще не установлен:
    
```bash
sudo apt update && sudo apt install -y curl
```
    
2. Подключите официальный репозиторий **NodeSource** для текущей (Latest) версии:
    
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
```

3. Установите Node.js (пакет уже включает в себя `npm`): 

```bash
sudo apt install -y nodejs
```

---
