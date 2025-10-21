# 🖧 Samba RHEL 9

## 📦 Installation & Setup

| Function | Command |
|---------|---------|
| Install Samba | `yum install samba samba-client cifs-utils` |
| Edit config file | `vi /etc/samba/smb.conf` |
| Test config syntax | `testparm` |
| Start Samba service | `systemctl start smb` |
| Start NetBIOS service | `systemctl start nmb` |
| Enable Samba on boot | `systemctl enable smb` |

---

## 🔐 SELinux & Firewall

| Function | Command |
|---------|---------|
| Show SELinux Booleans | `getsebool -a | egrep 'samba|smb|cifs'` |
| Enable RW Boolean | `setsebool -P samba_export_all_rw=1` |
| Set SELinux context | `semanage fcontext -at samba_share_t "/share/path(/.*)?"` |
| Open iptables ports (SMB) | `iptables -A INPUT -p udp --match multiport --dports 137,138 -j ACCEPT`<br>`iptables -A INPUT -p tcp --dport 139 -j ACCEPT` |
| Open iptables ports (CIFS) | `iptables -A INPUT -p tcp --dport 445 -j ACCEPT` |
| Open firewalld ports | `firewall-cmd --permanent --add-service samba` |

---

## 👥 User & Share Management

| Function | Command |
|---------|---------|
| Add Samba user | `smbpasswd -a username` |
| List Samba users | `pdbedit -Lv` |
| View share tree | `smbtree` |
| Send print job | `smbprint` |
| Lookup NetBIOS name | `nmblookup servername` |
| Access share | `smbclient //host/share -U username` |
| List shares | `smbclient -NL hostname` |
| Mount share | `mount -t cifs //hostname/sharename /mnt/share` |
| Mount with credentials | `mount -t cifs //hostname/sharename /mnt/share -o username=username,password=secretpassword` |

---

## 📁 Example Share Configurations

### 🔓 Public Share (Browsable, Writable if Logged In)

```ini
[public]
path = /var/public
writable = yes
browsable = yes
public = yes
create mask = 0660
```

### 🔐 Secure Office Share (Accounting Group Only)

```ini
[accounting]
path = /var/accounting
writable = yes
browsable = no
public = no
valid users = @accounting
write list = @accounting
force group = @accounting
directory mode = 0770
```

---

 
