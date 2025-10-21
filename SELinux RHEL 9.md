# 🔐 SELinux RHEL 9

## 📦 RPM Packages

| Package | Purpose |
|--------|---------|
| `setroubleshoot` | Provides `setroubleshootd` and `sealert` |
| `policycoreutils-gui` | GUI tool: `system-config-selinux` |
| `setools` | Includes `seaudit` and `apol` |
| `policycoreutils-python` | Contains policy creation scripts |

---

## 📁 Key Files & Services

| Command/File | Purpose |
|--------------|---------|
| `/etc/sysconfig/selinux` | SELinux config file |
| `/etc/selinux` | Policy storage location |
| `setroubleshootd` | Translates AVC denial messages |
| `/var/log/audit/audit.log` | Log of all SELinux messages |
| `/var/log/messages` | Denial logs if `setroubleshootd` is active |
| `sealert -a audit.log -H > file.html` | Converts audit log to HTML report |

---

## ⚙️ SELinux Status & Info

| Command | Purpose |
|--------|---------|
| `setenforce` | Change SELinux mode (Enforcing/Permissive) |
| `sestatus` | Show current SELinux status |
| `seinfo -c` | List object classes |
| `seinfo -t` | List object types |
| `seinfo -u` | List SELinux users |
| `seinfo -n` | List network contexts |
| `seinfo -p` | List network port contexts |
| `seinfo -b` | List Booleans |
| `getsebool -a` | Show all Booleans and their values |
| `setsebool <boolean> <on|off>` | Set Boolean (use `-P` for persistence) |
| `restorecon <file>` | Restore default security context |

---

## 🧪 Context & Policy Management

| Command | Purpose |
|--------|---------|
| `chcon -t <context_t> <file>` | Set file context manually |
| `ls -Z <file>` | Show file security context |
| `ps -AZ` | Show process security contexts |
| `id -Z` | Show user security context |
| `system-config-selinux` | GUI policy management |
| `semanage` | CLI policy management |
| `checkpolicy` | Compile policy to binary |
| `audit2allow` | Generate policy modules from audit logs |
| `semodule -i <policy module>` | Insert policy module |

---

## 🧪 Example: Create & Apply Policy Module

```bash
grep http audit.log | audit2allow -m local && semodule -i local.pp
```

---

 
