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

Undo changes

```bash
:u
```

Redo changes

```bash
Ctrl + r
```

Search

```bash
/$STRING_TO_SEARCH_FOR
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

Go to the start of the line after whitespaces:

```bash
^
```

Go to the end of the line:

```bash
$
```

## Vim plugins

### Volt

A meta-level vim package manager available [here](https://github.com/vim-volt/volt).

**Installation**

See [Volt Github repo](https://github.com/vim-volt/volt#install).

**Usage**

Install a vim plugin:

```bash
volt get https://github.com/frazrepo/vim-rainbow
```

Update plugins:

```bash
# Update all plugins
volt get -l -u

# Update a specific plugin
volt get -u https://github.com/frazrepo/vim-rainbow
```

Uninstall plugins:

```bash
volt rm https://github.com/frazrepo/vim-rainbow
```

### Vim-rainbow

Rainbow brackets for Vim available [here](https://github.com/frazrepo/vim-rainbow).

**Installation**

```bash
volt get https://github.com/frazrepo/vim-rainbow
```

**Usage**

Enable the plugin globally, add the following to `.vimrc`:

```bash
let g:rainbow_active = 1
```

### NERDTree

Rainbow brackets for Vim available [here](https://github.com/scrooloose/nerdtree).

**Installation**

```bash
volt get https://github.com/scrooloose/nerdtree
```

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

### Vim-gitgutter

A Vim plugin which shows a git diff in the gutter and stages/undoes hunks and partial hunks available [here](https://github.com/airblade/vim-gitgutter).

**Installation**

```bash
volt get https://github.com/airblade/vim-gitgutter
```

**Usage**

Enable the plugin globally, add the following to `.vimrc`:

```bash
let g:gitgutter_enabled = 1
```

## Overal basic setup

1. Install `volt`:

    See instructions [here](#volt)

2. Install the `vim` pluggins:

```bash
volt get https://github.com/frazrepo/vim-rainbow
volt get https://github.com/scrooloose/nerdtree
volt get https://github.com/airblade/vim-gitgutter
```

3. Create a `~/.vimrc` file:

```bash
set number
syntax enable

let g:rainbow_active = 1

let g:gitgutter_enabled = 1

map <F2> :NERDTreeToggle<CR>
```
