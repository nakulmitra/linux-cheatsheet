# Wildcards in Linux

**Wildcards** are special characters used in Linux to **match filenames or strings**. They are incredibly useful when working with file operations such as `ls`, `cp`, `mv`, `rm`, `find`, etc.

Wildcards simplify operations by allowing pattern matching, especially when you’re dealing with multiple files.

## Types of Wildcards

| Wildcard             | Description                                             |
| -------------------- | ------------------------------------------------------- |
| `*`                  | Matches **zero or more characters**                     |
| `?`                  | Matches **exactly one character**                       |
| `[abc]`              | Matches **one character from the set** `a`, `b`, or `c` |
| `[a-z]`              | Matches **one character in the specified range**        |
| `[!abc]` or `[^abc]` | Matches **any character except** `a`, `b`, or `c`       |

## Common Use Cases & Examples

### 1. `*` — Match Zero or More Characters

```bash
ls *.txt
```

* Matches all files ending in `.txt`

```bash
rm file*
```

* Deletes files starting with `file`

### 2. `?` - Match Exactly One Character

```bash
ls file?.txt
```

* Matches `file1.txt`, `fileA.txt`, but not `file12.txt`

### 3. `[abc]` - Match a Specific Set of Characters

```bash
ls file[123].txt
```

* Matches `file1.txt`, `file2.txt`, or `file3.txt`

### 4. `[a-z]` - Match a Range of Characters

```bash
ls file[a-c].txt
```

* Matches `filea.txt`, `fileb.txt`, `filec.txt`

### 5. `[!abc]` or `[^abc]` - Negated Character Set

```bash
ls file[!0-9].txt
```

* Matches `filea.txt`, `fileX.txt`, but **not** `file1.txt`, `file2.txt`

## Using Wildcards with Common Commands

### `ls`

```bash
ls *.sh      # Lists all shell scripts
```

### `cp`

```bash
cp *.jpg /backup/images/
```

### `mv`

```bash
mv report_202?.pdf archive/
```

### `rm`

```bash
rm *.log
```

### `find`

```bash
find . -name "*.conf"
```

> Note: Wildcards used with `find` must be quoted to prevent shell expansion.


## `{}` in Brace Expansion (NOT a Wildcard)

The `{}` syntax is used to **generate multiple text strings** or **filenames** in a compact form.

### Examples:

```bash
echo file{1,2,3}.txt
```

**Output:**

```
file1.txt file2.txt file3.txt
```

```bash
mkdir project_{frontend,backend,db}
```

**Creates directories:**

```
project_frontend/
project_backend/
project_db/
```

```bash
cp file{A,B}.txt /backup/
```

**Expands to:**

```bash
cp fileA.txt /backup/
cp fileB.txt /backup/
```

## Comparison: Wildcard vs Brace Expansion

| Feature   | Wildcard (`*`, `?`, `[]`)          | Brace Expansion (`{}`)                 |
| --------- | ---------------------------------- | -------------------------------------- |
| Purpose   | Pattern matching                   | Explicit enumeration                   |
| When Used | Matches existing files             | Generates strings before execution     |
| Example   | `file*.txt` -> file1.txt, file2.txt | `file{1,2}.txt` -> file1.txt, file2.txt |

## Important Notes

* **Brace expansion happens before wildcard expansion.**
* It does **not check if files exist**; it just creates the combinations.

### Example:

```bash
touch file{1..3}.txt
```

Creates:

```
file1.txt file2.txt file3.txt
```

## Tips and Gotchas

* Always use `echo` or `ls` before using `rm` with wildcards to prevent accidental deletions.
* Wildcards are expanded by the **shell** before the command is executed.
* For more advanced matching, use **globbing** with `shopt` or use **regular expressions**.

## Bonus: Enable Extended Globbing (Bash)

```bash
shopt -s extglob
ls !(*.txt)   # List files NOT ending in .txt
```