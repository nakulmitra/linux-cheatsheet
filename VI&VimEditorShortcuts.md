# VI/Vim Editor Shortcuts

## How to Delete a Line in a File
| Command | Description |
|---------|-------------|
| `dd` | Delete current line |
| `ndd` | Delete next `n` lines |
| `d$` | Delete from cursor to end of line |

## How to Undo in Vim
| Command | Description |
|---------|-------------|
| `u` | Undo last change |
| `U` | Undo all changes on the current line |
| `Ctrl + r` | Redo the undone changes |

## How to Replace or Append to a File in Linux
| Command | Description |
|---------|-------------|
| `vim filename` | Open file in editor |
| `:set paste` | (optional) Turn on paste mode |
| `i` or `a` | Insert/append content |
| `:w` | Save file |
| `:r filename2` | Append contents of `filename2` into the current file |

## Search a Word or String in Vim
| Command | Description |
|---------|-------------|
| `/word` | Search **forward** for "word" |
| `?word` | Search **backward** for "word" |
| `n` | Go to next match |
| `N` | Go to previous match |

## Save and Exit in Vim
| Command | Description |
|---------|-------------|
| `:w` | Save the file |
| `:wq` or `ZZ` | Save and exit |
| `:x` | Save and exit (only if changes exist) |

## Exit Without Saving in Vim
| Command | Description |
|---------|-------------|
| `:q!` | Quit without saving changes |

## Go to Start or End of a Line
| Command | Description |
|---------|-------------|
| `0` | Move to **beginning** of the line (column 0) |
| `^` | Move to **first non-whitespace** character in the line |
| `$` | Move to the **end** of the current line |

## Add a Line Before or After Current Line
| Command | Description |
|---------|-------------|
| `o` | Open a new line **below** the current line and enter Insert Mode |
| `O` | Open a new line **above** the current line and enter Insert Mode |

> Tip: After adding the new line, type your content and press `Esc` to return to Normal Mode.

## Replace Text Using Vim
| Command | Description |
|---------|-------------|
| `:s/old/new/` | Replace first occurrence of `old` with `new` in current line |
| `:s/old/new/g` | Replace all occurrences in current line |
| `:%s/old/new/g` | Replace all occurrences in the file |
| `:%s/old/new/gc` | Replace all occurrences with confirmation prompt |

## How to Show Line Numbers in Vim
If line numbers aren't visible, you can enable them in Normal Mode:

| Command | Description |
|---------|-------------|
| `:set number` or `:set nu` | Show line numbers |
| `:set relativenumber` | Show **relative** line numbers (useful for jumping lines with `d5j`, etc.) |
| `:set nonumber` | Hide line numbers |
| `:set norelativenumber` | Hide relative numbers |

> To make line numbers always show, add `set number` to your `~/.vimrc` file.