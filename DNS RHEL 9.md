# 🌐 DNS RHEL 9

## 📁 BIND Configuration (`/etc/named.conf`)

```conf
zone "example.com" IN {
  type master;
  file "example.com.zone";
  allow-update { none; };
};

zone "1.168.192.in-addr.arpa" IN {
  type master;
  file "example.com.rr.zone";
  allow-update { none; };
};
```

---

## 📦 Forward Zone File (`/var/named/example.com.zone`)

```dns
$TTL 86400
@ IN SOA nameserver.example.com. admin.example.com. (
  2010031003 ; Serial (YYMMDDNN)
  28800      ; Refresh
  7200       ; Retry
  864000     ; Expire
  86400      ; Minimum TTL
)

NS nameserver.example.com.
MX 10 mailserver.example.com.

$ORIGIN example.com.
nameserver IN A 192.168.1.100
example.com. IN A 192.168.1.100
```

---

## 🔁 Reverse Zone File (`/var/named/example.rr.com.zone`)

```dns
$TTL 86400
@ IN SOA localhost. root. (
  2010031003 ; Serial
  3H         ; Refresh
  15M        ; Retry
  1W         ; Expire
  1D         ) ; Minimum
)

NS nameserver.example.com.

$ORIGIN 1.168.192.in-addr.arpa.
100 IN PTR example.com.
```

---

## 🛠️ DNS Tools

| Task | Command |
|------|---------|
| Install BIND | `yum install bind` |
| Forward lookup | `dig @nameserver example.com` |
| Reverse lookup | `dig -x @nameserver 192.168.0.101` |
| Check zone file | `named-checkzone example.com /var/named/example.com.zone` |
| Check BIND config | `named-checkconf /etc/named.conf` |

---

 
