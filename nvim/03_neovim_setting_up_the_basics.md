# Neovim Setting up the basics

### General Settings

---

To include some basics in your config list create a directory called general and a file called `settings.vim`

```
mkdir ~/.config/nvim/general

touch ~/.config/nvim/general/settings.vim
```

Here is every general settings I use with a brief explanation:
Add the following to settings.vim

```
" set leader key
let g:mapleader = "\<Space>"

syntax enable								" Enables syntax highlighting
set hidden									" Required to keep multiple buffers open multiple buffers
set nowrap									" Display long lines as just one line
set encoding=utf-8					" The encoding displayed
set pumheight=10						" Makes popum menu smaller
set fileencoding=utf-8			" The encoding written to file
set ruler 									" Show the cursor position all the time
set cmdheight=2							" More space for displaying messages
set iskeyword+=-						" treat dash separated words as a word text object
set mouse=a									" Enable your mouse
set splitbelow							" Horizontal splits will automatically be below
set splitright							" Vertical splits will automatically be to the right
set t_Co=256								" Support 256 colors
set conceallevel=0					" So that I can see `` in markdown files
set tabstop=2								" Insert 2 spaces for a tab
set shiftwidth=2						" Change the number of space characters inserted for indentation
set smarttab								" Makes tabbing smarter will realize you have 2 vs 4
set expandtab								" Converts tabs to spaces
set smartindent							" Makes indenting smart
set autoindent							" Good auto indent
set laststatus=0						" Always display the status line
set relativenumber  "Relative Line Numbers
set number    " relativenumber and number sets relativenumber line to non zero
set cursorline							" Enable highlighting of the current line
set background=dark					" tell vim waht the background color looks like
set showtabline=2						" Always show tabs
set noshowmode							" We don't need to see things like -- INSERT -- anymore
set nobackup								" This is recommended by coc
set nowritebackup						" This is recommended by coc
set updatetime=300					" Faster completion
set timeoutlen=500					" By deault timeoutlen is 1000 ms
set formatoptions-=cro			" Stop newline continution of comments
set clipboard=unnamedplus		" Copy paste between vim and everything else
"set autochdir								Your working directory will always be the same as your working directory
au! BufWritePost $MYVIMRC source % " auto source when writing to init.vm alternatively you can run :source $MYVIMRC
" You can't stop me
cmap w!! w !sudo tee %
```

Source to init.vim

```
source $HOME/.config/nvim/general/settings.vim
```

---

## Mapping new keys

Again we'll create a directory called keys and a file called mappings.vim

```
mkdir ~/.config/nvim/keys
touch ~/.config/nvim/keys/mappings.vim
```


Add the following to mappings.vim
```
" Better nav for omnicomplete
inoremap <expr> <c-j> ("\<C-n>")
inoremap <expr> <c-k> ("\<C-p>")

" -- File Mode [ SAVE, QUIT, SAVE+QUIT ]
nnoremap <C-s> :w<CR>
nnoremap <C-Q> :q!<CR>
nnoremap <C-q> :wq!<CR>

" -- VIM Window Resize [ LEADER+jkhl ]
nnoremap <leader>j :resize -2<CR>
nnoremap <leader>k :resize +2<CR>
nnoremap <leader>h :vertical resize -2<CR>
nnoremap <leader>l :vertical resize +2<CR>

" -- Vim Window Cursor Movement
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

" -- ESC Key Mapping
nnoremap <C-z> <Esc>
inoremap jk <Esc>
inoremap kj <Esc>

" Easy CAPS
inoremap <c-u> <ESC>viwUi
nnoremap <c-u> viwU<Esc>

" -- Tabs Settings
nnoremap <C-t> :tabnew<CR>
nnoremap <TAB> :tabnext<CR>
nnoremap <S-TAB> :tabprevious<CR>

" -- Buffers Next / Previous
" nnoremap <TAB> :bnext<CR>
" nnoremap <S-TAB> :bprevious<CR>

" <TAB>: completion
inoremap <expr><TAB> pumvisible() ? "\C-n" : "\<TAB>"

"Better tabbing
vnoremap < <gv
vnoremap > >gv

"Better window navigation
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l
nnoremap <Leader>o o<Esc>^Da
nnoremap <Leader>O O<Esc>^Da

" -- Visual Block Movement - Move Entire Block Up/Down
nnoremap <A-j> :m+<CR>==
nnoremap <A-k> :m-2<CR>==
inoremap <A-j> <Esc>:m+<CR>==gi
inoremap <A-k> <Esc>:m-2<CR>==gi
vnoremap <A-j> :m'>+<CR>gv=gv
vnoremap <A-k> :m-2<CR>gv=gv

```

Source in init.vim
```
source $HOME/.config/nvim/keys/mappings.vim
```

## Get healthy

---

Open `nvim` and enter the following:

```
:checkhealth
```

You'll probably notice you don't have support for copy/paste also that python and node haven't been setup. So let's fix that. First we'll fix copy/paste.
- On mac pbcopy should be builtin
- On Ubuntu
  `sudo apt install xsel`
- On Arch Linux
  `sudo pacman -S xsel`

Next we need to install python support (node is optional)
- Neovim python support
  `pip install pynvim`
- Neovim node support
  `npm i -g neovim`

### Note: If you use virtual environments I highly suggests putting these variables in your config. I recommend putting this in paths.vim in the general directory.

```
let g:python2_host_prog = expand("<path to python with pynvim installed>")
let g:python3_host_prog = expand("<~/.miniconda/envs/neovim/bin/python3.8>") " <- example

let g:node_host_prog = expand("<path to node with neovim installed>")
let g:node_host_prog = expand("~/.nvm/versions/node/v12.16.1/bin/node") " <- example
```

Run `cheackhealth` again and you should now see the requirements are met


[Previous Page](/nvim/02_plugin_install_with_vim_plug.md "Vim Plug Install") | [Home Page](/README.md) | [Next Page](/nvim/04_neovim_themes.md "Neovim Theme Setup") |
