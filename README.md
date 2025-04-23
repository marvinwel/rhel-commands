# Table of Contents
- [Access Control List](#Access-Control-List)  
- [User Account Management](#User-Account-Management)
- [Monitor Users](#Monitor-Users)
- [Cut](#Cut)
- [AWK](#awk)
- [GREP](#GREP)
- [EGREP](#EGREP)
- [Sort/Uniq](#Sort/Uniq)
- [Word Count](#Word Count)


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
groupadd name-of-group
userdel -r <name of user>
usermod -G <name of group> <name of user> #add user to a group
chgrp _R <name of group> <name of user> #change user to a different group
```
<br> <br>

# Monitor Users
```
who  #how many people are logged in
last #show details of all users who been logged in 
last | awk '{print $1}' | sort | uniq  #shows all unique users
w   #similiar to who with more details
finger  #a program that trace a user
id
```


<br> <br>
# Cut:
```
cut -c1,2 filename  # c=column, show characters
```

<br> <br>
# AWK:
```
awk --version
awk '{print $1}' filename
awk '{print $NF}'        # Last field
awk '{print NF}'         # Number of columns on each line
awk '$3 > 100' file.txt  #Print lines where the third column is greater than 100
```

<br> <br>
# GREP: 
### Find a keyword
```
grep <string name> filename
grep -c <string name> filename  # How many times the string appears
grep -n <string name> filename  # Give line number of match
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
# Diff: Compare two files line by line:
```
diff file1 file2
```


<br> <br>
# CMP: Compare two files byte by byte:
```
cmp file1 file2
```

<br> <br>
# TAR: Archive files:
```
tar -cvf archive_name.tar file_or_directory
tar -xvf archive_name.tar
```


<br> <br>
# GZIP: Compress and uncompress files:
```
gzip filename
gzip -d filename.gz
```


<br> <br>
# Split: Split a file by lines into other files:
```
split -l 2 filename new_filename
```


<br> <br>
# SED: Replace a string in a text file:

### keys:
- s - subsitute
- g - replace more than one word in global
- d - delete
- '-i' - make changes in file
- '^' - cap anything that starts with
- '$' - anything that ends with

```
sed 's/keyword/keyword-replace/g' filename
sed -i 's/keyword/keyword-replace/g' filename  #-i make changes to file
sed -i '/keyword/d' filename  # Delete lines containing keyword
sed -i '/^$/d' filename
sed -i '1,2d, filename  #delete line 1 and 2
sed -i 's/\t/ /g' filename  #replace all tabs(\t) with a space
sed -i '8!s/keyword/replaced-keyword/' #dont replace line 8 keyword
```


<br> <br>
# System Utility Commands:
```
date - give todays date
uptime - hpw long system been up
hostname - name of the host machine
uname - Linux machine name
uname -a - for more details
which <command> - location of your command
cal - show calendar
cal 9 1977 - shows September 1977
bc - binary calculator
```

<br> <br>
# Systemctl: run, enable, disable or stop a service
```
systemctl start|stop|status servicename.service
systemctl enable servicename.service
systemctl restart|reload servicename.service
systemctl list-units --all
```

<br> <br>