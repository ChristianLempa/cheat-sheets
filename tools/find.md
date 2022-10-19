---
tags:
    - search
    - file
    - directory
categories:
    - commands
---

# Find

## Usage

```bash
find [path...] [options] [expression]
```

Wildcard
```bash
find . -name "*.txt"
find . -name "2020*.csv"
find . -name "json_*"
```

----
- [Regex reference](../linux/regex.md)
- [Find cheatsheet](https://gist.github.com/gr1ev0us/3a9b9d9dbdd38f6379288eb2686fc538) _(gist.github.com)_

## Example options
| Option      | Example                                     | Description                                 |
|-------------|---------------------------------------------|---------------------------------------------|
| `-type`     | `find . -type d`                            | Find only directories                       |
| `-name`     | `find . -type f -name "*.txt"`              | Find file by name                           |
| `-iname`    | `find . -type f -iname "hello"`             | Find file by name (case-insensitive)        |
| `-size`     | `find . -size +1G`                          | Find files larger than 1G                   |
| `-user`     | `find . -type d -user jack`                 | Find jack's file                            |
| `-regex`    | `find /var -regex '.\*/tmp/.\*[0-9]*.file'` | Using Regex with find. See [regex](../linux/regex.md)  |
| `-maxdepth` | `find . -maxdepth 1 -name "a.txt"`          | In the current directory and subdirectories |
| `-mindepth` | `find / -mindepth 3 -maxdepth 5 -name pass` | Between sub-directory level 2 and 4         |

### Type
|           |                      |
|-----------|----------------------|
| `-type d` | Directory            |
| `-type f` | File                 |
| `-type l` | Symbolic link        |
| `-type b` | Buffered block       |
| `-type c` | Unbuffered character |
| `-type p` | Named pipe           |
| `-type s` | Socket               |


### Size
|           |                           |
|-----------|---------------------------|
| `-size b` | 512-byte blocks (default) |
| `-size c` | Bytes                     |
| `-size k` | Kilobytes                 |
| `-size M` | Megabytes                 |
| `-size G` | Gigabytes                 |
| `-size T` | Terabytes _(only BSD)_    |
| `-size P` | Petabytes _(only BSD)_    |

### Size +/-

Find all bigger than 10MB files
```bash
find / -size +10M
```

Find all smaller than 10MB files
```bash
find / -size -10M
````

Find all files that are exactly 10M
```bash
find / -size 10M
```

Find Size between 100MB and 1GB
```bash
find / -size +100M -size -1G
```

The `+` and `-` prefixes signify greater than and less than, as usual.


### Names

Find files using name in current directory
```bash
find . -name tecmint.txt
```

Find files under home directory

```bash
find /home -name tecmint.txt
```

Find files using name and ignoring case
```bash
find /home -iname tecmint.txt
```

Find directories using name
```bash
find / -type d -name tecmint
```

Find php files using name
```bash
find . -type f -name tecmint.php
```

Find all php files in directory
```bash
find . -type f -name "*.php"
```


### Permissions

Find the files whose permissions are 777.

```bash
find . -type f -perm 0777 -print
```

Find the files without permission 777.

```bash
find / -type f ! -perm 777
```

Find SUID set files.

```bash
find / -perm /u=s
```

Find SGID set files.

```bash
find / -perm /g=s
```

Find Read Only files.

```bash
find / -perm /u=r
```

Find Executable files.

```bash
find / -perm /a=x
```


### Owners and Groups

Find single file based on user
```bash
find / -user root -name tecmint.txt
```
Find all files based on user
```bash
find /home -user tecmint
```
Find all files based on group
```bash
find /home -group developer
```
Find particular files of user
```bash
find /home -user tecmint -iname "*.txt"
```


### Multiple filenames
```bash
find . -type f \( -name "*.sh" -o -name "*.txt" \)
```
Find files with `.sh` and `.txt` extensions


### Multiple dirs


```bash
find /opt /usr /var -name foo.scala -type f
```
Find files with multiple dirs


### Empty
```bash
find . -type d -empty
```

Delete all empty files in a directory
```bash
find . -type f -empty -delete
```


## Find Date and Time

### Means
| Option  | Description                                                     |
|---------|-----------------------------------------------------------------|
| `atime` | access time (last time file <yel>opened</yel>)                  |
| `mtime` | modified time (last time file <yel>contents was modified</yel>) |
| `ctime` | changed time (last time file <yel>inode was changed</yel>)      |
#### Example
| Option          | Description                                                |
|-----------------|------------------------------------------------------------|
| `-mtime +0`     | Modified greater than 24 hours ago                         |
| `-mtime 0`      | Modified between now and 1 day ago                         |
| `-mtime -1`     | Modified less than 1 day ago (same as `-mtime 0`)          |
| `-mtime 1`      | Modified between 24 and 48 hours ago                       |
| `-mtime +1`     | Modified more than 48 hours ago                            |
| `-mtime +1w`    | Last modified more than 1 week ago                         |
| `-atime 0`      | Last accessed between now and 24 hours ago                 |
| `-atime +0`     | Accessed more than 24 hours ago                            |
| `-atime 1`      | Accessed between 24 and 48 hours ago                       |
| `-atime +1`     | Accessed more than 48 hours ago                            |
| `-atime -1`     | Accessed less than 24 hours ago (same as `-atime 0`)       |
| `-ctime -6h30m` | File status changed within the last 6 hours and 30 minutes |


### Examples
 Find last 50 days modified files
```bash
find / -mtime 50
```
 find last 50 days accessed files
```bash
find / -atime 50
```
 find last 50-100 days modified files
```bash
find / -mtime +50 –mtime -100
```
 find changed files in last 1 hour
```bash
find / -cmin -60
```
 find modified files in last 1 hour
```bash
find / -mmin -60
```
 find accessed files in last 1 hour
```bash
find / -amin -60
```


## Find and

### Find and delete

Find and remove multiple files

```bash
find . -type f -name "*.mp3" -exec rm -f {} \;
```

Find and remove single file

```bash
find . -type f -name "tecmint.txt" -exec rm -f {} \;
```


Find and delete 100mb files
```bash
find / -type f -size +100m -exec rm -f {} \;
```

Find specific files and delete
```bash
find / -type f -name *.mp3 -size +10m -exec rm {} \;
```

### Find and replace

```bash
find ./ -type f -exec sed -i 's/find/replace/g' {} \;
find ./ -type f -readable -writable -exec sed -i "s/old/new/g" {} \;
```
See also: [sed](../linux/sed.md) command


### Find and rename
```bash
find . -type f -name 'file*' -exec mv {} {}_renamed \;
find . -type f -name 'file*' -exec sh -c 'x="{}"; mv "$x" "${x}.bak"' \;
```

### Find and move
```bash
find . -name '*.mp3' -exec mv {} /tmp/music \;
```
Find and move it to a specific directory

### Find and copy
```bash
find . -name '*2020*.xml' -exec cp -r "{}" /tmp/backup \;
```
Find and copy it to a specific directory

### Find and concatenate 

```bash
find download -type f -iname '*.csv' | xargs cat > merged.csv
find download -type f -name '*.gz' -exec cat {} \; > output
```

### Find and sort

```bash
find . -printf "%T+\t%p\n" | sort
find . -printf "%T+\t%p\n" | sort -r
```

### Find with spaces in filenames or directories

The `find` command was not originally intended to work with spaces
in filenames or directory names. It has been revised to do so provided
the `-print0` command line option is supplied. This option to `find`
can be used in conjunction with the `-0` option to `xargs`. For example:

```bash
find . -type f -name "*.java" -print0 | xargs -0 tar cvf myfile.tar
```

### Find and chmod

Find files and set permissions to 644.

```bash
find / -type f -perm 0777 -print -exec chmod 644 {} \;
```

Find directories and set permissions to 755.

```bash
find / -type d -perm 777 -print -exec chmod 755 {} \;
```


### Find and tar
```bash
find . -type f -name "*.java" | xargs tar cvf myfile.tar
find . -type f -name "*.java" | xargs tar rvf myfile.tar
```


