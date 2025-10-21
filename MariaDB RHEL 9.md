# 🐬 MariaDB RHEL 9

## 📦 RPM Packages

| Package | Purpose |
|---------|---------|
| `mariadb` | MariaDB client tools |
| `mariadb-server` | MariaDB server daemon |

---

## ⚙️ Installation & Setup

| Command | Purpose |
|--------|---------|
| `dnf install -y mariadb mariadb-server` | Install MariaDB packages |
| `sudo systemctl enable --now mariadb` | Start MariaDB and enable on boot |
| `mysql_secure_installation` | Secure MariaDB installation |
| `mysqladmin password "newpass"` | Set root password to `newpass` |

---

## 🔐 Accessing MariaDB

| Command | Purpose |
|--------|---------|
| `mysql -u root -p` | Log in as root (prompt for password) |
| `mysql -h rhhost1 -u user1 -p testdb` | Connect to `testdb` on `rhhost1` as `user1` |

---

## 🗃️ Database & Table Management

| Command | Purpose |
|--------|---------|
| `SHOW DATABASES;` | List all databases |
| `CREATE DATABASE testdb;` | Create a new database named `testdb` |
| `USE testdb;` | Switch to `testdb` |
| `SHOW TABLES;` | List tables in current database |
| `DESCRIBE testtable;` | Show structure of `testtable` |
| `SHOW INDEX FROM testtable;` | Show indexes of `testtable` |
| `CREATE TABLE developers (devnum int, Name varchar(20), Lastname varchar(20));` | Create `developers` table |
| `SELECT * FROM testtable;` | Show all records in `testtable` |
| `SELECT devnum, Name FROM developers;` | Show selected columns from `developers` |

---

## 🧹 Data Operations

| Command | Purpose |
|--------|---------|
| `DELETE FROM developers WHERE Name = 'Bob';` | Delete records where `Name = Bob` |

---

## 💾 Backup & Restore

| Command | Purpose |
|--------|---------|
| `mysqldump -u root -p testdb > testdb.sql` | Backup `testdb` to `testdb.sql` |
| `mysql -u root -p testdb < testdb.sql` | Restore `testdb` from `testdb.sql` |

---

## 🚪 Exit

| Command | Purpose |
|--------|---------|
| `exit` | Quit the MySQL shell |

---

 
