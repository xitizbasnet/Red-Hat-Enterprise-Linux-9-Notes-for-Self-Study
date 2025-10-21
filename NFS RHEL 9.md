# 📡 NFS RHEL 9

## 📦 Installation & Services

| Command | Purpose |
|---------|---------|
| `yum install nfs-utils` | Install NFS server and utilities |
| `service nfs start` | Start NFS service |
| `service portmap start` | Start Portmap service |
| `/etc/exports` | Main NFS configuration file |
| `nfsstat` | Show NFS server status |
| `exportfs` | Export shares from `/etc/exports` |
| `mount -t nfs` | Mount NFS shares |
| `umount` | Unmount NFS shares |
| `showmount -e` | Show all exported shares |
| `showmount -a` | Show all exports mounted by clients |
| `rpcinfo -p` | Show RPC ports |

---

## 📁 Example `/etc/exports`

```exports
/var/share
bob.example.com(rw,no_root_squash)
*(rw,root_squash)
192.168.2.101(ro)

/var/www
192.168.2.100(ro,nosuid,noexec,all_squash)
```

### 🔍 Export Options

| Option | Description |
|--------|-------------|
| `bob.example.com` | Hostname or IP of allowed clients (`*` for all) |
| `rw` / `ro` | Read/write or read-only access |
| `root_squash` / `all_squash` | Map root/all users to `nobody` |
| `no_root_squash` | Allow root access |
| `nosuid` / `noexec` | Disable SUID binaries / executable files |

---

## 🖥️ NFS Client Mount Options

```bash
mount -t nfs -o rsize=4096,wsize=4096,nfsvers=3,soft,tcp 192.168.2.100:/var/share
```

| Option | Description |
|--------|-------------|
| `rsize=n`, `wsize=n` | Read/write block size |
| `nfsvers=n` | NFS version (2 or 3) |
| `nfs4` | Use NFS version 4 |
| `soft` | Allow process to terminate if share is offline |
| `hard` | Lock process and wait if share is offline |
| `tcp` / `udp` | Transport protocol (`udp` is default) |

---

 
