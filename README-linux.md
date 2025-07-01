# Linux helper MD

## Table of Contents

- [SD & OS](#sd--os)
- [Terminal Command References](#terminal-command-references)

## SD & OS

1. Insert the SD card to the computer and run a terminal session.
2. If the SD card doesn't automatically mount follow the next steps:
   - 2a. In the terminal run [`lsblk`](#lsblk-ref), and identify your SD in the list.
   - 2b. Create a directory to mount the SD on using [`sudo mkdir -p /mnt/sdcard`](#mkdir-ref).
   - 2c. Mount the SD card to the directory using [`sudo mount /dev/PARTITION_NAME /mnt/sdcard`](#mount-ref). (Replace 'PARTITION_NAME' with the SD's actual partition name).
3. To wipe the SD card, first unmount the SD card using [`sudo umount /mnt/sdcard`](#unmount-ref), and follow the next steps:
   - 3a. Wipe the SD card using [`sudo dd if=/dev/zero of=/dev/PARTITION_NAME bs=4M status=progress`](#wipe-ref). (Replace 'PARTITION_NAME' with the SD's actual partition name from).
   - 3b. Create a new partition table using [`sudo fdisk /dev/sda`](#fdisk-ref)

## Terminal Command References

<a name="lsblk-ref"></a>

```bash
lsblk
# Lists all block devices in a tree format
# Helps identify your SD card device name (e.g., sdb, sdc)
```

<a name="mkdir-ref"></a>

```bash
sudo mkdir -p /mnt/sdcard
# Creates a mount point directory for the SD card
# -p flag creates parent directories if they don't exist
```

<a name="mount-ref"></a>

```bash
sudo mount /dev/PARTITION_NAME /mnt/sdcard
# Mounts the SD card partition to the specified directory
# Replace PARTITION_NAME with actual partition (e.g., sdb1)
```

<a name="unmount-ref"></a>

```bash
sudo umount /mnt/sdcard
# Unmounts the SD card from the mount point
```

<a name="wipe-ref"></a>

```bash
sudo dd if=/dev/zero of=/dev/PARTITION_NAME bs=4M status=progress
# WARNING: This will completely wipe the SD card!
# Replace PARTITION_NAME with actual device (e.g., sdb)
```

<a name="fdisk-ref"></a>

```bash
sudo fdisk /dev/PARTITION_NAME
# Opens fdisk utility to manage partitions
# Replace PARTITION_NAME with actual device (e.g., sdb)
```
