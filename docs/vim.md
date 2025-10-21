# VIM

## Basic actions

To permanently apply the following, you can put them in the `~/.vimrc` file in your home directory.

To display line numbers:

```bash
:set number
```

To remove line numbers:

```bash
:set nonumber
```

Save the file:

```bash
:w
```

Exit the file:

```bash
:q
```

Comment from line 1 to 8:

```bash
:1,8s/^/#
```

Uncomment from line 1 to 8:

```bash
:1,8s/^#/
```

## Clipboard

Cut:

```bash
dd
```

Copy:

```bash
yy
```

Paste:

```bash
p
```

Paste before:

```bash
P
```

## Editing

Append:

```bash
:a
```

Insert:

```bash
:i
```

Undo changes:

```bash
:u
```

Redo changes:

```bash
Ctrl + r
```

Search:

```bash
/$STRING_TO_SEARCH_FOR
```

Search a specific string:

```bash
/\<$STRING_TO_SEARCH_FOR\>
```

Search ignoring the case:

```bash
/$STRING_TO_SEARCH_FOR\c
```

Search and replace

```bash
:s/$STRING_TO_SEARCH_FOR/$STRING_TO_REPLACE_WITH/
```

Search and replace an entire file

```bash
:%s/$STRING_TO_SEARCH_FOR/$STRING_TO_REPLACE_WITH/
```

## Navigation

Go to specific line number:

```bash
:$LINE_NUMBER
```

Got to the first line:

```bash
gg
```

Got to the last line:

```bash
G
```

Go page up:

```bash
Ctrl + u
```

Go page down:

```bash
Ctrl + d
```

Go to the end of the current word:

```bash
e
```

Go to the beginning of the next word:

```bash
w
```

Go to the beginning of the previous word:

```bash
b
```

Go to the start of the line after whitespaces:

```bash
^
```

Go to the end of the line:

```bash
$
```

Navigate blocks of code:

```bash
# Move one code block up
Shift-{
# Move one code block down
Shift-}
```

Navigate blocks of code:

```bash
# Move one code block up
Shift-{
# Move one code block down
Shift-}
```

## Miscellaneous

Set password protection to a file:

```bash
vim -x $PATH_TO_THE_FILE
```

## Vim plugins

### vim-plug

vim-plug for Vim available [here](https://github.com/junegunn/vim-plug). Installed using the `~/.vimrc` file provided in the overal basic setup section.

### vim-rainbow

vim-rainbow for Vim available [here](https://github.com/frazrepo/vim-rainbow).

### NERDTree

NERDTree for Vim available [here](https://github.com/scrooloose/nerdtree).

**Usage**

Activate NERDTree:

```bash
:NERDTree
```

Close NERDTree:

```bash
:NERDTreeClose
```

Toggle NERDTree:

```bash
:NERDTreeToggle
```

Or add this line to your `.vimrc` file to to toggle when you hit `F2` key:

```bash
map <F2> :NERDTreeToggle<CR>
```

Keyboard shortcuts:

- `t`: Open the selected file in a new tab
- `i`: Open the selected file in a horizontal split window
- `s`: Open the selected file in a vertical split window
- `I`: Toggle hidden files
- `R`: Refresh the tree, useful if files change outside of Vim
- `Ctrl + w w`: Cycle though all windows
- `Ctrl + w h`: Takes you left a window
- `Ctrl + w j`: Takes you down a window
- `Ctrl + w k`: Takes you up a window
- `Ctrl + w l`: Takes you right a window

## Overal basic setup

1. Create a `~/.vimrc` file:

```bash
" Install vim-plug if not found
if empty(glob('~/.vim/autoload/plug.vim'))
  silent !curl -fLo ~/.vim/autoload/plug.vim --create-dirs
    \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
endif

" Run PlugInstall if there are missing plugins
autocmd VimEnter * if len(filter(values(g:plugs),'!isdirectory(v:val.dir)'))
  \| PlugInstall --sync | source $MYVIMRC
\| endif

call plug#begin()
" The default plugin directory will be as follows:
"   - Vim (Linux/macOS): '~/.vim/plugged'

" Make sure you use single quotes

Plug 'junegunn/vim-plug'
Plug 'https://github.com/frazrepo/vim-rainbow'
Plug 'https://github.com/scrooloose/nerdtree'
Plug 'https://github.com/vim-airline/vim-airline'

" Initialize plugin system
call plug#end()

set number
syntax enable
set laststatus=2
colorscheme delek

let g:rainbow_active = 1
map <F4> :RainbowToggle<CR>

map <F2> :NERDTreeToggle<CR>
```
