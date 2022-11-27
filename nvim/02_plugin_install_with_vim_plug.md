# Plugins with Vim-Plug

---

Vim-Plug is a Plugin for Vim that acts as a Plugin Manager for Vim. You can install/uninstall/Update any vim plugin from Github using Vim-Plug. We'll Setup the Vim-Plug first, then we will setup more plugins using Vim-Plug.
Install Vim-Plug:

- On Mac

```
brew install neovim
```
- Ubuntu
```sh
sudo apt install neovim
```
- Arch
```sh
sudo pacman -S neovim
```

---

### Create config

Creating Folder for All NVIM Configuration Files:
```sh
mkdir ~/.config/nvim
```

All the config files/plugins will be in `~/.config/nvim/` here. All the configs, key-mappings will be linked to `init.vim` file.
Create `init.vim` file:
```sh
touch ~/.config/nvim/init.vim
```

---

### Install vim-plug

Download the `Vim-Plug` plugin to `~/.config/nvim/autoload` folder using:

```
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

You should now have `plug.vim` in your autoload directory. So, it will load automatically when you start nvim.

---

### Add a new file for plugins

If you have done everything in order, you already have nvim installed, vim-plug plugin manager on your system and you have some folders:
```
~/.config/nvim
~/.config/nvim/init.vim
~/.config/nvim/autoload/plug.vim
```

We will Create another directory and file and all the plugins for Vim-Plug will be added there:
```
mkdir ~/.config/nvim/vim-plug

touch ~/.config/nvim/vim-plug/plugins.vim
```

---

### Let's add some plugins


Add the following to `~/.config/nvim/vim-plug/plugins.vim`

```
" auto-install vim-plug
if empty(glob('~/.config/nvim/autoload/plug.vim'))
  silent !curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  "autocmd VimEnter * PlugInstall
  "autocmd VimEnter * PlugInstall | source $MYVIMRC
endif

call plug#begin('~/.config/nvim/autoload/plugged')

    " Better Syntax Support
    Plug 'sheerun/vim-polyglot'
    " File Explorer
    Plug 'scrooloose/NERDTree'
    " Auto pairs for '(' '[' '{'
    Plug 'jiangmiao/auto-pairs'

call plug#end()
```

---

### Source your plugins

Add the following line to `init.vim`:
```
source $HOME/.config/nvim/vim-plug/plugins.vim
```

---

### Vim-plug commands

If you done everything all right, then you should have already installed your vim-plug plugin manager.
- Open nvim using: `nvim`
- Check the status of your all neovim plugins: `:PlugStatus`
- Install all of your plugins: `:PlugInstall`
- To update your plugins: `:PlugUpdate`
- After the update you can press `d` to see the differences or run: `:PlugClean`
- To remove plugins that are no longer defined in the `plugins.vim` file:`:PlugClean`
- Finally if you want ot upgrade vim-plug itself run the following: `:PlugUpgrade`

---

### Where did I learn all this?

[Home Page](/README.md "Home Page") |  [Check out vim-plug on github](https://github.com/junegunn/vim-plug "https://github.com/junegunn/vim-plug") | [Next Page](/nvim/03_neovim_setting_up_the_basics.md "https://github.com/abuzafarhaqq/linux-help/blob/main/nvim/03_neovim_setting_up_the_basics.md")
