# Day 02 – Linux Architecture Notes

## What is Linux?

- Linux is an **open-source operating system** created by Linus Torvalds as a pet project.
- It comes in multiple **flavours (distros):** Ubuntu, Debian, Mint, Kali, etc.
- ~90% of applications and servers run on Linux.
- Unix is the paid counterpart, mostly used in macOS.

---

## Linux Architecture (How it works)

Linux has 3 core layers:

```
[ Applications ]   ← Programs run by the user (browsers, scripts, etc.)
[    Shell     ]   ← Interface between user and the OS (bash, zsh)
[    Kernel    ]   ← Core of the OS; written in C; manages hardware
```

- **Kernel** – The innermost layer. Written in C. Manages CPU, memory, and hardware.
- **Shell** – Interface between the user and the kernel. Interprets commands.
- **Applications** – Programs that run on top of the shell.

---

## File System Hierarchy

- Everything in Linux starts from `/` (root).
- **"Everything in Linux is a file or folder."**
- **"Everything in Linux is a process."**

Key directories:

| Path | Purpose |
|------|---------|
| `/` | Root – starting point of the entire filesystem |
| `/bin` | Essential binaries (ls, cd, cat, etc.) |
| `/etc` | Configuration files (e.g. `/etc/os-release`) |
| `/home` | User home directories |
| `/var` | Variable data (logs, etc.) |

---

## Processes in Linux

- Every running program is a **process**.
- **systemd** is the first process started by the kernel — it gets **PID 1**.
- All other processes are children of systemd.

### Process States

| State | Meaning |
|-------|---------|
| Running | Actively using the CPU |
| Sleeping | Waiting for a resource or event |
| Stopped | Paused (e.g. by Ctrl+Z) |
| Zombie | Finished but not cleaned up by parent |

---

## What is systemd?

- **systemd** is the **init system** in modern Linux distros.
- It starts and manages services (daemons) at boot and runtime.
- It is always **PID 1** — the parent of all processes.

### Why it matters for DevOps

- Start/stop/restart services: `systemctl restart nginx`
- Check service status: `systemctl status sshd`
- Enable services at boot: `systemctl enable docker`
- View logs: `journalctl -u nginx --since today`

---

## 5 Daily-Use Linux Commands

| Command | What it does |
|---------|-------------|
| `ls -l` | List files with details (permissions, owner, size) |
| `pwd` | Print current working directory |
| `cd <dir>` | Change directory |
| `cat <file>` | View file contents |
| `ps aux` | List all running processes |

**Bonus commands practiced today:**

```bash
df -h          # Check disk usage (human-readable)
free -h        # Check memory usage
uptime         # How long the system has been running
date           # Current date and time
history        # View command history
```

---

## File Operations Practiced

```bash
mkdir Harshal           # Create a directory
cd Harshal/             # Navigate into it
touch Harshal.txt       # Create an empty file
vi Harshal.txt          # Edit the file using vi
cat Harshal.txt         # View file contents
head Harshal.txt        # Show first 10 lines (default)
tail Harshal.txt -n 1   # Show last 1 line
tail Harshal.txt -n 2   # Show last 2 lines
```

> **Note:** Linux commands are case-sensitive. `Head` ≠ `head`

---

## Key Takeaways

- Linux is the backbone of DevOps — servers, containers, and CI/CD all run on it.
- The **Kernel** manages hardware; the **Shell** is your interface to it.
- **systemd (PID 1)** is the init system — master of all processes.
- Knowing how to navigate the filesystem and manage processes is foundational for debugging any production issue.