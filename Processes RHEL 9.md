# 🧠 Processes — RHEL 9

## 🔍 Viewing Processes

| Command | Purpose |
|--------|---------|
| `ps -ef` | Show every process with full output |
| `ps -ejH` | Show process hierarchy (tree) |
| `pstree` | Show more graphical process tree |
| `ps -efL` | Show process threads |
| `ps -efZ` | Show processes with SELinux security context |
| `ps -u root -f` | Show all processes run by the user root with full output |
| `ps -eo pid,ni,pri,stat,comm` | Show customizable output fields |
| `ps -C salt-master -o pid=` | Show process IDs of a specific process (salt-master) |
| `ps -p 25409 -o comm=` | Show only the name of process ID 25409 |
| `ps -f -t tty1` | Show all processes running on a certain terminal (tty1) |
| `ps -eo pid, user, args -- sort user` | Show all process IDs, users, and args sorted by user |
| `ps -u root -eo start, pid,args` | Show all process args run by a user with start time |

## 🔎 Filtering & Grepping

| Command | Purpose |
|--------|---------|
| `pgrep -u root sshd` | Grep for sshd processes run by root |
| `pgrep -u root,bob sshd` | Grep for sshd processes run by root OR bob |
| `ps -fp $(pgrep -d, -x salt-master)` | Give detailed statistics on all salt-master processes |

## 🛑 Killing Processes

| Command | Purpose |
|--------|---------|
| `kill 25045` | Kill process 25045 nicely |
| `kill -9 25045` | Kill process 25045 forcibly |
| `kill -HUP 25045` | Send process 25045 hangup signal (reread config) |
| `pkill salt-master` | Kill all processes named salt-master nicely |
| `pkill -9 salt-master` | Kill all processes named salt-master forcibly |
| `kill -HUP salt-master` | Send process named salt-master hangup signal |

## ⚙️ Process Priorities

| Command | Purpose |
|--------|---------|
| `nice -10 cp` | Run `cp` with a nice level of +10 |
| `nice --10 cp` | Run `cp` with nice level of -10 |
| `renice -10 cp` | Change nice value of running process (`cp`) |

## 📊 Monitoring & Utilities

| Command | Purpose |
|--------|---------|
| `top` | Show top processes by resource |
| `lsof` | List open files (running programs from disk) |
| `lsof -u root` | List open files owned by root |
| `nohup cp -av /media /backup &` | Run a command that will survive a log-out |
| `pidof crond` | List process ID of `crond` |

---

 
