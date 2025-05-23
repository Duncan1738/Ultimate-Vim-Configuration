PROJECT TITLE: Ultimate Vim Configuration

PURPOSE OF PROJECT:
A comprehensive guide to configuring Vim as a modern, efficient code editor.
This project provides everything from installation steps to plugin integration
for syntax highlighting, code completion, file browsing, and a polished UI.

VERSION or DATE: 24 May 2025

HOW TO START THIS PROJECT:

Step 1 – Install Vim:

Linux (Debian/Ubuntu):
  sudo apt install vim

macOS (Homebrew):
  brew install vim

Windows (PowerShell with Chocolatey):
  choco install vim

Alternatively download from: https://www.vim.org/download.php

Step 2 – Install Plugin Manager (vim-plug):

PowerShell / Command Prompt:
  curl -fLo %USERPROFILE%\\vimfiles\\autoload\\plug.vim --create-dirs ^
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

Linux/macOS Terminal:
  curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

Step 3 – Create .vimrc File:

Linux/macOS:
  touch ~/.vimrc

Windows PowerShell:
  ni $HOME/.vimrc

Paste the following content into `.vimrc`:

------------------ BEGIN .vimrc ------------------
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

" Navigation & Search
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
------------------- END .vimrc -------------------

Step 4 – Open Vim and Run:

  :source ~/.vimrc
  :PlugInstall

AUTHORS:
Advanced Vim Setup by ChatGPT, inspired by the Vim community

USER INSTRUCTIONS:

- Use `Ctrl + N` to toggle file explorer (NERDTree)
- Use `Ctrl + S` to save
- Exit insert mode quickly with `jk`
- Use `gcc` to comment lines
- Install language servers via:
    :CocInstall coc-json coc-python coc-tsserver coc-html coc-css

OPTIONAL – Install Node.js (for Coc):

Linux/macOS:
  curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
  sudo apt install -y nodejs

Windows (PowerShell):
  choco install nodejs-lts

TROUBLESHOOTING:

- Plugin not working? Try:
    :PlugInstall
    :PlugClean

- Coc not responding?
    :CocInfo

- No syntax highlighting?
    Make sure `syntax enable` is in .vimrc

- To run without config:
    vim -u NONE

NOTES:
This is a fully functional, minimal Vim IDE setup. Easily extendable and built for modern development.
