##### 1. Создаем ключ.

```bash
ssh-keygen -t ed25519
```

##### 2. Запустите агент SSH в фоновом режиме. Работает только в bash.

```bash
eval "$(ssh-agent -s)"
```

##### 3. Добавьте закрытый ключ SSH в ssh-agent.

```bash
ssh-add ~/.ssh/id_ed25519
```

##### 4. Скопируйте открытый ключ SSH в буфер обмена.

```bash
$ cat ~/.ssh/id_ed25519.pub
# Then select and copy the contents of the id_ed25519.pub file
# displayed in the terminal to your clipboard
```

##### 5. Добавить ключ SSH в конфигурациях github|gitlab.