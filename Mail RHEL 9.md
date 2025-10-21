# 📬 Mail RHEL 9

## 📦 Installation & Components

| Item | Purpose |
|------|--------|
| `yum groupinstall "Mail Server"` | Installs Dovecot, Sendmail, Cyrus, SpamAssassin |
| `yum install postfix` | Installs Postfix SMTP server |
| `yum install squirrelmail` | Installs Squirrelmail webmail client |
| `yum install system-switch-mail` | Tool to switch between MTAs |

### Mail Components

| Service | Role |
|---------|------|
| Postfix | SMTP server |
| Sendmail | Legacy SMTP server |
| Dovecot | POP/IMAP server |
| Cyrus | POP/IMAP server |
| SpamAssassin | Spam filtering |
| Squirrelmail | Webmail interface |

---

## ⚙️ Configuration Files

| File | Purpose |
|------|--------|
| `/etc/dovecot.conf` | Dovecot configuration |
| `/etc/postfix/main.cf` | Main Postfix config |
| `/etc/postfix/*` | Additional Postfix configs |
| `/var/log/maillog` | Mail system logs |

---

## 📡 SMTP/POP3/IMAP Setup Steps

```bash
# 1. Install mail server group
yum groupinstall "Mail Server"

# 2. Install Postfix
yum install postfix

# 3. Install switch tool
yum install system-switch-mail

# 4. Switch MTA from Sendmail to Postfix
system-config-mail

# 5. Set DNS or /etc/hosts entry
192.168.2.100 example.net mail.example.net

# 6–9. Configure Postfix
myhostname = mail.example.net
myorigin = $mydomain
inet_interfaces = all
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

# 10–13. Enable and start Postfix
chkconfig postfix on
service sendmail stop
chkconfig sendmail off
service postfix start

# 14–15. Enable and start Dovecot
chkconfig dovecot on
service dovecot start
```

---

## 🧪 Mail Troubleshooting

| Step | Description |
|------|-------------|
| 1 | Ping mailserver using `myhostname` from Postfix config |
| 2 | Check listening services for SMTP, POP3, IMAP → `netstat -l` |
| 3 | Test sending/receiving via Thunderbird |
| 4 | Monitor logs → `tail -f /var/log/maillog` |

---

 
