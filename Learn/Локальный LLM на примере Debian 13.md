## 1. Установка NodeJS

Используем [[Установка NodeJS LTS Debain]]

## 2. Установка Ollama

1. Обнови систему:

```bash
sudo apt update && sudo apt upgrade -y
```

2. Установи Ollama:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

После этого проверь, что сервис поднялся:

```bash
systemctl status ollama
```

API обычно будет доступен на `127.0.0.1:11434`. <citation src="2,3"></citation>

3. Скачай модели:

Общая модель Qwen, можно использовать для кода:
```bash
ollama pull bqwen3.5:4b
```

Универсальная модель:
```bash
ollama pull llama3.2:3b
```

Универсальная модель:
```bash
ollama pull deepseek-r1:8b
```

## 3. Установка Qwen Code

Самый простой способ — установить через npm. Нужен Node.js 20 или новее. Откройте терминал и выполните:

```bash
sudo npm install -g @qwen-code/qwen-code@latest
```

```bash
qwen --version
```
### Первый запуск

Перейдите в папку проекта и запустите:

```bash
cd путь/к/проекту
qwen
```
### Полезные команды

- `/model` — выбрать модель.
- `/auth` — настроить или сменить авторизацию.
- `/init` — создать контекст проекта.
- `/clear` — начать новый диалог.
- `/compress` — сжать историю разговора. <citation src="3"></citation>

Qwen Code также поддерживает запуск запроса из командной строки, например `qwen -p "Кратко опиши структуру репозитория"`. <citation src="1"></citation>

## 4. Установка DeepSeek

**DeepSeek Harness (dsh)** — это официальная среда выполнения открытых AI-агентов от компании [DeepSeek AI GitHub](https://www.google.com/goto?url=CAESZwHrOzAVhOQgBzPgetDWeFXbYK30obCpGUGnRL2tSaJpC500vaWhei0cWU4yBC_Pjb4WM6bOrUDa-S8Cz0fJptrNT45N6HC8dgxEKPIv8H9De1LCFxD5TO8J4ae9-WnzLMrJx88o048). Поскольку официального графического Desktop-приложения под Linux нет, на **Debian 13 Trixie** используется CLI-версия, которая запускает локальный веб-интерфейс (Web UI).

---
#### Глобальная установка в систему

Если вы планируете пользоваться агентом регулярно, установите его как постоянную глобальную команду:

1. **Установите пакет:**
    
```bash
sudo npm install -g @deepseek-ai/dsh
```
    
2. **Запустите веб-интерфейс** из любой папки вашего терминала:
    
```bash
dsh web
```

---

## 5. Установка OpenCode


```bash
sudo npm install -g opencode-ai
```
После установки проверь:

```bash
opencode --version
```

Запусти OpenCode:

```bash
opencode
```

В открывшемся интерфейсе введи:

```text
/connect
```

Выбери провайдера и пройди авторизацию. Для облачной модели обычно понадобится аккаунт или API-ключ. Затем выбери модель командой:

```text
/models
```

OpenCode поддерживает множество провайдеров и локальные модели. <citation src="2,6,7"></citation>

```bash
vim ~/.config/opencode/opencode.json
```

Затем создай в нужной папке файл `opencode.json` с настройкой провайдера:

```json
{
  "$schema": "https://opencode.ai/config.json",
    "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama (local)",
      "options": {
        "baseURL": "http://localhost:11434/v1"
      },
      "models": {
        "deepseek-r1:8b": {
          "name": "DeepSeek R1 8B (Ollama)"
        },
        "qwen3.5:4b": {
          "name": "Qwen 3.5 4B (Ollama)"
        },
        "llama3.2:3b": {
          "name": "llama 3.2 3b (Ollama)"
        }
      }
    }
  },
  "model": "ollama/deepseek-r1:8b"
}
```

Запусти OpenCode в этой папке и выбери модель через `/models`. Ollama должен быть запущен. <citation src="6"></citation>

### 4. Начни работу

Перейди в папку, с которой OpenCode может работать, и запусти его там:

```bash
cd ~/Documents
opencode
```

В чате можно попросить, например: «Просуммируй содержимое файла `meeting-notes.txt`» или «Найди в этой папке документы о бюджете». Для изучения проекта без внесения правок переключись клавишей **Tab** в режим `plan`; по умолчанию агент `build` может редактировать файлы. <citation src="2"></citation>


## 6. Конфигурация Qwen Code

##### Создай конфиг Qwen Code

```bash
vim ~/.qwen/settings.json
```

Содержимое:

```json
{
  "env": {
    "OLLAMA_API_KEY": "ollama"
  },
  "modelProviders": {
    "openai": [
      {
        "id": "qwen-code-local",
        "name": "Qwen2.5 3B (Ollama)",
        "envKey": "OLLAMA_API_KEY",
        "baseUrl": "http://localhost:11434/v1",
        "generationConfig": {
          "timeout": 300000,
          "streamIdleTimeoutMs": 600000,
          "maxRetries": 1,
          "contextWindowSize": 32768,
          "samplingParams": {
            "temperature": 0.2,
            "top_p": 0.9,
            "max_tokens": 4096
          }
        }
      }
    ]
  }
}
```

Это использует OpenAI-compatible endpoint Ollama на `http://localhost:11434/v1` и подходит для локальных моделей. `envKey` — это имя переменной окружения, а не сам ключ. Для Ollama можно поставить любое значение, например `ollama`. <citation src="3"></citation>

##### Задай переменную окружения

```bash
export OLLAMA_API_KEY=ollama
```

Чтобы сохранить навсегда:

```bash
echo 'export OLLAMA_API_KEY=ollama' >> ~/.bashrc
```

```bash
echo 'export OLLAMA_API_KEY=ollama' >> ~/.zshrc
```

```bash
echo 'export OLLAMA_API_KEY=ollama' >> ~/.config/fish/config.fish
```

```bash
source ~/.bashrc
```
