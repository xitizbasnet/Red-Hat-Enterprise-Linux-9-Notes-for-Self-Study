# 🔥 firewalld RHEL 9

## 🌐 Zone Concept

Every network packet is associated with a zone based on:

- The network address bound to a zone
- The network interface bound to a zone
- Otherwise, it defaults to the system’s default zone

---

## 🛡️ Zone Management Commands

| Task | Command |
|------|---------|
| Check status | `systemctl status firewalld` |
| Get default zone | `firewall-cmd --get-default-zone` |
| List zones with interfaces | `firewall-cmd --get-active-zones` |
| List all zones | `firewall-cmd --get-zones` |
| Change default zone | `firewall-cmd --set-default-zone=home` |
| Add interface to zone | `firewall-cmd --permanent --zone=internal --change-interface=eth0` |
| Modify zone via NetworkManager | `nmcli con mod "System eth0" connection.zone internal` |
| Bring up zone | `nmcli con up "System eth0"` |
| List zone for eth0 | `firewall-cmd --get-zone-of-interface=eth0` |
| List permanent zone info | `firewall-cmd --permanent --zone=public --list-all` |
| Create new zone | `firewall-cmd --permanent --new-zone=test` |

---

## 🔧 Zone Configuration Commands

| Task | Command |
|------|---------|
| Add source to zone | `firewall-cmd --permanent --zone=trusted --add-source=192.168.2.0/24` |
| Remove source from zone | `firewall-cmd --permanent --zone=trusted --remove-source=192.168.2.0/24` |
| Add service to zone | `firewall-cmd --permanent --zone=internal --add-service=http` |
| Add port 443 to zone | `firewall-cmd --zone=internal --add-port=443/tcp` |
| Add new service | `firewall-cmd --permanent --new-service=haproxy` |
| Create direct rule | `firewall-cmd --direct --add-rule ipv4 filter INPUT 0 -p tcp --dport 9000 -j ACCEPT` |
| Reload firewall | `firewall-cmd --reload` |

---

