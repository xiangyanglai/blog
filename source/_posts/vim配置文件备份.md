---
title: vim配置文件备份
date: 2016-10-04 16:49:23
tags: vim
---

``` 

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"  => general vim setting
"
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" set how many lines of history VIM has to remeber
set history=700
" enable filetype plugins
filetype plugin on
filetype indent on
" show line number
set nu
" auto read when a file has been changed from the outside
set autoread
" set the lines to the cursor,when moving vertically with the key j/k
set so=7
" when we are in last line mode,the code completion will show above the command
" line
set wildmenu
" ignore compiled files,when we use e command to open the specified files
set wildignore=*.o,*~,*.pyc
" always show the current position
set ruler
" highlight search results
set hlsearch
" make search act like search in modern browsers,that's once you type one word
" the word will highlight,one more word one more highlight
set incsearch
" don't redraw while excting macros(good performance config)
set lazyredraw

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" =>colors and fonts
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"enable syntax highlighting
syntax enable
colorscheme desert
set background=dark
" set extra options when running in GUI mode
if has("gui_running")
    set guioptions-=T
    set guioptions-=e
    set t_Co=256
    set guitablabel=%M\ %t
endif
" set utf-8 as standard encoding(auto change other file encoding) and en_US as the standard language
set encoding=utf-8 fileencodings=ucs-bom,utf-8,cp936
" show the status line
" set statusline and in specifed format
set statusline=\ %{HasPaste()}%F%m%r%h\ %w\ \ CWD:\ %r%{getcwd()}%h\ \ \ Line:\ %l\ \ \ [Pos:\ %l,%v][%p%%]
function! HasPaste()
    if &paste
        return 'PASTE MODE'
    en
    return ''
endfunction

"set statusline=%F%m%r%h%w\ \ \ \ \ \ [file:\ %{&ff}]\ \ [Type:\ %Y]\ \ \ \ \ \ [Pos:\ %l,%v][%p%%]\ \ [Len:\ %l/%L]
set laststatus=2

```
<!-- more --> 

```

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Files, backups and undo
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set nobackup
set nowb
set noswapfile
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"=> Text, tab and indent related
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Use spaces instead tabs
set expandtab
" set 1 tab=4 spaces
set shiftwidth=4
set tabstop=4
" Linebreak on 500 characters
set lbr
set tw=500
" Auto indent
set ai
" Smart indent
set si
" Wrap lines
set wrap

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"=> Visual Model Related
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" search the current selected word
vnoremap <slient> * :call VisualSelection('f')<CR>
vnoremap <slient> # :call VisualSelection('b')<CR>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Moving around, tabs, windows and buffers
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Treat long lines as bread lines(useful when moving around in them)
map j gj
map k gk
" Map <Space> to / (search) and Ctr-<Space> to ?(backwards search)
map <space> /
map <c-space> ?
" Smart way to move between windows
nnoremap <c-h> <c-w>h
nnoremap <c-j> <c-w>j
nnoremap <c-k> <c-w>k
nnoremap <c-l> <c-w>h
" Increase and decrease window width and height
nnoremap <C-S-Left> 5<c-w><
nnoremap <C-S-Down> 5<c-w>-
nnoremap <C-S-Up> 4<c-w>+
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Plugins Configuration
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Create tags
set tags+=/home/lxy/.vim/sys_tags
nmap <F12> :!ctags -R --c++-kinds=+p --fields=+iaS --extra=+q .<CR>
" Tlist Configuration
"only show one file's tag
let Tlist_Show_One_File=1
"when there's only window,exit vim
let Tlist_Exit_OnlyWindow=1
"show taglist menu
let Tlist_Show_Menu=1
"auto update tags
nmap <silent> <F7> :TlistUpdate<cr>
"combine taglist and winmanager,and show them together
let g:winManagerWindowLayout='FileExplorer|TagList'
nmap <silent> <F8> :WMToggle<cr>
" OmniCpp configuration
set completeopt=menu
let OmniCpp_MayCompleteDot = 1 " autocomplete with .
let OmniCpp_MayCompleteArrow = 1 " autocomplete with ->
let OmniCpp_MayCompleteScope = 1 " autocomplete with ::
let OmniCpp_SelectFirstItem = 2 " select first item (but don't insert)
let OmniCpp_NamespaceSearch = 2 " search namespaces in this and included files
let OmniCpp_ShowPrototypeInAbbr = 1 " show function prototype  in popup window
let OmniCpp_GlobalScopeSearch=1
let OmniCpp_DisplayMode=1
let OmniCpp_DefaultNamespaces=["std"]
set cursorline
set cursorcolumn

```