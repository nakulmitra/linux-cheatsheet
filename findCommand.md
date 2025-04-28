# `find` Command 
The `find` command is used to **search for files and directories** based on conditions like name, size, type, modified time, permissions, etc. It is extremely powerful for managing files.


## Basic Syntax
```
find [starting-point] [options] [expression]
```
If `[starting-point]` is not provided, it defaults to the **current directory** (`.`).

## Common Use Cases for `find`

| Use Case | Command | Description |
|----------|---------|-------------|
| **Find a file by name** | `find /path/to/dir -name "filename"` | Search for a file with exact name |
| **Find a file ignoring case** | `find /path/to/dir -iname "filename"` | Case-insensitive search |
| **Find all files with a specific extension** | `find /path/to/dir -name "*.txt"` | Find all `.txt` files |
| **Find all directories** | `find /path/to/dir -type d` | List all directories |
| **Find all files** | `find /path/to/dir -type f` | List all files |
| **Find empty files** | `find /path/to/dir -type f -empty` | Find all empty files |
| **Find empty directories** | `find /path/to/dir -type d -empty` | Find all empty directories |
| **Find files by size** | `find /path/to/dir -size +100M` | Find files **larger** than 100MB |
| **Find files smaller than a size** | `find /path/to/dir -size -10k` | Find files **smaller** than 10KB |
| **Find files modified in the last N days** | `find /path/to/dir -mtime -7` | Files modified in the last 7 days |
| **Find files accessed in the last N days** | `find /path/to/dir -atime -3` | Files accessed in last 3 days |
| **Find files modified exactly N days ago** | `find /path/to/dir -mtime 2` | Files modified exactly 2 days ago |
| **Find and delete files (careful!)** | `find /path/to/dir -type f -name "*.log" -delete` | Find and delete `.log` files |
| **Find files and execute a command (like `ls`)** | `find /path/to/dir -type f -exec ls -lh {} \;` | List details of found files |
| **Find files and move them** | `find /path/to/dir -type f -name "*.txt" -exec mv {} /path/to/target/ \;` | Move matching files to another directory |
| **Find files by permission** | `find /path/to/dir -perm 644` | Find files with permission 644 |
| **Find broken symbolic links** | `find /path/to/dir -xtype l` | List all broken symlinks |
| **Find multiple patterns** | `find /path/to/dir \( -name "*.txt" -o -name "*.md" \)` | Find files matching **either** `.txt` **or** `.md` |
| **Find files newer than another file** | `find /path/to/dir -newer file.txt` | Find files modified **more recently** than `file.txt` |
| **Find files owned by a user** | `find /path/to/dir -user username` | Find files belonging to a specific user |

## Advanced Examples

| Use Case | Command | Description |
|----------|---------|-------------|
| **Find files modified in the last 1 hour** | `find /path/to/dir -mmin -60` | Files modified in last 60 minutes |
| **Find all `.log` files and compress them** | `find /path/to/dir -name "*.log" -exec gzip {} \;` | Compress found log files |
| **Find files and print only their names** | `find /path/to/dir -type f -printf "%f\n"` | Only show file names (not full paths) |
| **Find and delete files older than 30 days** | `find /path/to/dir -type f -mtime +30 -delete` | Cleanup old files |

## Important Notes
- `{} \;` -> `{}` is a placeholder for the file found; `\;` ends the `-exec` command.
- `-delete` directly deletes files without asking. Be **very careful** — always test with `-print` first.
- For efficiency in mass operations, prefer `+` instead of `\;`:
  ```
  find . -name "*.txt" -exec rm {} +
  ```
  (This batches deletes rather than one-by-one.)