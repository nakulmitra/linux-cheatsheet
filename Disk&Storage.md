# Disk Space Monitoring & Disk Management Commands in Linux

Monitoring and managing disk usage is essential for keeping a Linux system healthy, organized, and performing well. Below are essential commands used to check disk usage, analyze space consumption, and manage disks and filesystems.

## 1. `df` - Disk Filesystem Usage

`df` (disk free) reports the **amount of disk space used and available** on file systems.

### Basic Usage:

```bash
df
```

### Common Options:

| Option    | Description                                            |
| --------- | ------------------------------------------------------ |
| `-h`      | Human-readable (shows sizes in KB, MB, GB)             |
| `-T`      | Show filesystem type                                   |
| `-a`      | Include pseudo, duplicate, or inaccessible filesystems |
| `--total` | Display a grand total                                  |
| `-x`      | Exclude specific file systems                          |
| `-i`      | Show inode usage (not just disk space)                 |

### Examples:

```bash
df -h              # Show disk usage in human-readable format
df -hT             # Include filesystem type with human-readable sizes
df -i              # Show inode usage
df --total         # Display total disk usage summary
```

## 2. `du` - Disk Usage by File/Directory

`du` (disk usage) estimates **file and directory space usage**.

### Basic Usage:

```bash
du /path/to/dir
```

### Common Options:

| Option          | Description                                   |
| --------------- | --------------------------------------------- |
| `-h`            | Human-readable                                |
| `-s`            | Summary only (total size of a directory)      |
| `-a`            | Show size of all files, not just directories  |
| `-c`            | Display total                                 |
| `--max-depth=N` | Limit directory depth (e.g., `--max-depth=1`) |

### Examples:

```bash
du -h /home/user           # Show usage of /home/user in human-readable format
du -sh /var/log            # Show total size of /var/log only
du -h --max-depth=1 /etc   # Show usage of each folder under /etc, depth 1
du -ah                     # Show sizes of all files and subfolders
```

## 3. `free` - Memory and Swap Usage

`free` displays **system memory usage**, including RAM and swap space.

### Basic Usage:

```bash
free
```

### Common Options:

| Option | Description                                  |
| ------ | -------------------------------------------- |
| `-h`   | Human-readable                               |
| `-m`   | Show in megabytes                            |
| `-g`   | Show in gigabytes                            |
| `-t`   | Show totals                                  |
| `-s N` | Refresh every `N` seconds (e.g., `-s 2`)     |
| `--si` | Use powers of 1000 instead of 1024 for units |

### Examples:

```bash
free -h         # Human-readable memory summary
free -m         # Show memory in MB
free -g         # Show memory in GB
free -t         # Include total memory line
free -s 2       # Refresh every 2 seconds (live monitoring)
```

## 4. `mount` - Mount a Filesystem

`mount` attaches a storage device (partition or disk) to the Linux filesystem.

### Basic Syntax:

```bash
mount <device> <mount_point>
```

### Example:

```bash
mount /dev/sdb1 /mnt/usb
```

> To list currently mounted filesystems:

```bash
mount | column -t
```

## 5. `umount` - Unmount a Filesystem

`umount` detaches a mounted filesystem.

### Example:

```bash
umount /mnt/usb
```

> If the device is busy:

```bash
lsof +f -- /mnt/usb   # Find what's using it
```

## 6. `lsblk` - List Block Devices

`lsblk` displays information about **block devices** (disks, partitions).

### Example:

```bash
lsblk -f     # Show filesystem type, label, and UUID
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT
```

> Useful to visualize disk layout and mount points.

## 7. `fdisk -l` - Partition Table Viewer

`fdisk -l` lists **all available disks and partitions**, their sizes, and filesystem types.

### Example:

```bash
sudo fdisk -l
```

> This is useful for inspecting newly attached disks or troubleshooting boot/partition issues.

## Summary Table

| Command    | Purpose                              | Use Case                         |
| ---------- | ------------------------------------ | -------------------------------- |
| `df`       | Disk usage of mounted filesystems    | Check space used/free per FS     |
| `du`       | Space used by files/directories      | Find space-heavy folders         |
| `free`     | View RAM and swap usage              | Monitor memory usage             |
| `mount`    | Attach storage to the filesystem     | Mount USBs, external drives      |
| `umount`   | Safely detach mounted storage        | Before removing external storage |
| `lsblk`    | Show disks and partition structure   | View layout and mounts           |
| `fdisk -l` | Display partition info for all disks | Disk partition inspection        |