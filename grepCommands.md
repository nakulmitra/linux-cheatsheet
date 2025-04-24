# `grep` Command Cheat Sheet
`grep` (Global Regular Expression Print) is used to search for specific patterns (strings, regex) within files or output.

## Basic Syntax
```
grep [options] pattern [file...]
```

## Commonly Used Grep Commands

| Command | Description |
|---------|-------------|
| `grep "text" file.txt` | Search for **"text"** in `file.txt` |
| `grep -i "text" file.txt` | Case-insensitive search |
| `grep -r "text" /path/to/dir` | Recursively search in all files inside a directory |
| `grep -v "text" file.txt` | Show lines **not** matching the pattern |
| `grep -n "text" file.txt` | Show line numbers with matches |
| `grep -c "text" file.txt` | Count number of matching lines |
| `grep -l "text" *.log` | Show only filenames that contain the match |
| `grep -L "text" *.log` | Show files **not** containing the match |
| `grep -w "word" file.txt` | Match **whole word** only |
| `grep -o "pattern" file.txt` | Print only the matched parts |
| `grep --color=always "text" file.txt` | Highlight matched text in color |

## Grep with Regular Expressions

| Command | Description |
|---------|-------------|
| `grep "^abc" file.txt` | Match lines starting with **abc** |
| `grep "xyz$" file.txt` | Match lines ending with **xyz** |
| `grep "[0-9]" file.txt` | Match lines containing any digit |
| `grep "a.*z" file.txt` | Match anything starting with "a" and ending with "z" (greedy) |
| `grep -E "one|two" file.txt` | Match lines with either **one** or **two** (`-E` enables extended regex) |
| `grep -E "[a-z]{3}" file.txt` | Match lowercase letters of exactly 3 characters |

## Piping and Grep

| Command | Description |
|---------|-------------|
| `ps aux | grep java` | Find running Java processes |
| `dmesg | grep -i error` | Find error messages from kernel logs |
| `cat access.log | grep "404"` | Search for 404 status codes in access logs |
| `ls -l | grep "^d"` | List only directories (lines starting with 'd') |

## Multiple Files and Directories

| Command | Description |
|---------|-------------|
| `grep "text" file1 file2` | Search "text" in multiple files |
| `grep "pattern" *.txt` | Search pattern in all `.txt` files |
| `grep -r "pattern" .` | Search recursively from current directory |

## Grep in Scripts or Silent Checks

| Command | Description |
|---------|-------------|
| `grep -q "pattern" file && echo "Found"` | Silent mode (no output), useful in scripts |
| `grep -e "pattern1" -e "pattern2"` | Match multiple patterns |