# 🚀 Getting Started

AstroNvim is an aesthetically pleasing and feature-rich neovim config that is extensible and easy to use with a great set of plugins

## 🧰 Installation

[Our configuration template](https://github.com/AstroNvim/template) is an easy way to going with AstroNvim. The template provides a directory structure with the required files in place. Within the files some indication, through commented out code, of how to configure the feature. Here are the instructions for installing this template:

1. **Make a backup of your current nvim config** _(if exists)_
    
```bash
mv ~/.config/nvim ~/.config/nvim.bak
```
    
2. **Clean neovim folders** _(Optional but recommended)_
    
```bash
mv ~/.local/share/nvim ~/.local/share/nvim.bak
```

```bash
mv ~/.local/state/nvim ~/.local/state/nvim.bak
```

```bash
mv ~/.cache/nvim ~/.cache/nvim.bak
```
    
3. **Clone the repository**

```bash
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/nvim
```

```bash
rm -rf ~/.config/nvim/.git
```

```bash
nvim
```

## 📦 Setup

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
    
- **Reload AstroNvim** (_EXPERIMENTAL_)
    
    Run `:AstroReload` to reload the AstroNvim configuration and any new user configuration changes without restarting. This is currently an experimental feature and may lead to instability until the next restart.

## 🔧 Configuration

To begin making customizations simply treat your `nvim` folder as your own Neovim configuration! This can be synced to a git repository to backup as well. AstroNvim is simply a plugin managed by the Lazy package manager that provides it’s own collection of plugins and their configurations.

### 🚀 The Starter Template

If you followed the instructions in this guide for installation, you are probably starting out with our template configuration. This comes with the following basic structure:

- Directory~/.config/nvim/
    
    - README.md
    - init.lua bootstrap the lazy plugin manager
    - Directorylua/
        - community.lua import AstroCommunity plugin specs
        - lazy_setup.lua configure and setup lazy.nvim
        - Directoryplugins/ configure plugins
            - astrocore.lua
            - astrolsp.lua
            - astroui.lua
            - mason.lua
            - none-ls.lua
            - treesitter.lua
            - user.lua
            - … add more files here as needed
        - polish.lua file executed last with arbitrary Lua
    