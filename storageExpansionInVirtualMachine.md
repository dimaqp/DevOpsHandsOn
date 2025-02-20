# Expanding Disk Storage in Ubuntu Virtual Machine

This README outlines the steps to expand the disk storage of an Ubuntu Virtual Machine after increasing the virtual hard disk size from 12GB to 50GB in a Hyper-V environment.

## Table of Contents

- [Overview](#overview)
- [Step 1: Verify Disk Size Increase](#step-1-verify-disk-size-increase)
- [Step 2: Resize the Partition](#step-2-resize-the-partition)
    - [Option 1: Using growpart (Recommended)](#option-1-using-growpart-recommended)
    - [Option 2: Using fdisk (Manual Method)](#option-2-using-fdisk-manual-method)
- [Step 3: Resize the Filesystem](#step-3-resize-the-filesystem)
    - [For ext4 Filesystem](#for-ext4-filesystem)
    - [For XFS Filesystem (CentOS/RHEL 7+)](#for-xfs-filesystem-centosrhel-7)
- [Additional Cleanup Steps](#additional-cleanup-steps)

---

## Overview

After increasing the disk size in Hyper-V, the operating system might not automatically update the partition size. This guide will help you verify the disk increase, resize the partition, and extend the filesystem accordingly.

---

## Step 1: Verify Disk Size Increase

After increasing the disk size in Hyper-V, check if the OS recognizes the new size. If `/dev/sda` shows 50GB but `/dev/sda1` (the partition) still shows 12GB, proceed with resizing.

---

## Step 2: Resize the Partition

### Option 1: Using growpart (Recommended)

1. Run the command:
     ```
     sudo growpart /dev/sda 1
     ```
2. Verify the new partition layout:
     ```
     lsblk
     ```

### Option 2: Using fdisk (Manual Method)

1. Open fdisk:
     ```
     sudo fdisk /dev/sda
     ```
2. Delete the existing partition:
     - Press `d` (the data remains if the partition is recreated properly).
3. Create a new partition:
     - Press `n` to create a new partition.
     - Select the primary partition type.
     - Use the same start sector as before.
     - Press Enter to use the full disk size.
4. Write the changes and exit:
     - Press `w`.
5. Reboot the VM to apply changes:
     ```
     sudo reboot
     ```

---

## Step 3: Resize the Filesystem

After resizing the partition, extend the filesystem to use the new space.

### For ext4 Filesystem

```
sudo resize2fs /dev/sda1
```

### For XFS Filesystem (CentOS/RHEL 7+)

*(Use the appropriate command, for example:)*

```
sudo xfs_growfs /
```

Verify the changes:
```
df -h /
```
and
```
lsblk
```
You should now see the full 50GB available for the root partition.

---

## Additional Cleanup Steps

If you still receive disk space warnings, consider removing unnecessary files.

### Remove Unnecessary Files

- **Find large files:**
    ```
    sudo du -ahx / | sort -rh | head -20
    ```

- **Clean APT Cache:**
    ```
    sudo apt-get autoremove
    sudo apt-get clean
    ```

- **Vacuum Journal Logs:**
    ```
    sudo journalctl --vacuum-size=500M
    ```

- **Clear Docker (if installed):**
    ```
    docker system prune -a
    ```

---

Your Ubuntu VM should now properly reflect 50GB of storage!
