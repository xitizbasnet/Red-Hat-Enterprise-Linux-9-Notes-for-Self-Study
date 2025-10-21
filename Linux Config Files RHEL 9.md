# 📁 Linux Config Files  — `/etc/fstab`

## 🧾 Sample Entries

```fstab
# This file is edited by fstab-sync - see 'man fstab-sync' for details

/dev/VolGroup00/LogVol00   /               ext3    defaults        1 1
LABEL=/boot                /boot           ext3    defaults        1 2
tmpfs                      /dev/shm        tmpfs   defaults        0 0
devpts                     /dev/pts        devpts  gid=5,mode=620  0 0
sysfs                      /sys            sysfs   defaults        0 0
proc                       /proc           proc    defaults        0 0
/dev/VolGroup00/LogVol01   swap            swap    defaults        0 0
/mnt/ISO/SUSE10-x64.iso    /media/SUSE10-cdrom iso9660 defaults,loop,ro 0 0
```

---

## 📌 Field Descriptions

| Field | Description |
|-------|-------------|
| 1 | Disk volume label (e.g., `LABEL=/home`) or device name (e.g., `/dev/hda5`) |
| 2 | Mountpoint |
| 3 | Filesystem type |
| 4 | Mount options (e.g., `rw`, `ro`, `exec`, `defaults`) |
| 5 | Dump backup flag (`0` = no, `1` = yes) |
| 6 | fsck scan priority (`0` = no scan, `1+` = scan with priority) |

---

