# 🌐 Apache RHEL 9

## 📦 Installation

| Task | Command |
|------|---------|
| Install Apache | `yum groupinstall "Web Server"` |
| Install MariaDB | `yum install mariadb-server mariadb` |

---

## ⚙️ Service Management

| Task | Command |
|------|---------|
| Start Apache | `systemctl start httpd` |
| Enable Apache on boot | `systemctl enable httpd` |
| Start MariaDB | `systemctl start mariadb` |
| Enable MariaDB on boot | `systemctl enable mariadb` |

---

## 🧾 Configuration Files

| Item | Path |
|------|------|
| Main config file | `/etc/httpd/conf/httpd.conf` |
| Module & virtual host configs | `/etc/httpd/conf.d/` |
| Remove welcome page | `vi /etc/httpd/conf.d/welcome.conf` |
| Document root | `/var/www/html/` |
| Logs | `/var/log/httpd/` |

---

## 🔍 Testing & Management

| Task | Command |
|------|---------|
| Test config syntax | `httpd -t` |
| Dump virtual host config | `httpd -D DUMP_VHOSTS` |
| Manage Apache process | `apachectl` |
| Set basic auth passwords | `htpasswd` |
| Get SELinux Booleans | `getsebool -a | grep 'httpd'` |

---

## 📁 Directory Directive Example

```apache
<Directory "/var/www/html/files">
  Options Indexes MultiViews
  Require group admins
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>
```

---

## 🔐 Basic Auth `.htaccess` Example

```apache
Options Indexes Multiviews
Require group admins
AuthType Basic
AuthName "Password Required"
AuthUserFile /etc/httpd/password.txt
AuthGroupFile /etc/httpd/group.txt
```

---

## 🧩 Options & Access Control

| Option | Description | Access Control | Description |
|--------|-------------|----------------|-------------|
| `ExecCGI` | Execute CGI scripts | `AuthType` | Set basic authentication |
| `FollowSymLinks` | Follow symbolic links | `AuthName` | Label/comment |
| `Includes` | Allow server-side includes | `AuthBasicProvider` | Auth type |
| `Indexes` | Show index if no index.html | `AuthUserFile` | User password file |
| `MultiViews` | Extension substitution | `AuthGroupFile` | Group password file |
| `ALL` | All options minus MultiViews | `Require` | user, valid-user, group, ip, host, all |

---

## 🌐 Virtual Host Example

```apache
<VirtualHost *:80>
  DocumentRoot /var/www/html/testhost.com/
  ServerAdmin admin@testhost.com
  ServerName testhost.com
  ErrorLog logs/testhost-error.log
  CustomLog logs/testhost-access.log common
</VirtualHost>
```

---

 
