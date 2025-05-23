# Mac

## Keyboard shortcut

### Symboles

Symbole | FR Shortcut     | CH DE Shortcut
------- | --------------- | ----------- 
\|      | Alt + Maj + L   | Alt + 7
\       | Alt + Maj + /   | Alt + Maj + 7
[       | Alt + Maj + (   | Alt + 5
]       | Alt + Maj + )   | Alt + 6
{       | Alt + (         | Alt + 8
}       | Alt + )         | Alt + 9
 
### Systeme

Shortcut            | Action
------------------- | ------------- 
Ctrl + Cmd + Q      | Lock the screen
Cmd + Alt + Maj + V | Past whithout formatting
Cmd + Maj + R       | Reload the navigator window
Cmd + Maj + D       | Once in the finder, go to Desktop
Cmd + Maj + H       | Once in the finder, go to Home

## Shell config

Check which shell is used:

```bash
echo $SHELL
```

Switch to a bash shell:

```bash
chsh -s /bin/bash
```

## Package managment

Install [Homebrew](https://brew.sh/):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Packages

Here is the list of packages I usually use:

- [Rectangle](https://github.com/rxhanson/Rectangle)

Here is how to install this packages using the terminal:

```
brew install rectangle
```

## Some easy fix

Remove the binary malware virification:

```bash
sudo xattr -rc $BINARY
```
