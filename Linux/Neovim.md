
**🚀 AstroNvim** больше похож на заранее собранную и оформленную IDE для Neovim. Он удобен, если хочется сразу получить цельную рабочую среду с большим количеством функций.

**LazyVim** больше похож на хорошо подготовленный фундамент для собственной конфигурации. Он особенно удобен, если вы хотите постепенно менять стандартное поведение и собирать Neovim под свои привычки.

Если вы только начинаете пользоваться готовыми конфигурациями Neovim, разумный выбор такой:

- **AstroNvim** — если важны готовый внешний вид и максимальная функциональность из коробки.
- **LazyVim** — если важнее гибкость, обучение и постепенная кастомизация.


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