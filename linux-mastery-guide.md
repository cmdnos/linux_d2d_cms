# Linux Mastery Guide: Beginner to Enterprise Professional

A comprehensive guide to Linux concepts and commands, structured for progressive learning from basics to enterprise-level proficiency.

---

## Table of Contents

1. [Beginner Level](#beginner-level)
2. [Intermediate Level](#intermediate-level)
3. [Advanced Level](#advanced-level)
4. [Enterprise/Professional Level](#enterpriseprofessional-level)
5. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

---

## Beginner Level

### 1. File System Navigation

**Concepts:**
- Linux directory structure (/, /home, /etc, /var, /usr, /bin)
- Absolute vs relative paths
- Current working directory
- Hidden files (files starting with .)

**Essential Commands:**
```bash
pwd                    # Print working directory
ls                     # List files and directories
ls -la                 # List all files with details (including hidden)
ls -lh                 # List with human-readable file sizes
cd /path/to/directory  # Change directory
cd ..                  # Go up one directory
cd ~                   # Go to home directory
cd -                   # Go to previous directory
tree                   # Display directory tree structure
```

### 2. File and Directory Operations

**Concepts:**
- Creating, copying, moving, and deleting files/directories
- File naming conventions
- Directory hierarchy

**Essential Commands:**
```bash
mkdir dirname              # Create directory
mkdir -p path/to/dirname   # Create nested directories
touch filename             # Create empty file or update timestamp
cp source dest             # Copy file
cp -r source dest          # Copy directory recursively
mv source dest             # Move or rename file/directory
rm filename                # Remove file
rm -r dirname              # Remove directory recursively
rm -rf dirname             # Force remove directory (use carefully!)
rmdir dirname              # Remove empty directory
```

### 3. Viewing and Editing Files

**Concepts:**
- Text viewers vs editors
- Standard input/output
- File content inspection

**Essential Commands:**
```bash
cat filename               # Display entire file content
less filename              # View file with pagination (q to quit)
more filename              # View file page by page
head filename              # Show first 10 lines
head -n 20 filename        # Show first 20 lines
tail filename              # Show last 10 lines
tail -f filename           # Follow file in real-time (for logs)
nano filename              # Simple text editor
vim filename               # Advanced text editor
```

### 4. File Permissions

**Concepts:**
- User, Group, Others (UGO)
- Read (r=4), Write (w=2), Execute (x=1)
- Numeric and symbolic notation
- Ownership

**Essential Commands:**
```bash
ls -l                      # View permissions
chmod 755 filename         # Set permissions (rwxr-xr-x)
chmod u+x filename         # Add execute permission for user
chmod -R 644 dirname       # Recursively set permissions
chown user:group filename  # Change owner and group
chown -R user dirname      # Recursively change owner
```

**Permission Quick Reference:**
- `777` (rwxrwxrwx) - All permissions for everyone
- `755` (rwxr-xr-x) - Owner full, others read/execute
- `644` (rw-r--r--) - Owner read/write, others read only
- `600` (rw-------) - Owner read/write only

### 5. Getting Help

**Concepts:**
- Manual pages
- Command documentation
- Built-in help

**Essential Commands:**
```bash
man command                # View manual page for command
man -k keyword             # Search manual pages
command --help             # Display command help
whatis command             # Brief description of command
apropos keyword            # Search command descriptions
info command               # Detailed information
```

---

## Intermediate Level

### 6. Text Processing and Search

**Concepts:**
- Pattern matching
- Regular expressions basics
- Text streams and pipelines

**Essential Commands:**
```bash
grep "pattern" filename         # Search for pattern in file
grep -r "pattern" directory     # Recursive search
grep -i "pattern" filename      # Case-insensitive search
grep -v "pattern" filename      # Invert match (exclude pattern)
grep -n "pattern" filename      # Show line numbers
find /path -name "*.txt"        # Find files by name
find /path -type f              # Find files only
find /path -type d              # Find directories only
find /path -mtime -7            # Files modified in last 7 days
find /path -size +100M          # Files larger than 100MB
locate filename                 # Quick file search (uses database)
wc filename                     # Count lines, words, characters
wc -l filename                  # Count lines only
sort filename                   # Sort lines
uniq filename                   # Remove duplicate lines
cut -d',' -f1 file.csv          # Extract column from CSV
```

### 7. Redirection and Pipes

**Concepts:**
- Standard streams (stdin, stdout, stderr)
- Redirection operators
- Pipelines for command chaining

**Essential Commands:**
```bash
command > file                  # Redirect output to file (overwrite)
command >> file                 # Redirect output to file (append)
command 2> file                 # Redirect errors to file
command &> file                 # Redirect both output and errors
command1 | command2             # Pipe output to next command
command < file                  # Use file as input
command1 | tee file | command2  # Write to file and pass to next command
```

**Examples:**
```bash
ls -la > filelist.txt
cat file1.txt file2.txt > combined.txt
grep "error" logfile.log | wc -l
find /var/log -name "*.log" | xargs grep "error"
```

### 8. Process Management

**Concepts:**
- Processes and PIDs
- Foreground vs background processes
- Process states
- Signals

**Essential Commands:**
```bash
ps                         # Show current user processes
ps aux                     # Show all processes
ps -ef                     # Show all processes (alternative format)
top                        # Interactive process viewer
htop                       # Enhanced interactive process viewer
pgrep process_name         # Find process ID by name
pidof process_name         # Find process ID
kill PID                   # Terminate process
kill -9 PID                # Force kill process
killall process_name       # Kill all processes by name
pkill process_name         # Kill processes by name pattern
bg                         # Resume process in background
fg                         # Bring process to foreground
jobs                       # List background jobs
command &                  # Run command in background
nohup command &            # Run command immune to hangups
```

### 9. Disk Usage and Management

**Concepts:**
- Disk space monitoring
- Filesystem types
- Mount points
- Partitions

**Essential Commands:**
```bash
df -h                      # Disk space usage (human-readable)
df -i                      # Inode usage
du -h directory            # Directory size
du -sh directory           # Summary of directory size
du -h --max-depth=1        # Size of subdirectories one level deep
lsblk                      # List block devices
mount                      # Show mounted filesystems
mount /dev/sdb1 /mnt       # Mount device
umount /mnt                # Unmount filesystem
fdisk -l                   # List disk partitions
```

### 10. Network Basics

**Concepts:**
- IP addressing
- Network interfaces
- Ports and services
- DNS

**Essential Commands:**
```bash
ip addr                    # Show IP addresses
ip addr show               # Show network interfaces
ip link                    # Show network devices
ifconfig                   # Show/configure network interfaces (deprecated)
ping hostname              # Test connectivity
ping -c 4 hostname         # Ping 4 times
traceroute hostname        # Trace route to host
netstat -tuln              # Show listening ports
ss -tuln                   # Show listening ports (modern alternative)
nslookup domain            # DNS lookup
dig domain                 # DNS lookup (detailed)
curl url                   # Transfer data from URL
wget url                   # Download file from URL
scp file user@host:/path   # Secure copy to remote host
```

### 11. Archive and Compression

**Concepts:**
- Tar archives
- Compression algorithms (gzip, bzip2, xz)
- Archive vs compression

**Essential Commands:**
```bash
tar -cvf archive.tar files         # Create tar archive
tar -xvf archive.tar               # Extract tar archive
tar -czvf archive.tar.gz files     # Create compressed archive (gzip)
tar -xzvf archive.tar.gz           # Extract gzip archive
tar -cjvf archive.tar.bz2 files    # Create bzip2 archive
tar -xjvf archive.tar.bz2          # Extract bzip2 archive
gzip file                          # Compress file
gunzip file.gz                     # Decompress file
zip archive.zip files              # Create zip archive
unzip archive.zip                  # Extract zip archive
```

**Tar Options:**
- `-c` create
- `-x` extract
- `-v` verbose
- `-f` file
- `-z` gzip
- `-j` bzip2

---

## Advanced Level

### 12. Shell Scripting

**Concepts:**
- Bash scripting basics
- Variables and parameters
- Conditionals and loops
- Functions
- Exit codes

**Essential Commands & Syntax:**
```bash
#!/bin/bash                # Shebang line
variable="value"           # Assign variable
echo $variable             # Use variable
$1, $2, $@                 # Script arguments
$?                         # Exit status of last command
$0                         # Script name
$$                         # Current process ID

# Conditionals
if [ condition ]; then
    commands
elif [ condition ]; then
    commands
else
    commands
fi

# Loops
for item in list; do
    commands
done

while [ condition ]; do
    commands
done

# Functions
function_name() {
    commands
    return value
}

# Test operators
[ -f file ]                # File exists
[ -d directory ]           # Directory exists
[ -z string ]              # String is empty
[ -n string ]              # String is not empty
[ string1 = string2 ]      # Strings are equal
[ num1 -eq num2 ]          # Numbers are equal
```

### 13. User and Group Management

**Concepts:**
- User accounts
- Groups and permissions
- sudo and privilege escalation
- PAM (Pluggable Authentication Modules)

**Essential Commands:**
```bash
whoami                     # Current username
id                         # User and group IDs
users                      # Logged in users
w                          # Who is logged in and what they're doing
last                       # Login history
sudo command               # Execute command as superuser
sudo -i                    # Start root shell
sudo -u user command       # Execute as different user
su - username              # Switch user
useradd username           # Create user
usermod -aG group user     # Add user to group
userdel username           # Delete user
passwd username            # Change user password
groupadd groupname         # Create group
groupdel groupname         # Delete group
groups username            # Show user's groups
```

### 14. System Monitoring and Performance

**Concepts:**
- System resources (CPU, RAM, I/O)
- Load average
- Performance bottlenecks
- System logs

**Essential Commands:**
```bash
uptime                     # System uptime and load
free -h                    # Memory usage
vmstat                     # Virtual memory statistics
vmstat 1                   # Update every second
iostat                     # CPU and I/O statistics
sar                        # System activity report
dmesg                      # Kernel ring buffer messages
dmesg | tail               # Recent kernel messages
journalctl                 # Systemd journal
journalctl -u service      # Logs for specific service
journalctl -f              # Follow journal in real-time
lsof                       # List open files
lsof -i :80                # Show what's using port 80
lsof -u username           # Files opened by user
strace command             # Trace system calls
```

### 15. Systemd and Service Management

**Concepts:**
- Init systems
- Service units
- Targets (runlevels)
- Service dependencies

**Essential Commands:**
```bash
systemctl status service           # Service status
systemctl start service            # Start service
systemctl stop service             # Stop service
systemctl restart service          # Restart service
systemctl reload service           # Reload configuration
systemctl enable service           # Enable at boot
systemctl disable service          # Disable at boot
systemctl list-units               # List all units
systemctl list-units --type=service # List services
systemctl daemon-reload            # Reload systemd configuration
systemctl get-default              # Show default target
systemctl set-default multi-user.target # Set default target
journalctl -u service -f           # Follow service logs
```

### 16. Advanced Text Processing

**Concepts:**
- AWK programming
- SED stream editing
- Regular expressions
- Text transformation

**Essential Commands:**
```bash
# SED
sed 's/old/new/' file              # Replace first occurrence
sed 's/old/new/g' file             # Replace all occurrences
sed -i 's/old/new/g' file          # In-place replacement
sed -n '10,20p' file               # Print lines 10-20
sed '/pattern/d' file              # Delete lines matching pattern

# AWK
awk '{print $1}' file              # Print first column
awk -F',' '{print $2}' file.csv    # CSV with custom delimiter
awk '$3 > 100' file                # Print lines where 3rd field > 100
awk '{sum+=$1} END {print sum}' file # Sum first column
awk 'NR==5' file                   # Print 5th line

# Advanced grep
grep -E 'regex' file               # Extended regex
grep -P 'perl_regex' file          # Perl regex
grep -A 3 'pattern' file           # Show 3 lines after match
grep -B 3 'pattern' file           # Show 3 lines before match
grep -C 3 'pattern' file           # Show 3 lines around match
```

### 17. Cron Jobs and Scheduling

**Concepts:**
- Task scheduling
- Cron syntax
- Anacron for irregular schedules
- At for one-time tasks

**Essential Commands:**
```bash
crontab -l                 # List cron jobs
crontab -e                 # Edit cron jobs
crontab -r                 # Remove all cron jobs

# Cron syntax: minute hour day month weekday command
# * * * * * command
0 2 * * * /path/script     # Run at 2 AM daily
*/5 * * * * /path/script   # Run every 5 minutes
0 0 * * 0 /path/script     # Run weekly on Sunday
0 0 1 * * /path/script     # Run monthly on 1st

at now + 1 hour            # Schedule command in 1 hour
at 10:00 AM                # Schedule at specific time
atq                        # List scheduled at jobs
atrm job_number            # Remove at job
```

---

## Enterprise/Professional Level

### 18. Package Management

**Concepts:**
- Package managers (apt, yum, dnf, zypper)
- Repositories
- Dependencies
- System updates

**Essential Commands:**

**Debian/Ubuntu (APT):**
```bash
apt update                         # Update package list
apt upgrade                        # Upgrade packages
apt dist-upgrade                   # Distribution upgrade
apt install package                # Install package
apt remove package                 # Remove package
apt purge package                  # Remove package and config
apt search keyword                 # Search packages
apt show package                   # Show package details
apt autoremove                     # Remove unused dependencies
dpkg -l                            # List installed packages
dpkg -i package.deb                # Install .deb file
```

**RHEL/CentOS/Fedora (YUM/DNF):**
```bash
yum update                         # Update packages
yum install package                # Install package
yum remove package                 # Remove package
yum search keyword                 # Search packages
yum info package                   # Package information
dnf update                         # Update (Fedora/RHEL 8+)
dnf install package                # Install (newer systems)
rpm -qa                            # List installed packages
rpm -ivh package.rpm               # Install .rpm file
```

### 19. SSH and Remote Access

**Concepts:**
- Public key authentication
- SSH tunneling
- SSH config
- Jump hosts/bastion servers

**Essential Commands:**
```bash
ssh user@hostname                  # Connect to remote host
ssh -p 2222 user@hostname          # Connect on custom port
ssh -i keyfile user@hostname       # Use specific private key
ssh-keygen                         # Generate SSH key pair
ssh-keygen -t rsa -b 4096          # Generate 4096-bit RSA key
ssh-copy-id user@hostname          # Copy public key to remote host
scp file user@host:/path           # Secure copy file
scp -r directory user@host:/path   # Copy directory
rsync -avz source/ dest/           # Sync directories
rsync -avz -e ssh src/ user@host:dest/  # Sync over SSH
ssh -L 8080:localhost:80 user@host # Local port forwarding
ssh -R 8080:localhost:80 user@host # Remote port forwarding
ssh -D 1080 user@host              # Dynamic port forwarding (SOCKS)
ssh -J jump_host target_host       # SSH through jump host
```

**SSH Config (~/.ssh/config):**
```
Host myserver
    HostName 192.168.1.100
    User admin
    Port 2222
    IdentityFile ~/.ssh/mykey
```

### 20. Docker and Containers

**Concepts:**
- Containerization
- Images vs containers
- Dockerfile
- Container orchestration basics

**Essential Commands:**
```bash
docker ps                          # List running containers
docker ps -a                       # List all containers
docker images                      # List images
docker pull image:tag              # Pull image
docker run image                   # Run container
docker run -d image                # Run in detached mode
docker run -p 8080:80 image        # Port mapping
docker run -v /host:/container image # Volume mounting
docker exec -it container bash     # Execute command in container
docker logs container              # View container logs
docker logs -f container           # Follow container logs
docker stop container              # Stop container
docker rm container                # Remove container
docker rmi image                   # Remove image
docker build -t name:tag .         # Build image from Dockerfile
docker-compose up                  # Start services (docker-compose)
docker-compose down                # Stop services
docker system prune                # Clean up unused resources
```

### 21. Git Version Control

**Concepts:**
- Version control
- Branches and merging
- Remote repositories
- Collaboration workflows

**Essential Commands:**
```bash
git init                           # Initialize repository
git clone url                      # Clone repository
git status                         # Check status
git add file                       # Stage file
git add .                          # Stage all changes
git commit -m "message"            # Commit changes
git commit -am "message"           # Stage and commit tracked files
git push origin branch             # Push to remote
git pull                           # Pull from remote
git fetch                          # Fetch from remote
git branch                         # List branches
git branch name                    # Create branch
git checkout branch                # Switch branch
git checkout -b branch             # Create and switch branch
git merge branch                   # Merge branch
git log                            # View commit history
git log --oneline                  # Compact log
git diff                           # Show changes
git stash                          # Stash changes
git stash pop                      # Apply stashed changes
git reset --hard HEAD              # Discard all changes
git revert commit                  # Revert commit
```

### 22. Nginx/Apache Web Servers

**Concepts:**
- Web server configuration
- Virtual hosts
- Reverse proxy
- SSL/TLS certificates

**Essential Commands:**

**Nginx:**
```bash
nginx -t                           # Test configuration
nginx -s reload                    # Reload configuration
systemctl status nginx             # Check status
systemctl restart nginx            # Restart service
cat /var/log/nginx/access.log      # View access logs
cat /var/log/nginx/error.log       # View error logs
```

**Apache:**
```bash
apachectl configtest               # Test configuration
apachectl -t                       # Test configuration (short)
systemctl restart apache2          # Restart (Debian/Ubuntu)
systemctl restart httpd            # Restart (RHEL/CentOS)
a2ensite sitename                  # Enable site (Debian/Ubuntu)
a2dissite sitename                 # Disable site
a2enmod modulename                 # Enable module
a2dismod modulename                # Disable module
```

### 23. Database Management (MySQL/PostgreSQL)

**Concepts:**
- Database servers
- SQL basics
- Backup and restore
- User permissions

**Essential Commands:**

**MySQL/MariaDB:**
```bash
mysql -u user -p                   # Connect to MySQL
mysqldump -u user -p dbname > backup.sql    # Backup database
mysql -u user -p dbname < backup.sql        # Restore database
mysql -u user -p -e "SHOW DATABASES;"       # Execute query
mysqlcheck -u user -p --all-databases       # Check all databases
```

**PostgreSQL:**
```bash
psql -U user -d database           # Connect to PostgreSQL
pg_dump dbname > backup.sql        # Backup database
psql dbname < backup.sql           # Restore database
pg_dumpall > full_backup.sql       # Backup all databases
createdb dbname                    # Create database
dropdb dbname                      # Drop database
```

### 24. Firewall and Security

**Concepts:**
- Firewall rules
- Port management
- SELinux/AppArmor
- Security hardening

**Essential Commands:**

**UFW (Ubuntu):**
```bash
ufw status                         # Check firewall status
ufw enable                         # Enable firewall
ufw disable                        # Disable firewall
ufw allow 22                       # Allow SSH
ufw allow 80/tcp                   # Allow HTTP
ufw deny 23                        # Deny telnet
ufw delete allow 80                # Remove rule
ufw reset                          # Reset to defaults
```

**Firewalld (RHEL/CentOS):**
```bash
firewall-cmd --state               # Check status
firewall-cmd --list-all            # List all rules
firewall-cmd --add-port=80/tcp     # Add port
firewall-cmd --add-port=80/tcp --permanent  # Add permanent rule
firewall-cmd --reload              # Reload rules
firewall-cmd --add-service=http    # Add service
firewall-cmd --remove-port=80/tcp  # Remove port
```

**IPTables:**
```bash
iptables -L                        # List rules
iptables -A INPUT -p tcp --dport 22 -j ACCEPT  # Allow SSH
iptables -A INPUT -j DROP          # Drop all other input
iptables-save > /etc/iptables/rules.v4  # Save rules
iptables-restore < /etc/iptables/rules.v4  # Restore rules
```

**SELinux:**
```bash
getenforce                         # Check SELinux status
setenforce 0                       # Set to permissive
setenforce 1                       # Set to enforcing
sestatus                           # SELinux status details
semanage port -l                   # List port contexts
semanage port -a -t http_port_t -p tcp 8080  # Add port context
ausearch -m avc -ts recent         # Recent SELinux denials
```

### 25. Kubernetes Basics

**Concepts:**
- Container orchestration
- Pods, Services, Deployments
- kubectl CLI
- Cluster management

**Essential Commands:**
```bash
kubectl get pods                   # List pods
kubectl get pods -A                # List all pods (all namespaces)
kubectl get nodes                  # List nodes
kubectl get services               # List services
kubectl get deployments            # List deployments
kubectl describe pod podname       # Pod details
kubectl logs podname               # View pod logs
kubectl logs -f podname            # Follow pod logs
kubectl exec -it podname -- bash   # Execute command in pod
kubectl apply -f manifest.yaml     # Apply configuration
kubectl delete -f manifest.yaml    # Delete resources
kubectl scale deployment name --replicas=3  # Scale deployment
kubectl port-forward pod 8080:80   # Port forward
kubectl get events                 # View cluster events
kubectl top nodes                  # Node resource usage
kubectl top pods                   # Pod resource usage
```

### 26. Infrastructure as Code (Terraform/Ansible)

**Concepts:**
- Configuration management
- Infrastructure provisioning
- Idempotency
- State management

**Essential Commands:**

**Terraform:**
```bash
terraform init                     # Initialize working directory
terraform plan                     # Preview changes
terraform apply                    # Apply changes
terraform destroy                  # Destroy infrastructure
terraform validate                 # Validate configuration
terraform fmt                      # Format configuration files
terraform state list               # List resources in state
terraform output                   # Show outputs
```

**Ansible:**
```bash
ansible all -m ping                # Ping all hosts
ansible-playbook playbook.yml      # Run playbook
ansible-playbook playbook.yml --check  # Dry run
ansible-playbook playbook.yml --tags "tag"  # Run specific tags
ansible-inventory --list           # List inventory
ansible-vault create secret.yml    # Create encrypted file
ansible-vault edit secret.yml      # Edit encrypted file
ansible-galaxy install role        # Install role
```

### 27. Log Management and Analysis

**Concepts:**
- System logs
- Application logs
- Log rotation
- Centralized logging

**Essential Commands:**
```bash
# System logs (traditional)
tail -f /var/log/syslog            # Follow system log
tail -f /var/log/auth.log          # Authentication logs
tail -f /var/log/messages          # General messages (RHEL)

# Journalctl (systemd)
journalctl -f                      # Follow all logs
journalctl -u service              # Service-specific logs
journalctl -p err                  # Error priority and above
journalctl --since "1 hour ago"    # Logs from last hour
journalctl --since "2024-01-01"    # Logs since date
journalctl -b                      # Current boot logs
journalctl -b -1                   # Previous boot logs
journalctl --disk-usage            # Journal disk usage
journalctl --vacuum-time=7d        # Clean logs older than 7 days

# Log rotation
logrotate /etc/logrotate.conf      # Rotate logs
logrotate -f /etc/logrotate.conf   # Force rotation

# Log analysis
zgrep "pattern" /var/log/syslog*   # Search compressed logs
awk '{print $1}' access.log | sort | uniq -c | sort -rn  # Count by IP
```

### 28. Performance Tuning and Troubleshooting

**Concepts:**
- System bottlenecks
- Resource optimization
- Kernel parameters
- Performance profiling

**Essential Commands:**
```bash
# CPU analysis
mpstat -P ALL 1                    # Per-CPU statistics
pidstat 1                          # Per-process statistics
perf top                           # System profiling
perf record -g command             # Record performance data
perf report                        # Analyze recorded data

# Memory analysis
free -h                            # Memory usage
vmstat 1                           # Virtual memory stats
slabtop                            # Kernel slab cache
/proc/meminfo                      # Detailed memory info

# I/O analysis
iotop                              # I/O usage by process
iostat -x 1                        # Extended I/O statistics
iowait                             # I/O wait time

# Network analysis
iftop                              # Network bandwidth by connection
nethogs                            # Network bandwidth by process
tcpdump -i eth0                    # Packet capture
tcpdump -i eth0 port 80            # Capture HTTP traffic
wireshark                          # GUI packet analyzer

# System tuning
sysctl -a                          # List all kernel parameters
sysctl net.ipv4.ip_forward=1       # Enable IP forwarding
sysctl -p                          # Reload sysctl.conf
ulimit -a                          # Show resource limits
ulimit -n 4096                     # Set open files limit

# Debugging
ldd /path/to/binary                # Show shared library dependencies
ltrace command                     # Library call trace
strace -p PID                      # Trace running process
gdb program                        # GNU debugger
```

### 29. Backup and Disaster Recovery

**Concepts:**
- Backup strategies (full, incremental, differential)
- Snapshot management
- Disaster recovery planning
- Data integrity

**Essential Commands:**
```bash
# rsync backups
rsync -avz --delete source/ dest/  # Mirror backup
rsync -avz --backup --backup-dir=../backup-$(date +%Y%m%d) source/ dest/

# tar backups
tar -czf backup-$(date +%Y%m%d).tar.gz /path/to/backup
tar -xzf backup.tar.gz -C /restore/path

# dd (disk imaging)
dd if=/dev/sda of=/backup/disk.img bs=4M status=progress
dd if=/dev/sda of=/dev/sdb bs=4M conv=noerror,sync  # Clone disk

# Database backups
mysqldump --all-databases --single-transaction | gzip > all-db-$(date +%Y%m%d).sql.gz
pg_dumpall | gzip > pg-all-$(date +%Y%m%d).sql.gz

# LVM snapshots
lvcreate -L 5G -s -n snap /dev/vg/lv  # Create snapshot
mount /dev/vg/snap /mnt/snap          # Mount snapshot
lvremove /dev/vg/snap                 # Remove snapshot

# Verification
md5sum file > file.md5                # Create checksum
md5sum -c file.md5                    # Verify checksum
sha256sum file                        # SHA256 checksum
```

### 30. High Availability and Clustering

**Concepts:**
- Load balancing
- Failover
- Cluster management
- Distributed systems

**Essential Commands:**
```bash
# Keepalived (VRRP)
systemctl status keepalived
ip addr show | grep VIP            # Check virtual IP

# HAProxy
haproxy -f /etc/haproxy/haproxy.cfg -c  # Check config
systemctl reload haproxy           # Reload config
echo "show stat" | socat stdio /var/run/haproxy.sock  # Statistics

# Pacemaker/Corosync
pcs status                         # Cluster status
pcs cluster start --all            # Start cluster
pcs resource show                  # Show resources
crm_mon -1                         # Monitor cluster
corosync-cfgtool -s                # Corosync status

# etcd
etcdctl member list                # List cluster members
etcdctl endpoint health            # Check endpoint health
etcdctl get / --prefix --keys-only # List all keys
```

---

## Quick Reference Cheatsheet

### File Operations
```bash
ls -lah        # List all files with details
cp -r src dst  # Copy recursively
mv old new     # Move/rename
rm -rf dir     # Remove directory forcefully
find /path -name "*.log"  # Find files
```

### Text Processing
```bash
grep -r "text" /path     # Recursive search
sed 's/old/new/g' file   # Replace text
awk '{print $1}' file    # Print first column
tail -f file             # Follow file
```

### System Info
```bash
uname -a        # System information
df -h           # Disk usage
free -h         # Memory usage
ps aux          # All processes
top             # Process monitor
```

### Network
```bash
ip addr         # IP addresses
ping host       # Test connectivity
ss -tuln        # Listening ports
curl URL        # Transfer data
scp file user@host:/path  # Secure copy
```

### Permissions
```bash
chmod 755 file         # rwxr-xr-x
chown user:group file  # Change owner
```

### Package Management (Debian/Ubuntu)
```bash
apt update && apt upgrade  # Update system
apt install package        # Install
apt search keyword         # Search
```

### Services
```bash
systemctl status service   # Check status
systemctl start service    # Start service
systemctl enable service   # Enable at boot
journalctl -u service -f   # Follow logs
```

### Docker
```bash
docker ps -a           # List containers
docker images          # List images
docker run -d image    # Run detached
docker logs -f container  # Follow logs
docker exec -it container bash  # Shell
```

### Git
```bash
git status             # Check status
git add .              # Stage all
git commit -m "msg"    # Commit
git push origin main   # Push
git pull               # Pull changes
```

---

## Learning Path Recommendations

### Week 1-2: Beginner
Focus on sections 1-5. Practice daily navigation, file operations, and reading documentation.

### Week 3-4: Intermediate
Master sections 6-11. Build small shell scripts, practice text processing, and understand process management.

### Month 2: Advanced
Dive into sections 12-17. Write automation scripts, configure services, and practice system monitoring.

### Month 3+: Enterprise/Professional
Work through sections 18-30. Set up lab environments with Docker/Kubernetes, practice infrastructure as code, and simulate production scenarios.

---

## Practice Tips

1. **Set up a lab environment**: Use VirtualBox, VMware, or cloud providers (AWS free tier, Google Cloud, Azure)
2. **Practice daily**: Run at least 10-15 commands each day
3. **Break things**: Create VMs specifically for experimentation
4. **Read logs**: Develop the habit of checking logs for troubleshooting
5. **Automate tasks**: Convert repetitive tasks into shell scripts
6. **Join communities**: Participate in r/linux, r/linuxadmin, Stack Overflow
7. **Build projects**: Deploy web servers, databases, monitoring solutions
8. **Document everything**: Keep notes on problems and solutions

---

## Additional Resources

- **Official Documentation**: Always start here for any tool
- **Linux Journey**: https://linuxjourney.com
- **OverTheWire**: Wargames for learning security (Bandit for beginners)
- **Linux Foundation Training**: Professional certifications
- **Red Hat Learning**: RHCSA/RHCE certification paths
- **Man Pages**: `man command` is your best friend
- **Stack Overflow**: For specific problem-solving
- **GitHub**: Study open-source projects and scripts

---

## Contributing

Found an error or want to add something? Feel free to submit a pull request or open an issue!

---

**Last Updated**: March 2026  
**License**: MIT  
**Author**: Your GitHub Username

---

*Remember: The best way to learn Linux is by doing. Don't just read—practice every command in a safe environment!*
