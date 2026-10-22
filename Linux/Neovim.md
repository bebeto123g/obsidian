
**🚀 AstroNvim** больше похож на заранее собранную и оформленную IDE для Neovim. Он удобен, если хочется сразу получить цельную рабочую среду с большим количеством функций.

**LazyVim** больше похож на хорошо подготовленный фундамент для собственной конфигурации. Он особенно удобен, если вы хотите постепенно менять стандартное поведение и собирать Neovim под свои привычки.

Если вы только начинаете пользоваться готовыми конфигурациями Neovim, разумный выбор такой:

- **AstroNvim** — если важны готовый внешний вид и максимальная функциональность из коробки.
- **LazyVim** — если важнее гибкость, обучение и постепенная кастомизация.

##  💤 LazyVim install

```bash
mv ~/.config/nvim ~/.config/nvim.bak
```
```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim
```
```bash
rm -rf ~/.config/nvim/.git
```
```bash
nvim
```
```sh
:LazyHealth
```

! Рекомендуется запустить команду `:LazyHealth` после установки. Это загрузит все плагины и проверит, всё ли работает корректно.

[Документация](https://www.lazyvim.org/)
##  🚀 AstroVim install

```bash
mv ~/.config/nvim ~/.config/nvim.bak
```
```bash
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/nvim
```
```bash
rm -rf ~/.config/nvim/.git
```
```bash
nvim
```

#### 📦 Setup

- **Install LSP**
    
    Enter `:LspInstall` followed by the name of the server you want to install
    
    > Example: `:LspInstall pyright`
    
- **Install language parser**
    
    Enter `:TSInstall` followed by the name of the language you want to install
    
    > Example: `:TSInstall python`
    
- **Install Debugger**
    
    Enter `:DapInstall` followed by the name of the debugger you want to install
    
    > Example: `:DapInstall python`
    
- **Manage plugins**
    
    - Run `:Lazy check` (`<Leader>pu`) to check for plugin updates
    - Run `:Lazy update` (`<Leader>pU`) to apply any pending plugin updates
    - Run `:Lazy sync` (`<Leader>pS`) to update and clean plugins
    - Run `:Lazy clean` to remove any disabled or unused plugins
    
- **Update Mason packages and plugins**a
    
    Run `:AstroUpdate` (`<Leader>pa`) to update both Neovim plugins and Mason packages
    
- **Check AstroNvim version**
    
    Run `:AstroVersion` to display the currently installed AstroNvim version

#### 📦 #### Копирование для AstroVim


**Для работы с системным буфером обмена** в [AstroNvim](https://www.google.com/goto?url=CAESTgHrOzAVZAtzcFNoAzMbi0OcvhpWNUgRE9uA1TSQExjUU6eB01-BMVJJS270K-vt_aAAB20RZQ2k81-RlJTtojl96ikn3CeyeUwOTBZ8rQ) (сборка Neovim) на **Debian 13** используются стандартные команды Neovim, но для их работы в системе должны быть установлены специальные утилиты, умеющие общаться с графическим сервером (X11 или Wayland).

Шаг 1: Подготовка системы (Важно)

Neovim не сможет скопировать текст в буфер вашей графической оболочки без сторонней утилиты. Откройте терминал и установите нужный пакет в зависимости от того, какая сессия у вас запущена:

```bash
sudo apt install wl-clipboard
```

_После установки перезапустите AstroNvim._

---

Шаг 2: Копирование и вставка штатными командами

AstroNvim по умолчанию настроен так, что операции копирования обращаются к системному регистру буфера обмена (`+`), если в системе установлены `wl-clipboard` или `xclip`.

Из AstroNvim во внешнюю программу (Браузер, Telegram, VS Code):

1. Перейдите в визуальный режим, нажав кнопку **`v`** (посимвольно) или **`V`** (построчно).
2. Выделите нужный текст стрелочками или клавишами перемещения (`h`, `j`, `k`, `l`).
3. Нажмите **`y`** (yank — скопировать).
4. В другой программе вставьте текст обычным способом (**`Ctrl + V`**). 

_Если базовая клавиша `y` не сработала с системным буфером, используйте явное указание системного регистра: после выделения текста нажмите последовательно три клавиши: **`"+y`**._ 

Из внешней программы в AstroNvim:

1. Скопируйте текст в браузере или документе с помощью **`Ctrl + C`**.
2. В AstroNvim в **нормальном режиме (Normal mode)** (нажмите `Esc`, чтобы выйти из режима ввода) нажмите клавишу **`p`** (paste). Текст вставится после курсора.
3. Либо нажмите **`P`** (заглавную), чтобы вставить текст _до_ курсора. 

_Если не срабатывает, используйте команду **`"+p`** в нормальном режиме._

---

Шаг 3: Как быстро скопировать/вставить мышкой

Если вам привычнее использовать мышь, терминалы в Debian 13 поддерживают встроенные горячие клавиши, которые работают в обход внутренних регистров редактора: 

- **Копирование:** Выделите текст мышкой в окне терминала и нажмите **`Ctrl + Shift + C`**.
- **Вставка:** Поставьте курсор в AstroNvim, перейдите в **режим вставки** (нажмите **`i`**) и нажмите **`Ctrl + Shift + V`**.

_В некоторых графических терминалах Linux достаточно просто выделить текст мышью (он сразу попадает в выделенный буфер) и вставить его в нужном месте кликом на **колесико мыши (среднюю кнопку)**._
