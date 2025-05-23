PROJECT TITLE: Ultimate Vim Configuration

PURPOSE OF PROJECT:
A full setup guide to configure Vim as a fast, modern development environment.
Includes plugin support, code completion, navigation, syntax highlighting, and themes.

VERSION or DATE: 24 May 2025

HOW TO START THIS PROJECT:

Step 1 – Install Vim
---------------------

1.1 For Debian/Ubuntu:

    sudo apt install vim

1.2 For macOS (Homebrew):

    brew install vim

1.3 For Windows (PowerShell with Chocolatey):

    choco install vim

Alternatively, download Vim manually: https://www.vim.org/download.php

---

Step 2 – Install vim-plug (Plugin Manager)
------------------------------------------

2.1 For Linux/macOS:

    curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
         https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

2.2 For Windows (PowerShell):

    curl -fLo $HOME\\vimfiles\\autoload\\plug.vim --create-dirs `
         https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

---

Step 3 – Create the `.vimrc` File
---------------------------------

3.1 For Linux/macOS:

    touch ~/.vimrc

3.2 For Windows:

    ni $HOME/.vimrc

---

Step 4 – Paste the following into `.vimrc`
------------------------------------------
" Base Settings
syntax enable
filetype plugin indent on
set number relativenumber
set tabstop=4 shiftwidth=4 expandtab
set smartindent autoindent
set clipboard=unnamedplus
set cursorline
set mouse=a
set nowrap
set incsearch
set hlsearch
set ignorecase
set smartcase
set splitbelow
set splitright
set termguicolors

" Plugin Section
call plug#begin('~/.vim/plugged')

" Essentials
Plug 'tpope/vim-sensible'
Plug 'tpope/vim-commentary'
Plug 'jiangmiao/auto-pairs'

" File Explorer and Search
Plug 'preservim/nerdtree'
Plug 'junegunn/fzf.vim'

" UI Enhancements
Plug 'vim-airline/vim-airline'
Plug 'morhetz/gruvbox'

" Code Completion
Plug 'neoclide/coc.nvim', {'branch': 'release'}

call plug#end()

" Key Mappings
command! W w
nnoremap <C-n> :NERDTreeToggle<CR>
noremap <C-s> :w<CR>
inoremap jk <Esc>
nnoremap <leader><space> :noh<CR>

" Theme
colorscheme gruvbox
set background=dark


---

Step 5 – Install the Plugins
----------------------------

5.1 Open Vim and run:

    :source ~/.vimrc
    :PlugInstall

---

Step 6 – Install Node.js (Required for coc.nvim)
-------------------------------------------------

6.1 For Debian/Ubuntu:

    curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    sudo apt install -y nodejs

6.2 For Windows:

    choco install nodejs-lts

---

Step 7 – Install Language Support in Vim
----------------------------------------

Open Vim and run:

    :CocInstall coc-json coc-python coc-tsserver coc-html coc-css

This adds intelligent auto-completion for JSON, Python, JS/TS, HTML, and CSS.

---

Step 8 – Test the Configuration
-------------------------------

Try:

```bash
vim test.py
vim test.html

Inside Vim:

:NERDTreeToggle to toggle file explorer

Type console. in a .js file to see autocompletion

Type { and it should auto-close

Use gcc to comment a line

TROUBLESHOOTING
Plugins not working?
Run: :PlugClean then :PlugInstall

Coc.nvim unresponsive?
Run: :CocInfo

Syntax highlighting not working?
Ensure syntax enable is in your .vimrc

Debug without config:
Run: vim -u NONE

