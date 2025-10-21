# 🛠️ Config Files RHEL 9

## 📁 File: `/etc/sysconfig/network-scripts/ifcfg-eth#`

This file contains network settings for each network interface.

---

### 🧷 Static IP Example

```ini
DEVICE=eth0
BOOTPROTO=none
IPV6INIT=yes
MTU=1500
NM_CONTROLLED=no
ONBOOT=yes
TYPE=Ethernet
HWADDR=00:19:87:65:43:21
IPADDR=192.168.0.101
NETMASK=255.255.255.0
GATEWAY=192.168.0.10
DNS1=192.168.0.100
USERCTL=no
```

---

### 🔄 Dynamic IP Example

```ini
DEVICE=eth0
BOOTPROTO=dynamic
```

---

## 🧩 Configuration Parameters

| Argument | Description |
|----------|-------------|
| `DEVICE=` | Network device name (e.g., eth0, eth1) |
| `BOOTPROTO=` | Static (`none`) or dynamic |
| `IPV6INIT=` | Initialize IPv6 |
| `MTU=` | Maximum transmission unit |
| `NM_CONTROLLED=` | Controlled by NetworkManager? (`yes` or `no`) |
| `ONBOOT=` | Start interface on boot? |
| `TYPE=` | Type of network card (e.g., Ethernet) |
| `HWADDR=` | Hardware address (MAC) |
| `IPADDR=` | IP address |
| `NETMASK=` | Network subnet mask |
| `GATEWAY=` | Default gateway for the interface |
| `DNS1=` | Nameserver for the interface |
| `USERCTL=` | Allow non-root users to control the device |

---

