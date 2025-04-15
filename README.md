# Linux Command Cheat Sheet
Welcome to the ultimate cheat sheet for essential **Linux** commands.
This repository is designed to help developers, sysadmins, and DevOps engineers quickly recall the most commonly used terminal commands.

## File and Directory Commands
| Command | Description |
|--------|-------------|
| `ls` | Lists files and directories in the current directory. Use `ls -l` for long listing format. |
| `cd <dir>` | Changes the current directory to `<dir>`. |
| `pwd` | Prints the current working directory. |
| `mkdir <dir>` | Creates a new directory named `<dir>`. |
| `rmdir <dir>` | Removes an empty directory named `<dir>`. |
| `rm -r <dir>` | Removes a directory and its contents recursively. |
| `rm <file>` | Deletes a file. Use `rm -f` to force delete without confirmation. |
| `touch <file>` | Creates a new, empty file or updates the timestamp of an existing file. |
| `cp <src> <dest>` | Copies files or directories. Use `cp -r` to copy directories. |
| `mv <src> <dest>` | Moves or renames files or directories. |
| `find <path> -name <filename>` | Searches for files and directories by name under the given path. |
| `tree` | Displays directory structure in a tree-like format. (Needs to be installed.) |

## File Content Commands
| Command | Description |
|--------|-------------|
| `cat <file>` | Displays the contents of a file. |
| `more <file>` | Views the content of a file page-by-page. |
| `less <file>` | Improved version of `more` with backward navigation. |
| `head <file>` | Shows the first 10 lines of a file. |
| `tail <file>` | Shows the last 10 lines of a file. Use `tail -f` to follow a file in real-time. |
| `wc <file>` | Counts lines, words, and characters in a file. |
| `cut -d':' -f1 <file>` | Cuts out sections from each line in a file, useful for parsing. |
| `grep <pattern> <file>` | Searches for a pattern in a file. Use `grep -r` to search recursively. |
| `diff <file1> <file2>` | Compares two files line by line. |

