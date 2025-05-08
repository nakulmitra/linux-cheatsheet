# File Permission & Ownership
In Linux, every file and directory is associated with a set of permissions that control **who can read, write, or execute** the content. This ensures system security by restricting unauthorized access or modification.

Permissions are defined for **three categories of users**:

* **Owner (User):** The creator or assigned user of the file
* **Group:** A set of users with shared access
* **Others:** Everyone else on the system

Each category can have the following permissions:

* `r` (read): View file contents or list directory contents
* `w` (write): Modify file contents or add/remove items in a directory
* `x` (execute): Run files (if executable) or access directories

Permissions can be viewed using `ls -l` and are represented as:

```
-rwxr-xr--  (Owner: rwx | Group: r-x | Others: r--)
```

To modify access, Linux provides powerful commands like:

* `chmod` - Change permission levels
* `chown` - Change file ownership
* `chgrp` - Change group ownership

Understanding and managing these permissions is essential for:

* Securing files and scripts
* Setting correct access for collaborative environments
* Preventing accidental modification or execution

## Linux File Permissions & Access Control

### 1. **How to Check and Understand "Permission Denied" Issues**

| Command                  | Description                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------- |
| `ls -l filename`         | Check permissions on a file                                                                  |
| `ls -ld directoryname`   | Check permissions of a directory                                                             |
| `whoami`                 | Shows the current user                                                                       |
| `groups`                 | Lists groups the current user belongs to                                                     |
| `namei -l /path/to/file` | Breaks down the permission chain of a path - useful for debugging "Permission denied" errors |

**Tip:** If you see `Permission denied`, verify:

* Do you have read/execute rights?
* Is the file owned by you or your group?
* Is the parent directory accessible?

### 2. **How to Check File and Folder Permissions**

```bash
ls -l              # Lists permissions for all files/folders in current directory
ls -ld foldername  # Lists permissions of the folder itself
stat filename      # Shows detailed metadata, including permissions
```

**Example Output:**

```
-rw-r--r-- 1 user group 1234 Apr 28  file.txt
```

* `-` = file, `d` = directory
* `rw-` = owner permissions
* `r--` = group permissions
* `r--` = others (world) permissions

### 3. **Types of Permissions in Linux**

| Symbol | Type    | Description                                        |
| ------ | ------- | -------------------------------------------------- |
| `r`    | Read    | View file contents or list directory               |
| `w`    | Write   | Modify file contents or create/delete in directory |
| `x`    | Execute | Run file as program or enter directory             |

### 4. **Scope of Users and Permissions**

Permissions are applied across **three categories**:

| Scope    | Description                     |
| -------- | ------------------------------- |
| `Owner`  | The user who owns the file      |
| `Group`  | Users who are in the same group |
| `Others` | All other users                 |

**Example:**

```
-rwxr-xr-- 1 user group 100 Apr 28 file.sh
```

* **Owner (user):** `rwx` -> full access
* **Group:** `r-x` -> read & execute
* **Others:** `r--` -> read only

### 5. **Change Permissions Using `chmod`**

#### Numeric (Octal) Method

| Permission | Octal |
| ---------- | ----- |
| `r`        | 4     |
| `w`        | 2     |
| `x`        | 1     |
| `-`        | 0     |

**Command Example:**

```bash
chmod 755 filename
```

This means:

* `7` -> `rwx` (owner)
* `5` -> `r-x` (group)
* `5` -> `r-x` (others)

#### Symbolic Method

```bash
chmod u+x filename    # Add execute for user
chmod g-w filename    # Remove write from group
chmod o=r filename    # Set others to read-only
chmod a+x script.sh   # Add execute to all (user, group, others)
```

### 6. **Add / Remove Permissions**

| Task                              | Command               |
| --------------------------------- | --------------------- |
| Add execute for user              | `chmod u+x file.sh`   |
| Remove read for others            | `chmod o-r file.txt`  |
| Add read/write for group          | `chmod g+rw file.txt` |
| Remove all permissions for others | `chmod o= file.txt`   |
| Make script executable by all     | `chmod a+x script.sh` |

## Ownership Management in Linux: `chown` and `chgrp`

### `chown` - Change Ownership

Used to **change the owner** of a file or directory (and optionally its group).

#### Syntax:

```bash
chown [OPTIONS] USER[:GROUP] file
```

#### Examples:

| Use Case                                                 | Command                       | Description                                               |
| -------------------------------------------------------- | ----------------------------- | --------------------------------------------------------- |
| Change owner                                             | `chown alice file.txt`        | `file.txt` is now owned by `alice`                        |
| Change owner and group                                   | `chown alice:devs file.txt`   | Owner → `alice`, Group → `devs`                           |
| Recursive ownership change                               | `chown -R bob:staff /opt/app` | Changes ownership for all files in `/opt/app` recursively |
| Only change owner, leave group unchanged                 | `chown alice: file.txt`       | Leaves group as-is                                        |
| Change ownership of symlink target (not the link itself) | `chown -h user file_symlink`  | Modifies symlink target ownership                         |

### `chgrp` - Change Group Ownership

Used to **change only the group** associated with a file or directory.

#### Syntax:

```bash
chgrp [OPTIONS] GROUP file
```

#### Examples:

| Use Case                       | Command                        | Description                                             |
| ------------------------------ | ------------------------------ | ------------------------------------------------------- |
| Change group                   | `chgrp devs file.txt`          | `file.txt` now belongs to group `devs`                  |
| Change group recursively       | `chgrp -R devs /var/www`       | All files under `/var/www` are assigned to `devs` group |
| Change group of multiple files | `chgrp qa file1.txt file2.txt` | Assigns `qa` group to both files                        |

### Tips:

* You must be **root** or have appropriate privileges to change ownership with `chown`.
* Use `ls -l` to verify changes in ownership and group.
* `chmod` controls **access**, while `chown` and `chgrp` control **who has access**.