## common commands
```
head foo
head -n 2 foo
tail -f foo

sort: by alphabetic of 1st character
sort -n: by numeric values of 1st character

## show line numbers
$cat -b /etc/passwd  | head
     1	root:x:0:0:root:/root:/bin/bash
     2	bin:x:1:1:bin:/bin:/sbin/nologin
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
     4	adm:x:3:4:adm:/var/adm:/sbin/nologin
     5	lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
     6	sync:x:5:0:sync:/sbin:/bin/sync
     7	shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
     8	halt:x:7:0:halt:/sbin:/sbin/halt
     9	mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
    10	operator:x:11:0:operator:/root:/sbin/nologin
$

## -f: field; -d: delimiter
$cut -f 3 -d : /etc/passwd | head
0
1
2
3
4
5
6
7
8
11
$
```

## grep and regex

- -A5: 5 lines after
- -B5: 5 lines before
- -C5: 5 lines before and after
- -i: ignore case
- -P: pattern
- --color: highlight in color
- -v: exclude
- -R or -r: recursive

```
$grep jordan *
file1:jordan is bad
grep: test2: Is a directory
$grep -R jordan *
file1:jordan is bad
test2/file2:jordan is good
$grep -r jordan *
file1:jordan is bad
test2/file2:jordan is good
```
**enclose regex in single quote**  

repeators  
```
## find jordan where n repeated 0 or more times
$grep 'jordan*' file1 
jordan is goat
jorda is good
jordaaaa is real

## find jordan where n repeat 1 or more times
$grep 'jordan\+' file1 
jordan is goat

## find jordan where n repeat 0 o 1 times
$grep 'jordan\?' file1 
jordan is goat
jorda is good
jordaaaa is real
$

## find jorda where a repeat exactly 4 times
$grep 'jorda\{4\}' file1 
jordaaaa is real
$

```

positions
```
## find lines that begin with kobe
$grep '^kobe' file2 
kobe is great player

## find lines that end with goat
$grep 'goat$' file2
jordan is better goat

## find exact word 
$grep '\<great\>' file2
kobe is great player
$
```

## awk
pls refer to awk section for details

## sed
```
## a very basic example, will do sed after awk
$sed -i s/kobe/KOBE/g file2
$cat file2
KOBE is great player
jordan is better goat

## display 5th line
$sed -n 5p /etc/passwd
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin

$
```
