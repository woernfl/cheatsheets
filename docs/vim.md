# VIM

## Basic actions

To permanently apply the following, you can put them in the `.vimrc` file in your home directory.

To display line numbers:

```
:set number
```

To remove line numbers:

```
:set nonumber
```

Save the file:

```
:w
```

Exit the file:

```
:q
```

## Clipboard

Cut:

```
dd
```

Copy:

```
yy
```

Paste:

```
p
```

Paste before:

```
P
```

## Editing

Append:

```
:a
```

Insert:

```
:i
```

Undo changes

```
:u
```

Redo changes

```
Ctrl + r
```

Search

```
/$STRING_TO_SEARCH_FOR
```

Search and replace

```
:s/search/replace/
```

Search and replace an entire file

```
:%s/search/replace/
```

## Navigation

Go to specific line number:

```
:$LINE_NUMBER
```

Got to the first line:

```
gg
```

Got to the last line:

```
G
```

Go page up:

```
Ctrl + u
```

Go page down:

```
Ctrl + d
```

Go to the start of the line after whitespaces:

```
^
```

Go to the end of the line:

```
$
```
