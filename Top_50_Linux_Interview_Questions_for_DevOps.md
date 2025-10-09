
# 🧠 Top 50 Linux Interview Questions & Answers for DevOps

---

### **1. What is Linux?**
Linux is an open-source operating system based on UNIX. It’s widely used in DevOps for servers, containers, and automation because it’s stable, secure, and efficient.

---

### **2. What are the main components of Linux?**
- **Kernel** – Controls hardware.
- **Shell** – Command interpreter.
- **File System** – Organizes data.
- **User Space** – Where applications run.

---

### **3. What is the Linux kernel?**
The kernel is the core of the OS. It manages CPU, memory, devices, and system calls.

---

### **4. What are runlevels?**
Runlevels define the system state (e.g., multi-user, reboot, shutdown).  
Examples: 0 – Halt, 1 – Single-user, 3 – Multi-user (CLI), 5 – GUI, 6 – Reboot.

---

### **5. How do you check system information?**
```bash
uname -a
lsb_release -a
hostnamectl
```

---

### **6. How do you check disk usage?**
```bash
df -h
du -sh *
```

---

### **7. How do you check memory usage?**
```bash
free -h
vmstat
top
```

---

### **8. How do you check CPU usage?**
```bash
top
mpstat
uptime
```

---

### **9. How do you find the top 10 memory-consuming processes?**
```bash
ps -eo pid,comm,%mem --sort=-%mem | head
```

---

### **10. How do you view all running processes?**
```bash
ps -ef
top
```

---

### **11. How do you kill a process?**
```bash
kill <PID>
kill -9 <PID>   # Force kill
```

---

### **12. How do you find which process is using a port?**
```bash
sudo lsof -i :<port>
sudo netstat -tuln | grep <port>
```

---

### **13. How do you check system uptime?**
```bash
uptime
```

---

### **14. How do you find the current working directory?**
```bash
pwd
```

---

### **15. How do you list all files including hidden ones?**
```bash
ls -la
```

---

### **16. How do you search for text in files?**
```bash
grep "error" logfile.txt
```

---

### **17. How do you replace text in a file?**
```bash
sed 's/error/warning/g' logfile.txt
```

---

### **18. How do you extract specific columns from a file?**
```bash
awk '{print $1,$2}' file.txt
```

---

### **19. What is the difference between grep, sed, and awk?**
- **grep** – Search  
- **sed** – Replace/Edit  
- **awk** – Extract and format data  

---

### **20. How do you view last 100 lines of a file?**
```bash
tail -n 100 file.txt
```

---

### **21. How do you monitor logs in real-time?**
```bash
tail -f /var/log/syslog
```

---

### **22. How do you check free disk space on partitions?**
```bash
df -h
```

---

### **23. How do you check file permissions?**
```bash
ls -l
```

---

### **24. How do you change file permissions?**
```bash
chmod 755 filename
```

---

### **25. How do you change file ownership?**
```bash
chown user:group file.txt
```

---

### **26. How do you find large files?**
```bash
find / -type f -size +500M
```

---

### **27. How do you find and delete files older than 7 days?**
```bash
find /path -type f -mtime +7 -delete
```

---

### **28. How do you create and extract tar archives?**
```bash
tar -cvf backup.tar /folder
tar -xvf backup.tar
```

---

### **29. How do you compress and decompress files using gzip?**
```bash
gzip file.txt
gunzip file.txt.gz
```

---

### **30. How do you check network interfaces and IPs?**
```bash
ip addr show
ifconfig
```

---

### **31. How do you test network connectivity?**
```bash
ping google.com
```

---

### **32. How do you check routing table?**
```bash
netstat -rn
ip route
```

---

### **33. How do you list open ports?**
```bash
sudo netstat -tuln
sudo ss -tuln
```

---

### **34. How do you add a new user?**
```bash
sudo useradd username
sudo passwd username
```

---

### **35. How do you delete a user?**
```bash
sudo userdel username
```

---

### **36. How do you switch between users?**
```bash
su - username
```

---

### **37. How do you check currently logged-in users?**
```bash
who
w
```

---

### **38. How do you schedule a job using cron?**
```bash
crontab -e
```
Example:
```
0 2 * * * /home/user/backup.sh
```

---

### **39. How do you list scheduled cron jobs?**
```bash
crontab -l
```

---

### **40. How do you schedule a one-time job?**
```bash
at 10:00 AM
```

---

### **41. How do you check service status in Linux?**
```bash
sudo systemctl status nginx
```

---

### **42. How do you enable a service at boot?**
```bash
sudo systemctl enable nginx
```

---

### **43. How do you restart or stop a service?**
```bash
sudo systemctl restart nginx
sudo systemctl stop nginx
```

---

### **44. What is SELinux?**
SELinux (Security-Enhanced Linux) enforces security policies and controls access between users, apps, and files.

---

### **45. How do you check SELinux status?**
```bash
getenforce
sestatus
```

---

### **46. How do you find the OS version?**
```bash
cat /etc/os-release
```

---

### **47. How do you check currently running kernel version?**
```bash
uname -r
```

---

### **48. What’s the difference between absolute and relative path?**
- **Absolute Path** – Full path from root (`/home/user/file.txt`)
- **Relative Path** – Path from current directory (`./file.txt`)

---

### **49. How do you find command location?**
```bash
which python
whereis nginx
```

---

### **50. How do you check system boot logs?**
```bash
dmesg | less
journalctl -b
```

---

✅ **Bonus Tip for DevOps Interviews:**
Always connect your Linux answers with **real DevOps usage** — for example:
- "We use `systemctl` to manage Jenkins and Docker services."
- "We use `cron` to automate daily backup scripts."
- "We monitor CPU/memory using `top` and send alerts to CloudWatch or Prometheus."
