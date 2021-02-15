
## create path in one go
mkdir -p <path>

## which

## find
```
find / -name "hosts"
find / -type f -size +10M
find / -user tichen
find / -exec grep -i tichen {} \;
find / -exec grep -i tichen {} 2>/dev/null \; -exec cp {} /tmp \; 
```

## locate

## link
```
$ls file*
fileA

## hard link
> inode contains information  
> if 2 file has same inode, they are hard link  
> if 2 files has different inode, they are symlink  
$ln fileA fileB

## symlink
$ln -s fileA fileC

$ll -i file*
100865122 -rw-r--r--. 2 root root 0 Feb 15 10:01 fileA
100865122 -rw-r--r--. 2 root root 0 Feb 15 10:01 fileB
100865123 lrwxrwxrwx. 1 root root 5 Feb 15 10:01 fileC -> fileA
$
```

## tar:reduce number of files
create tar file  
```
$ls
anaconda-ks.cfg  fileA  fileB  fileC  initial-setup-ks.cfg  module-signing
$tar -cvf file.tar file{A,B,C}
fileA
fileB
fileC
$ls
anaconda-ks.cfg  fileA  fileB  fileC  file.tar  initial-setup-ks.cfg  module-signing
```
check tar content
```
$tar -tvf file.tar
-rw-r--r-- root/root         0 2021-02-15 10:01 fileA
hrw-r--r-- root/root         0 2021-02-15 10:01 fileB link to fileA
lrwxrwxrwx root/root         0 2021-02-15 10:01 fileC -> fileA
$
```
extract tar file  
```
$mkdir file
$tar -xvf file.tar -C file
fileA
fileB
fileC
$ls file/
fileA  fileB  fileC
```

## gzip/gunzip: reduce size
create zip  
```
$ll file.tar 
-rw-r--r--. 1 root root 10240 Feb 15 10:05 file.tar
$gzip file.tar 
$ll file.tar.gz 
-rw-r--r--. 1 root root 161 Feb 15 10:05 file.tar.gz
$
```
unzip
```
$gunzip file.tar.gz 
```
