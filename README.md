# File and Directory Commands
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

# File Content Commands
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

# File Permission & Ownership
| Command | Description |
|--------|-------------|
| `chmod +x <file>` | Adds execute permission to a file. |
| `chmod 755 <file>` | Sets permission using numeric mode. |
| `chown <user>:<group> <file>` | Changes file owner and group. |
| `ls -l` | Shows detailed file permissions. |

# Process Management
| Command | Description |
|--------|-------------|
| `ps` | Lists running processes. Use `ps aux` for detailed info. |
| `top` | Interactive process viewer (press `q` to quit). |
| `htop` | Enhanced version of `top` (needs installation). |
| `kill <PID>` | Kills a process by ID. |
| `kill -9 <PID>` | Force kills a process. |
| `pkill <name>` | Kills processes by name. |
| `nice`, `renice` | Starts/changes process priority. |

# User Management
| Command | Description |
|--------|-------------|
| `whoami` | Displays current user. |
| `id` | Shows user ID and group ID. |
| `adduser <user>` | Adds a new user. |
| `passwd <user>` | Changes user password. |
| `su <user>` | Switches to another user. |
| `sudo <command>` | Runs a command as root/superuser. |

# Disk & Storage
| Command | Description |
|--------|-------------|
| `df -h` | Shows disk space usage in human-readable format. |
| `du -sh <dir>` | Shows size of a directory. |
| `mount` | Lists or mounts a file system. |
| `umount` | Unmounts a mounted file system. |
| `lsblk` | Lists block devices (like hard drives). |
| `fdisk -l` | Shows partition table (needs sudo). |

# Networking
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

# System Information
| Command | Description |
|--------|-------------|
| `uname -a` | Shows system information. |
| `uptime` | Shows system uptime. |
| `free -h` | Displays memory usage. |
| `top` / `htop` | Displays resource usage. |
| `hostname` | Displays system hostname. |
| `dmesg` | Shows boot and kernel messages. |

# Package Management (Debian-based systems like Ubuntu)
| Command | Description |
|--------|-------------|
| `apt update` | Updates package list. |
| `apt upgrade` | Installs available updates. |
| `apt install <package>` | Installs a package. |
| `apt remove <package>` | Removes a package. |
| `dpkg -i <package>.deb` | Installs a `.deb` package manually. |

# Package Management (RHEL/CentOS)
| Command | Description |
|--------|-------------|
| `yum install <package>` | Installs a package. |
| `yum remove <package>` | Removes a package. |
| `yum update` | Updates all packages. |

# Archive & Compression
| Command | Description |
|--------|-------------|
| `tar -cvf file.tar <dir>` | Creates a tar archive. |
| `tar -xvf file.tar` | Extracts a tar archive. |
| `tar -czvf file.tar.gz <dir>` | Creates a gzipped tarball. |
| `gzip <file>` | Compresses a file. |
| `gunzip <file.gz>` | Decompresses a `.gz` file. |
| `zip <file.zip> <file>` | Zips a file. |
| `unzip <file.zip>` | Extracts a zip file. |

# Miscellaneous
| Command | Description |
|--------|-------------|
| `history` | Shows command history. |
| `alias ll='ls -alF'` | Creates an alias for a command. |
| `crontab -e` | Edits scheduled tasks (cron jobs). |
| `man <command>` | Shows the manual for a command. |
| `clear` | Clears the terminal screen. |
| `exit` | Exits the terminal or current shell. |