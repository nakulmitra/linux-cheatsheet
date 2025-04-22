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