# VIM

## Basic actions

To permanently apply the following, you can put them in the `.vimrc` file in your home directory.

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

**Installation guide**

See (Volt Github repo)[https://github.com/vim-volt/volt#install].

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

**Installation guide**

```bash
volt get https://github.com/frazrepo/vim-rainbow
```

**Usage**

Enable the plugin globally, add the following to `.vimrc`:

```bash
let g:rainbow_active = 1
```
