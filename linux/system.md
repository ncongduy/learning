## Table of contents
- systemd
- file

----------------------------------------------------------------------
## Contents

- systemd
```bash
# check run level
# 5 => GUI; 3 => CLI
runlevel

# get default
systemctl get-default

# set CLI
systemctl set-default multi-user.target
systemctl set-default graphical.target
```

-file
```bash
# check file type
file <name_of_file>

# file type and identifier
"""
directory           => d
regular file        => -
character device    => c
link                => l 
socket file         => s
pipe                => p 
block device        => b
"""

# viewing file size
du -sh <file_name>
du -h --max-depth=1 .

# archiving files
tar -cf test.tar file1 file2 file3
tar -zcf test.tar file1 file2 file3

# extract files
tar -tf test.tar
tar -xf test.tar

# compressing
bzip2 <file_name> # compress a file from 99M to 4K
gzip <file_name> # compress a file from 99M to 100K
xz <file_name> # compress a file from 99M to 16K

# uncompressing
bunzip2 <file_name>
gunzio <file_name>
unxz <file_name>
```

