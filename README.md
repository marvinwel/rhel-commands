# Red Hat Enterprise Linux Commands
#### This GitHub repository contains a curated collection of useful Red Hat Enterprise Linux (RHEL) commands. Whether you're managing users, configuring services, troubleshooting, or automating tasks, you'll find helpful command-line examples and explanations here to make your RHEL experience smoother.
<br><br>
# Table of Contents
- [Access Control List](#Access-Control-List)  
- [Monitor Users](#Monitor-Users)
- [Cut](#Cut)
- [AWK](#awk)
- [GREP](#GREP)
- [EGREP](#EGREP)
- [Sort/Uniq](#Sort/Uniq)
- [Word Count](#Word-Count)
- [DIFF](#Diff)
- [CMP](#CMP)
- [TAR](#TAR)
- [GZIP](#GZIP)
- [Split](#Split)
- [SED](#SED)
- [System Utility Commands](#System-Utility-Commands)
- [Systemctl](#Systemctl)
- [Process Status](#process-Status-(ps))
- [Top](#top)
- [Kill](#kill)
- [Crontab](#Crontab)





### 🔐 [User & Group Management](#User-Account-Management)
- `adduser <username>` – Add a new user  
- `passwd <username>` – Set or update user password  
- `usermod -aG <group> <user>` – Add a user to a group  
- `id <username>` – Show user UID, GID, and group membership  
- `groupadd <groupname>` – Create a new group  

### 📦 Package Management (YUM/DNF)
- `dnf install <package>` – Install a package  
- `dnf remove <package>` – Remove a package  
- `dnf update` – Update all packages  
- `dnf search <keyword>` – Search for a package  
- `dnf list installed` – List installed packages  

### 💻 System Info & Monitoring
- `top` – Real-time process monitoring  
- `htop` – Enhanced process viewer (if installed)  
- `uptime` – Show how long the system has been running  
- `free -h` – Display memory usage  
- `df -h` – Show disk space usage  
- `du -sh <directory>` – Show size of a directory  

### 📁 File Management
- `ls -l` – List directory contents in long format  
- `cp <source> <destination>` – Copy files/directories  
- `mv <source> <destination>` – Move or rename files  
- `rm -rf <directory>` – Delete a directory and its contents  
- `find <path> -name <filename>` – Find files by name  

### 📡 Networking
- `ip a` – Show IP addresses  
- `ping <hostname>` – Test network connectivity  
- `ss -tuln` – Show open ports and listening services  
- `nmcli` – Network manager CLI tool  

### 🔥 Firewall
- `firewall-cmd --state` – Check if the firewall is active  
- `firewall-cmd --add-port=8080/tcp --permanent` – Open port 8080  
- `firewall-cmd --reload` – Apply firewall changes  

### 📜 Logs & Services
- `journalctl -xe` – View system logs  
- `systemctl status <service>` – Check status of a service  
- `systemctl start|stop|restart <service>` – Manage services  
- `systemctl enable|disable <service>` – Enable/disable service





<br><br>
# Access Control List:

### Add permission for a user
```
setfacl -m u:<user name>:rwx /path/to/file
```

### Add permission for a group
```
setfacl -m g:<group name>:rwx /path/to/file
```

### To allow permissions for all files or directory recursively
```
setfacl -Rm "entry" /path/to/dir
```

### Show ACL Access
```
getfacl /path/to/file
```

### Remove ACL for a user:
```
setfacl -x u:user /path/to/file
```

### Remove all ACL
```
setfacl -b /path/to/file
```

<br> <br>
# User Account Management:
```
useradd -g <group-name> -s <shell> -c "user description" -m -d <home-directory> <name-of-user>
groupadd <name-of-group>
userdel -r <name-of-user>
usermod -G <name-of-group> <name-of-user>       #add user to a group
chgrp _R <name-of-group> <name-of-user>         #change user to a different group
```
<br> <br>

# Monitor Users
```
who                                     #how many people are logged in
last                                    #show details of all users who been logged in 
last | awk '{print $1}' | sort | uniq   #shows all unique users
w                                       #similiar to who with more details
finger                                  #a program that trace a user
id
```


<br> <br>
# Cut:
```
cut -c1,2 filename      #c=column, show characters
```

<br> <br>
# AWK:
```
awk --version
awk '{print $1}' filename
awk '{print $NF}'               #Last field
awk '{print NF}'                #Number of columns on each line
awk '$3 > 100' file.txt         #Print lines where the third column is greater than 100
```

<br> <br>
# GREP: 
### Find a keyword
```
grep <string name> filename
grep -c <string name> filename      #How many times the string appears
grep -n <string name> filename      #Give line number of match
```


<br> <br>
# EGREP:
### Find two keywords (case-insensitive):
```
egrep -i '<string name>|<string name>' filename
```


<br> <br>
# Sort/Uniq:
```
sort filename
uniq filename
```


<br> <br>
# Word Count:
```
wc -l filename    # Number of lines
wc filename       # (lines, words, bytes)
```

<br> <br>
# Diff: 
```
diff file1 file2        #Compare two files line by line
```


<br> <br>
# CMP: 
```
cmp file1 file2     #Compare two files byte by byte
```

<br> <br>
# TAR: 
### Archive files
```
tar -cvf archive_name.tar file_or_directory
tar -xvf archive_name.tar
```


<br> <br>
# GZIP: 
```
gzip filename               #Compress file  
gzip -d filename.gz         #decompresses file
```


<br> <br>
# Split: 
```
split -l 2 filename new_filename        #Split a file by lines into other files
```


<br> <br>
# SED: 
### Replace a string in a text file

### keys:
- s - subsitute
- g - replace more than one word in global
- d - delete
- '-i' - make changes in file
- '^' - cap anything that starts with
- '$' - anything that ends with

```
sed 's/keyword/keyword-replace/g' filename
sed -i 's/keyword/keyword-replace/g' filename      #-i make changes to file
sed -i '/keyword/d' filename                       #Delete lines containing keyword
sed -i '/^$/d' filename
sed -i '1,2d, filename                             #delete line 1 and 2
sed -i 's/\t/ /g' filename                         #replace all tabs(\t) with a space
sed -i '8!s/keyword/replaced-keyword/'             #dont replace line 8 keyword
```


<br> <br>
# System Utility Commands:
```
date                #give todays date
uptime              #hpw long system been up
hostname            #name of the host machine
uname               #Linux machine name
uname -a            #for more details
which <command>     #location of your command
cal                 #show calendar
cal 9 1977          #shows September 1977
bc                  #binary calculator
```

<br> <br>
# Systemctl: 
### run, enable, disable or stop a service
```
systemctl start|stop|status servicename.service
systemctl enable servicename.service
systemctl restart|reload servicename.service
systemctl list-units --all
```

<br> <br>
# process Status (ps):
```
ps -e               #shows all running processes
ps aux              #shows all running processes in BSD format
ps -ef              #shows all running processes in full format listing
ps -u <username>    #shows all running processes by username
```
<br> <br>
# top
- **PID**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; Shows task's unique process id.
- **USER**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   Username of owner of task.
- **PR**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;&nbsp; The "PR" field shows the scheduling priority of the process from the perpective of the kernel.
- **NI**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; Represents a Nice Value of task. A negative nice value implies higher priority, and positve nice value means lower priority.
- **VIRT**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;Total virtual memory used by the task.
- **RES**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Memory consumed by the process in RAM.
- **SHR**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Represents the amount of shared memory used by a task.
- **S**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;This field shows the process state in the single-letter form.
- **%CPU**&nbsp;&nbsp;&nbsp;&nbsp;Represents the CPU usage.
- **%MEM**&nbsp;&nbsp;&nbsp;&nbsp;Showa the memory usage of task.
- **TIME+**&nbsp;&nbsp;&nbsp;&nbsp; CPU time, the same as 'Time', but reflecting more granularity through hundredths of a second.
```
top
top -u <username>
top then press c    #shows command absolute path
top then press k    #kill a process by PID withhin top session
top then M and P    #to sort all Linux running processes by memory usage
```

<br> <br>
# Kill
```
kill PID
kill -l     #get a list of all process signal names or signal number
kill -1     #restart
kill -2     #interrupt from the keyboard just as CRTL C
kill -9     #Forcefully kill process
kill -15    #Kill a process gracefully
```
<br><br>
# Crontab
```
crontab -e      #edit the crontab
    <minutes 0-59> <hour 0-23> <day of the month 1-31> <month 1-12> <day of the week 0-6 (Sunday - Saturday)> <command to excute>
crontab -l      #list the crontab entries
crontab -r      #remove the crontab
crond           #crontab daemon/service that manages scheduling
systemctl status crond      #to manage the crond service
```

<br><br>
# Process Management
```
Ctrl-z, jobs and bg     #Background
fg                      #Foreground
nohup process &         #Run process even after exit
```