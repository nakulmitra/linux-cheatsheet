# Linux Terminal Tips & Tricks

| **Case** | **Command / Shortcut** | **Description** |
|----------|------------------------|------------------|
| **Tab for autocompletion** | `Tab` (once or twice) | Auto-completes commands, file paths, and directory names |
| **Switch to last working directory** | `cd -` | Switches to the **previous** directory you were in |
| **Run multiple commands in one line** | `command1; command2` <br> `command1 && command2` | `;` runs all sequentially <br> `&&` runs second only if first succeeds |
| **Read big/large files** | `less filename` <br> `more filename` | Efficiently view large files without loading the entire content into memory |
| **Empty a file without deleting it** | `> filename` <br> `: > filename` <br> `truncate -s 0 filename` | Truncates the file content but keeps the file |
| **Live monitoring of a file** | `tail -f filename` <br> `tail -f /var/log/syslog` | Shows new lines added to a file (great for logs) |
| **Record all terminal commands** | `script session.log` -> [do your work] -> `exit` | Records all terminal input/output to `session.log` |
| **Use calculator in Linux** | `bc` | Opens an interactive command-line calculator (`quit` to exit) |
| **Move cursor to start/end of command** | `Ctrl + A` -> Move to start <br> `Ctrl + E` -> Move to end | Useful in editing long commands |
| **Clear terminal / redo** | `clear` or `Ctrl + L` | Clears the terminal screen |
| **Reverse search command history** | `Ctrl + R` and type part of command | Incremental search through command history |
| **Clear screen (shortcut)** | `Ctrl + L` | Clears the terminal view (same as `clear`) |
| **Delete one character from beginning** | `Ctrl + D` | Deletes the character under the cursor (like `Del`) |
| **Switch to home directory** | `cd ~` <br> or just `cd` | Takes you back to your home directory |
| **History command** | `history` | Shows previously executed commands with line numbers |