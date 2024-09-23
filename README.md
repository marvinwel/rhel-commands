
# Access Control List:

1) Add permission for a user:
```
setfacl -m u:<user name>:rwx /path/to/file
```

2) Add permission for a group:
```
setfacl -m g:<group name>:rwx /path/to/file
```

3) To allow permissions for all files or directory recursively:
```
setfacl -Rm "entry" /path/to/dir
```

4) Show ACL Access:
```
getfacl /path/to/file
```

5) Remove ACL for a user:
```
setfacl -x u:user /path/to/file
```

6) Remove all ACL:
```
setfacl -b /path/to/file
```

# Cut:
```
cut -c1,2 filename  # c=column, show characters
```

# AWK:
```
awk --version
awk '{print $1}' filename
awk '{print $NF}'   # Last field
awk '{print NF}'    # Number of columns on each line
```

# GREP: Find a keyword:
```
grep <string name> filename
grep -c <string name> filename  # How many times the string appears
grep -n <string name> filename  # Give line number of match
```

# EGREP: Find two keywords (case-insensitive):
```
egrep -i '<string name>|<string name>' filename
```

# Sort/Uniq:
```
sort filename
uniq filename
```

# Word Count (wc):
```
wc -l filename    # Number of lines
wc filename       # (lines, words, bytes)
```

# Diff: Compare two files line by line:
```
diff file1 file2
```

# CMP: Compare two files byte by byte:
```
cmp file1 file2
```

# TAR: Archive files:
```
tar -cvf archive_name.tar file_or_directory
tar -xvf archive_name.tar
```

# GZIP: Compress and uncompress files:
```
gzip filename
gzip -d filename.gz
```

# Split: Split a file by lines into other files:
```
split -l 2 filename new_filename
```

# Linux File Editors:
- vi
- ed
- ex
- emacs
- pico
- vim

# SED: Replace a string in a text file:
```
sed -i 's/keyword/keyword-replace/g' filename
sed -i '/keyword/d' filename  # Delete lines containing keyword
```