## How to Create a File in Linux
| Command | Description |
|---------|-------------|
| `touch filename` | Creates a new empty file. |
| `> filename` | Also creates a new empty file (overwrites if it exists). |
| `vim filename` | Opens the file in Vim (creates it if it doesn't exist). |

## How to Edit a File in Linux
1. Use `vim filename` to open the file.
2. Press `i` to enter **Insert Mode**.
3. Make your changes.
4. Press `Esc` to return to **Normal Mode**.
5. Use `:w` to **save**, `:q` to **quit**, or `:wq` to **save and quit**.

## VI/Vim Editor Shortcuts

### How to Delete a Line in a File
| Command | Description |
|---------|-------------|
| `dd` | Delete current line |
| `ndd` | Delete next `n` lines |
| `d$` | Delete from cursor to end of line |

### How to Undo in Vim
| Command | Description |
|---------|-------------|
| `u` | Undo last change |
| `U` | Undo all changes on the current line |
| `Ctrl + r` | Redo the undone changes |

### How to Replace or Append to a File in Linux
| Command | Description |
|---------|-------------|
| `vim filename` | Open file in editor |
| `:set paste` | (optional) Turn on paste mode |
| `i` or `a` | Insert/append content |
| `:w` | Save file |
| `:r filename2` | Append contents of `filename2` into the current file |

### Search a Word or String in Vim
| Command | Description |
|---------|-------------|
| `/word` | Search **forward** for "word" |
| `?word` | Search **backward** for "word" |
| `n` | Go to next match |
| `N` | Go to previous match |

### Save and Exit in Vim
| Command | Description |
|---------|-------------|
| `:w` | Save the file |
| `:wq` or `ZZ` | Save and exit |
| `:x` | Save and exit (only if changes exist) |

### Exit Without Saving in Vim
| Command | Description |
|---------|-------------|
| `:q!` | Quit without saving changes |

### Go to Start or End of a Line
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

## How to Enable Syntax Highlighting (Colored Text)
To turn on color-based syntax highlighting for code/configs:

| Command | Description |
|---------|-------------|
| `:syntax on` | Enable syntax highlighting |
| `:syntax off` | Disable syntax highlighting |

> For permanent syntax highlighting, add this to your `~/.vimrc`:
```
syntax on
```

## Cut, Copy & Paste in Vim

### Cut (Delete and store in buffer)
| Command | Description |
|---------|-------------|
| `dd` | Cut (delete) a line |
| `ndd` | Cut `n` lines |
| `dG` | Cut until end of file |

### Copy
| Command | Description |
|---------|-------------|
| `yy` | Copy a line |
| `nyy` | Copy `n` lines |
| `yG` | Copy until end of file |

### Paste
| Command | Description |
|---------|-------------|
| `p` | Paste **after** the cursor/line |
| `P` | Paste **before** the cursor/line |

## File Comparison Using Vim (`vimdiff`)
| Command | Description |
|---------|-------------|
| `vimdiff file1 file2` | Open both files side by side with differences highlighted |
| `:diffupdate` | Refresh the diff view |
| `do` | Get changes from the other file |
| `dp` | Put changes into the other file |
| `]c` / `[c` | Jump to next/previous change |
| `:qa` | Quit all when done comparing |

## Switching Between Files in `vimdiff`
When we're using `vimdiff file1 file2`, both files open side-by-side. Here's how to switch and manage between them:

| Command | Description |
|---------|-------------|
| `Ctrl + w h` | Move to the **left** split (file1) |
| `Ctrl + w l` | Move to the **right** split (file2) |
| `Ctrl + w w` | Toggle between splits |

## File Permission & Ownership
| Command | Description |
|--------|-------------|
| `chmod +x <file>` | Adds execute permission to a file. |
| `chmod 755 <file>` | Sets permission using numeric mode. |
| `chown <user>:<group> <file>` | Changes file owner and group. |
| `ls -l` | Shows detailed file permissions. |

## Process Management
| Command | Description |
|--------|-------------|
| `ps` | Lists running processes. Use `ps aux` for detailed info. |
| `top` | Interactive process viewer (press `q` to quit). |
| `htop` | Enhanced version of `top` (needs installation). |
| `kill <PID>` | Kills a process by ID. |
| `kill -9 <PID>` | Force kills a process. |
| `pkill <name>` | Kills processes by name. |
| `nice`, `renice` | Starts/changes process priority. |

## User Management
| Command | Description |
|--------|-------------|
| `whoami` | Displays current user. |
| `id` | Shows user ID and group ID. |
| `adduser <user>` | Adds a new user. |
| `passwd <user>` | Changes user password. |
| `su <user>` | Switches to another user. |
| `sudo <command>` | Runs a command as root/superuser. |

## Disk & Storage
| Command | Description |
|--------|-------------|
| `df -h` | Shows disk space usage in human-readable format. |
| `du -sh <dir>` | Shows size of a directory. |
| `mount` | Lists or mounts a file system. |
| `umount` | Unmounts a mounted file system. |
| `lsblk` | Lists block devices (like hard drives). |
| `fdisk -l` | Shows partition table (needs sudo). |

## Networking
| Command | Description |
|--------|-------------|
| `ping <host>` | Checks network connectivity. |
| `ifconfig` or `ip a` | Displays network interfaces (use `ip a` on modern distros). |
| `netstat -tulnp` | Lists network connections (use `ss` on newer systems). |
| `ss -tuln` | Shows listening ports and services. |
| `curl <url>` | Transfers data from or to a server. |
| `wget <url>` | Downloads files from the internet. |
| `scp <src> <user>@<host>:<dest>` | Securely copies files between machines. |
| `ssh <user>@<host>` | Connects to a remote server via SSH. |

## System Information
| Command | Description |
|--------|-------------|
| `uname -a` | Shows system information. |
| `uptime` | Shows system uptime. |
| `free -h` | Displays memory usage. |
| `top` / `htop` | Displays resource usage. |
| `hostname` | Displays system hostname. |
| `dmesg` | Shows boot and kernel messages. |

## Package Management (Debian-based systems like Ubuntu)
| Command | Description |
|--------|-------------|
| `apt update` | Updates package list. |
| `apt upgrade` | Installs available updates. |
| `apt install <package>` | Installs a package. |
| `apt remove <package>` | Removes a package. |
| `dpkg -i <package>.deb` | Installs a `.deb` package manually. |

## Package Management (RHEL/CentOS)
| Command | Description |
|--------|-------------|
| `yum install <package>` | Installs a package. |
| `yum remove <package>` | Removes a package. |
| `yum update` | Updates all packages. |

## Archive & Compression
| Command | Description |
|--------|-------------|
| `tar -cvf file.tar <dir>` | Creates a tar archive. |
| `tar -xvf file.tar` | Extracts a tar archive. |
| `tar -czvf file.tar.gz <dir>` | Creates a gzipped tarball. |
| `gzip <file>` | Compresses a file. |
| `gunzip <file.gz>` | Decompresses a `.gz` file. |
| `zip <file.zip> <file>` | Zips a file. |
| `unzip <file.zip>` | Extracts a zip file. |

## Miscellaneous
| Command | Description |
|--------|-------------|
| `history` | Shows command history. |
| `alias ll='ls -alF'` | Creates an alias for a command. |
| `crontab -e` | Edits scheduled tasks (cron jobs). |
| `man <command>` | Shows the manual for a command. |
| `clear` | Clears the terminal screen. |
| `exit` | Exits the terminal or current shell. |