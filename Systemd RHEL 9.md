# ⚙️ Systemd RHEL 9

## 🔧 Services

| Common Task | Systemd | Legacy Red Hat | Legacy Debian |
|-------------|---------|----------------|----------------|
| Start service | `systemctl start httpd` | `service httpd start` | `/etc/init.d/httpd start` |
| Stop service | `systemctl stop httpd` | `service httpd stop` | `/etc/init.d/httpd stop` |
| Restart service | `systemctl restart httpd` | `service httpd restart` | `/etc/init.d/httpd restart` |
| Reload service config | `systemctl reload httpd` | `service httpd reload` | `/etc/init.d/httpd reload` |
| Show service status | `systemctl status httpd` | `service httpd status` | `/etc/init.d/httpd status` |
| Show all service statuses | `systemctl list-units -t service --all` | `service --status-all` | NA |
| Start service on boot | `systemctl enable httpd` | `chkconfig httpd on` | `update-rc.d httpd enable` |
| Disable service on boot | `systemctl disable httpd` | `chkconfig httpd off` | `update-rc.d httpd disable` |
| Add to runlevel | `systemctl enable httpd` | `chkconfig httpd --level 3` | `update-rc.d httpd enable 3` |
| Show all services | `systemctl list-unit-files -t service` | `chkconfig --list` | `rcconf --list` |
| Show modified services | `systemd-delta` | NA | — |
| Show details of service | `systemctl show httpd` | NA | — |
| Block service | `systemctl mask httpd` | NA | NA |
| Unblock service | `systemctl unmask httpd` | NA | NA |
| Is service enabled | `systemctl is-enabled httpd` | `chkconfig --list / grep httpd` | `ls /etc/init.d/rc.d/rc3.d/S*` |

## 🎯 Runlevels / Targets

| Common Task | Systemd | Legacy Red Hat | Legacy Debian |
|-------------|---------|----------------|----------------|
| Change to runlevel | `systemctl isolate basic.target` | `init 3` | `init 3` |
| Change to rescue mode | `systemctl rescue` | `init 1` | `init 1` |
| Set default runlevel | `systemctl set-default user.target` | `vi /etc/inittab` | `vi /etc/inittab` |
| Show current runlevel | `systemctl list-units -t target` | `runlevel` | `runlevel` |
| Get default runlevel | `systemctl get-default` | `grep default /etc/inittab` | `grep default /etc/inittab` |
| Power off system | `systemctl poweroff` | `shutdown -h now` | `shutdown -h now` |
| Halt system | `systemctl halt` | NA | NA |
| Reboot system | `systemctl reboot` | `shutdown -r now` | `shutdown -r now` |

## 🛠️ Miscellaneous

| Task | Command |
|------|---------|
| Run systemd commands remotely | `systemctl --host user@host_name command` |
| Analyze boot performance | `systemd-analyze blame` |

---

 
