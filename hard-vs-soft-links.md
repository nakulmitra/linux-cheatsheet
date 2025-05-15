# Hard Link vs Soft Link in Linux

In Linux, **links** are a way to reference files using different names or paths. There are two types of links:

* **Hard Links**
* **Soft Links (Symbolic Links)**

## What is a Hard Link?

A **hard link** is a **direct reference** to the same inode (data) on disk. It behaves like the original file and remains valid even if the original file is deleted.

### Features of Hard Links:

* Points to the same inode (same file data).
* Cannot link to directories (to prevent loops).
* Only works within the same filesystem.
* If original file is deleted, the link still works.

### Create a Hard Link:

```bash
ln original.txt hardlink.txt
```

### Verify:

```bash
ls -li original.txt hardlink.txt
```

Check that both have the **same inode number**.

## What is a Soft Link (Symbolic Link)?

A **soft link**, or **symlink**, is a **pointer to the original file's name/path**. It is like a shortcut.

### Features of Soft Links:

* Points to the file name, not the inode.
* Can link to directories and files.
* Can cross file systems.
* Breaks if the original file is deleted (dangling symlink).

### Create a Soft Link:

```bash
ln -s original.txt softlink.txt
```

### Verify:

```bash
ls -l softlink.txt
```

You'll see it pointing to the original:

```
softlink.txt -> original.txt
```

## Key Differences

| Feature              | Hard Link              | Soft Link (Symlink)   |
| -------------------- | ---------------------- | --------------------- |
| Points To            | Inode (actual data)    | File name/path        |
| Cross File System    | No                   | Yes                 |
| Links to Directories | Not allowed (mostly) | Yes                 |
| Survives Deletion    | Yes (file remains)   | No (becomes broken) |
| Inode Number         | Same as original       | Different             |
| Command              | `ln file link`         | `ln -s file link`     |

## Example in Practice

```bash
echo "Hello World" > original.txt
ln original.txt hardlink.txt
ln -s original.txt softlink.txt

rm original.txt

cat hardlink.txt      # Works
cat softlink.txt      # Fails (broken symlink)
```

## Useful Commands

* View all links:

```bash
find . -type l       # List all symlinks
```

* Check symlink target:

```bash
readlink softlink.txt
```