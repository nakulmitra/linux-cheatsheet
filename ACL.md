# What is Linux Access Control List (ACL)?

In traditional Linux file permissions, you can only set access for **one owner**, **one group**, and **others**. But what if you want to give access to **multiple users or groups** with different permission levels? That's where **Access Control Lists (ACLs)** come in.

**ACL** provides **fine-grained permissions** for files and directories, allowing you to assign read/write/execute access to multiple users and groups - beyond the default owner/group/others model.

## Why Use ACL?

* Give a specific user access to a file they don't own.
* Assign different permissions to different users for the same file.
* Avoid changing group ownership of files repeatedly.

## How to Set Permissions Using ACL

### Step 1: Enable ACL (if not already enabled)

For most modern systems, it's enabled by default. If not, you may need to remount the filesystem with `acl` option.

```bash
mount -o remount,acl /mount/point
```

### Step 2: Use `setfacl` command to assign permissions

#### Give read permission to user `ba` on `file.txt`:

```bash
setfacl -m u:ba:r file.txt
```

#### Give read+write permission to group `devs`:

```bash
setfacl -m g:devs:rw file.txt
```

#### Give execute permission to user `testers`:

```bash
setfacl -m u:testers:x file.sh
```

## How to Remove Permissions Using ACL

### Use `setfacl -x` to remove specific ACL entry

#### Remove ACL entry for user `ba`:

```bash
setfacl -x u:ba file.txt
```

#### Remove ACL entry for group `devs`:

```bash
setfacl -x g:devs file.txt
```

### Remove all ACL entries and reset to normal permissions:

```bash
setfacl -b file.txt
```

## Recursive Permissions Using ACL

Apply ACLs recursively to all files and subdirectories:

```bash
setfacl -R -m u:ba:rw /path/to/dir
```

You can also set **default ACLs** for newly created files in a directory:

```bash
setfacl -d -m u:ba:rw /path/to/dir
```

> `-d` sets default ACLs for all future files and folders created inside the directory.

## Check Current ACLs

```bash
getfacl file.txt
```

This will show both traditional and ACL-based permissions.