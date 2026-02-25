# Linux Administration Research Project  
**Author:** Oluwatunmise Adesanya  
**Course:** Linux Administration  

---

# Table of Contents

1. Introduction  
2. Linux Architecture and Core Concepts  
3. Filesystem Hierarchy Standard (FHS)  
4. Linux Distributions  
5. User and File Management  
6. System Administration and Service Management  
7. Networking in Linux  
8. Firewall and Security Configuration  
9. Package Management Systems  
10. System Monitoring and Performance Optimization  
11. SSH and Secure Remote Access  
12. Mandatory Access Control: SELinux & AppArmor  
13. Backup Strategies and Disaster Recovery  
14. Conclusion  
15. References  

---

# 1. Introduction

Linux administration is a fundamental discipline in modern computing infrastructure. Linux powers enterprise servers, cloud platforms, DevOps pipelines, cybersecurity environments, and embedded systems. Due to its open-source architecture, scalability, and security-focused design, Linux has become the dominant operating system in server and cloud computing environments.

This research explores Linux system architecture, file systems, user management, networking, package management, performance monitoring, security mechanisms, and backup strategies. The objective is to demonstrate a deep technical understanding suitable for enterprise-level system administration.

---

# 2. Linux Architecture and Core Concepts

Linux consists of several major components:

- **Kernel** – Core of the OS, manages hardware, memory, CPU, and processes  
- **Shell** – Interface between user and kernel (e.g., Bash)  
- **System Libraries** – Provide functionality to applications  
- **Utilities** – Command-line tools for system management  

## Key Differences Between Linux, Windows, and macOS

| Feature | Linux | Windows | macOS |
|----------|--------|----------|--------|
| Source Model | Open-source | Proprietary | Proprietary (Unix-based core) |
| Kernel Type | Monolithic | Hybrid | Hybrid (XNU) |
| Customization | Highly flexible | Limited | Controlled |
| Security Model | Strong permission + MAC | ACL-based | Unix permission model |
| Server Usage | Dominant | Moderate | Limited |

Linux’s modularity and command-line control make it highly suitable for automation and DevOps workflows.

---

# 3. Filesystem Hierarchy Standard (FHS)

Linux follows the **Filesystem Hierarchy Standard (FHS)**.

| Directory | Description |
|------------|--------------|
| `/bin` | Essential binaries required for system boot |
| `/sbin` | System binaries for administration |
| `/etc` | Configuration files |
| `/home` | User home directories |
| `/root` | Root administrator home |
| `/var` | Variable data (logs, mail, spool files) |
| `/usr` | Secondary hierarchy for applications |
| `/dev` | Device files |
| `/proc` | Virtual filesystem for process/kernel info |

Example command:
```bash
ls -l /
```

---

# 4. Linux Distributions

A Linux distribution packages the Linux kernel with GNU tools, package managers, and desktop/server utilities.

### Major Distributions

- **Ubuntu** – Beginner-friendly, cloud and server support  
- **Debian** – Stability-focused  
- **Rocky Linux** – Enterprise-grade RHEL alternative  
- **Fedora** – Cutting-edge development  
- **Kali Linux** – Cybersecurity penetration testing  

Each distribution uses a specific package management system.

---

# 5. User and File Management

## User Management

### Create User
```bash
sudo useradd -m username
sudo passwd username
```

### Modify User
```bash
sudo usermod -aG sudo username
```

### Delete User
```bash
sudo userdel -r username
```

User information is stored in:

```
/etc/passwd
/etc/shadow
/etc/group
```

---

## File Permissions Model

Linux uses a three-level permission structure:

- Owner
- Group
- Others

Permissions:
- r (4) = Read
- w (2) = Write
- x (1) = Execute

Example:
```bash
chmod 755 script.sh
```

Numeric breakdown:
7 (rwx) = 4+2+1  
5 (r-x) = 4+1  

---

# 6. System Administration and Service Management

Linux uses **systemd** in modern distributions.

### Manage Services

```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```

Services run as background processes (daemons).

---

# 7. Networking in Linux

## Essential Commands

```bash
ip addr show
ip route
ping google.com
ss -tuln
```

The `ip` command replaces `ifconfig`.

---

## Static IP Configuration (Ubuntu Netplan)

Edit:

```bash
sudo nano /etc/netplan/01-netcfg.yaml
```

Apply:

```bash
sudo netplan apply
```

---

# 8. Firewall and Security Configuration

## iptables

```bash
sudo iptables -L
```

## firewalld

```bash
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --reload
```

Firewalls filter incoming and outgoing traffic.

---

# 9. Package Management Systems

| Tool | Distribution |
|------|--------------|
| apt | Debian/Ubuntu |
| yum | Older RHEL |
| dnf | Fedora/RHEL 8+ |

### Install Package
```bash
sudo apt install nginx
```

### Update System
```bash
sudo apt update && sudo apt upgrade
```

---

# 10. System Monitoring and Performance Optimization

| Tool | Purpose |
|------|----------|
| top | Real-time CPU & memory |
| htop | Interactive monitor |
| vmstat | Memory statistics |
| iostat | Disk I/O |
| free -h | Memory usage |

### Disk Usage
```bash
df -h
du -sh /home
```

Monitoring ensures proactive system optimization.

---

# 11. SSH (Secure Shell)

SSH provides encrypted remote access.

### Install SSH Server
```bash
sudo apt install openssh-server
```

### Connect
```bash
ssh user@192.168.1.10
```

SSH uses port 22 by default and supports key-based authentication.

---

# 12. Mandatory Access Control (MAC)

## SELinux
- Used in RHEL-based systems
- Enforces strict access control policies

Check status:
```bash
sestatus
```

## AppArmor
- Used in Ubuntu
- Profile-based security

Check status:
```bash
sudo aa-status
```

These enhance security beyond standard permissions.

---

# 13. Backup Strategies and Disaster Recovery

## Backup Tools

### rsync
```bash
rsync -av /home /backup
```

### tar
```bash
tar -cvf backup.tar /home
```

### dd (Disk Imaging)
```bash
dd if=/dev/sda of=/backup.img
```

## Recovery Strategies

- Scheduled automated backups
- RAID redundancy
- Bootable recovery media
- Log analysis in `/var/log`
- Restore from disk images

Enterprise environments implement multi-layer backup strategies.

---

# 14. Conclusion

Linux administration requires mastery of system architecture, permissions, networking, security, package management, and recovery planning. Due to its stability and scalability, Linux remains the backbone of cloud computing, DevOps pipelines, and enterprise infrastructure.

A strong understanding of these concepts prepares professionals for certifications such as LPIC, RHCSA, and CompTIA Linux+.

---

# 15. References 

Nemeth, E., Snyder, G., Hein, T., & Whaley, B. (2017). *UNIX and Linux System Administration Handbook* (5th ed.). Addison-Wesley.

Shotts, W. (2019). *The Linux Command Line* (2nd ed.). No Starch Press.

Red Hat. (2023). *Red Hat Enterprise Linux Documentation*. https://access.redhat.com/documentation/

The Linux Foundation. (2023). *Introduction to Linux*. https://training.linuxfoundation.org/

Ubuntu Documentation Team. (2023). *Ubuntu Server Guide*. https://ubuntu.com/server/docs

---
