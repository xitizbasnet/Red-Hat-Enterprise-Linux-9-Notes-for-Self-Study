# 📦 Mounting RHEL 9

## 🔍 Device & Mount Info

| Task | Command |
|------|---------|
| Show device messages | `dmesg | less` |
| Show block devices | `lsblk`, `blkid` |
| Show raw block devices | `cat /proc/partitions` |
| Show mounted devices | `df`, `mount` |
| Mount all devices in `/etc/fstab` | `mount -a` |
| Mount device from `/etc/fstab` | `mount <device path>` or `mount <mountpoint path>` |
| Unmount device | `umount <device path>` or `umount <mountpoint path>` |
| Mount with multiple options | `mount -o acl,rw <device path> <mountpoint path>` |
| Find locks on mounted devices | `fuser <mountpoint path>` or `<device path>` |
| Find locks using open files | `lsof | grep <mountpoint>` |

---

## 🔗 Device Path Examples

| Mount Type | Device Path |
|------------|-------------|
| IDE disk | `/dev/hda1` |
| SATA, SCSI, USB, Firewire | `/dev/sda1` |
| CD-ROM writable | `/dev/sr0` |
| Disk by label | `/dev/disk/by-label/root` |
| Disk by UUID | `/dev/disk/by-uuid/bc5fbb9a-5e6e-46a0-9636-452129350168` |
| Disk by ID | `/dev/disk/by-id/dm-name-VolGroup00-LogVol00` |

---

## 📁 Filesystem Mounting

| Filesystem Type | Command |
|------------------|---------|
| Windows FAT32 | `mount -t vfat /dev/sdb /media/disk/` |
| Optical disk (CD/DVD) | `mount -t iso9660 /dev/sr0 /media/cdrom/` |
| Windows network drive | `mount -t cifs //computer/share /mnt/smbshare/` |
| Unix network drive | `mount -t nfs computer:/share /mnt/nfsshare/` |
| Disk file | `mount -o loop diskfile.img /media/diskfile/` |

---

## 🗂️ Filesystem Types

| Category | Supported Types |
|----------|------------------|
| Windows Filesystems | `fat`, `vfat`, `exfat`, `ntfs` |
| Linux Filesystems | `ext2`, `ext3`, `ext4`, `xfs`, `btrfs` |
| Network Filesystems | `cifs`, `nfs`, `gfs2` |

---

## 📄 Example `/etc/fstab`

```fstab
# Device         Mountpoint       Filesystem  Options         Dump  Fsck
/dev/sda1        /                ext4        defaults,acl     1     1
/dev/scd0        /media/cdrom     iso9660     user,exec        0     0
fs:/var/share    /var/share       nfs         defaults         0     0
```

---

