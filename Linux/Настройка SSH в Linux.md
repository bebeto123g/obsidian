##### 1. Устанавливаем GIT:
```bash
sudo pacman -S git
```

##### 2. Настраиваем глобальный конфиг:
```bash
git config --global user.name "bebeto123@arch16"
```
```bash
git config --global user.email "bebeto123g@gmail.com"
```

##### 3. Создаем ключ.

```bash
ssh-keygen -t ed25519
```

##### 4. Запустите агент SSH в фоновом режиме. Работает только в bash.

```bash
eval "$(ssh-agent -s)"
```

##### 5. Добавьте закрытый ключ SSH в ssh-agent.

```bash
ssh-add ~/.ssh/id_ed25519
```

##### 6. Скопируйте открытый ключ SSH в буфер обмена.

```bash
$ cat ~/.ssh/id_ed25519.pub
```

##### 7. Добавить ключ SSH в конфигурациях github|gitlab.