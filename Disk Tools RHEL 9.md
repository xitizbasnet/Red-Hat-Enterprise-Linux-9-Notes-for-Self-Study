# 💽 Disk Tools RHEL 9

## 🧰 Partitioning Tools Overview

| Tool | Description |
|------|-------------|
| `fdisk`, `sfdisk`, `cfdisk` | Legacy disk tools for BIOS systems (`sfdisk` is script-friendly) |
| `gdisk`, `sgdisk`, `cgdisk` | Disk tools for UEFI/GPT systems (`sgdisk` is script-friendly) |
| `parted` | Advanced disk tool with filesystem options |

---

## 🧭 Partitioning Commands Comparison

| Function | `fdisk` | `gdisk` | `parted` |
|----------|---------|---------|----------|
| Help menu | `m` | `?` | `help` |
| Print partitions | `p` | `p` | `print` |
| Create partition | `n` | `n` | `mkpart TYPE START END` |
| Create partition with FS | — | — | `mkpartfs TYPE FS-TYPE START END` |
| Make FS on partition | — | — | `mkfs NUMBER FS-TYPE` |
| Show detailed info | — | `i` | `print all` |
| Delete partition | `d` | `d` | `rm <number>` |
| List partition types | `l` | `l` | — |
| Change partition type | `t` | `t` | — |
| Expert menu | `x` | `x` | — |
| Transpose partitions | — | `x t` | `move NUMBER START END` |
| Resize partition | — | `x S` | `resize NUMBER START END` |
| Replicate partition table | — | `xu` | — |
| Verify disk | `v` | `v` | — |
| Write table to disk | `w` | `w` | — |
| Quit | `q` | `q` | `quit` |

---

## 🛠️ Other Disk Utilities

| Tool | Description |
|------|-------------|
| `lsblk` | List block devices in tree format |
| `blkid` | List block devices with UUID and filesystem type |
| `partprobe` | Force kernel to re-probe the disks |
| `fixparts`, `testdisk` | Fix and restore partitions and files |
| `wipefs`, `shred` | Erase disk or securely delete files |
| `mkfs`, `mke2fs` | Create filesystem on partition (format) |
| `tune2fs` | Modify filesystem options |
| `fsck` | Check filesystem integrity |
| `mkswap` | Create swap partitions |
| `dd`, `ddrescue`, `dd-rescue` | Duplicate disks or recover data |

---

 
