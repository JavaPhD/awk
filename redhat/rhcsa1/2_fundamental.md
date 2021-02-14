# 1-command

```
## these are too simple
pwd
whoami
ls
ip addr show
free -m
df -h
cat /etc/hosts
findmnt
```
# 2-BASH
## history
```
## press ctrl+r
(reverse-i-search)`': 

## press keyword you want search, this will search history in reverse order
(reverse-i-search)`df': df -h

## press ENTER
$df -h
Filesystem                        Size  Used Avail Use% Mounted on
devtmpfs                          5.7G     0  5.7G   0% /dev
tmpfs                             5.7G  236M  5.5G   5% /dev/shm
tmpfs                             5.7G   19M  5.7G   1% /run
tmpfs                             5.7G     0  5.7G   0% /sys/fs/cgroup
/dev/mapper/centos_garyhost-root   50G  8.2G   42G  17% /
/dev/loop2                         75M   75M     0 100% /var/lib/snapd/snap/p3x-onenote/97
/dev/loop0                        163M  163M     0 100% /var/lib/snapd/snap/gnome-3-28-1804/145
/dev/loop1                         56M   56M     0 100% /var/lib/snapd/snap/core18/1944
/dev/loop5                         32M   32M     0 100% /var/lib/snapd/snap/snapd/10707
/dev/loop3                         98M   98M     0 100% /var/lib/snapd/snap/core/10583
/dev/nvme0n1p2                   1014M  225M  790M  23% /boot
/dev/loop4                         65M   65M     0 100% /var/lib/snapd/snap/gtk-common-themes/1514
/dev/nvme0n1p1                    200M   12M  189M   6% /boot/efi
/dev/mapper/centos_garyhost-home   63G   11G   52G  17% /home
tmpfs                             1.2G   64K  1.2G   1% /run/user/1000
$
```
## pipe
```
$ps aux | less
```
## redirection
```
## >: redirect output
$ps aux > process.txt

## >>: append
$echo 'hello' >> err.txt 
$tail -n 1 err.txt 
hello
$

## 2>xxx redirect error
$ls $%^^ 2>err.txt 
$cat err.txt 
ls: cannot access $%^^: No such file or directory
$
```
## environment variables
```
$env | head
XDG_VTNR=1
SSH_AGENT_PID=5643
XDG_SESSION_ID=1
HOSTNAME=garyhost
IMSETTINGS_INTEGRATE_DESKTOP=yes
VTE_VERSION=5204
TERM=xterm-256color
SHELL=/bin/bash
XDG_MENU_PREFIX=gnome-
HISTSIZE=1000
$
```
## alias
```
$alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias vi='vim'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
$
```

# 3-IO Redirection and Piping
|name| file descriptor | abbr | notes |
|---|---|---|---|
|standard input|0|stdin|non standard input: <|
|standard output|1|stdout|> <br /> >>|
|standard error|2|stderr|non standard error: 2>/dev/null|

# 4-File System Hierarchy
- /: root directory
- /root: home directory of user root, a sub directory under /
- /proc: contains very accurate system information such as mount, partitions,meminfo etc
- /boot: boot up
- /dev: communicate with other devices
- /etc: configurations and readable
- /home: home directory
- /usr: binaries, bin for system binaries, sbin for system binaries
- /var: log

# 5-man
## chapters
> search **description** in man manpage
```
ESCRIPTION
       man is the system's manual pager. Each page argument given to man is normally the name of a program, utility or function.  The manual page associated with each of these arguments is then  found  and
       displayed. A section, if provided, will direct man to look only in that section of the manual.  The default action is to search in all of the available sections, following a pre-defined order and to
       show only the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```
> search **example** in any man page for sample usage  
options:
```
man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular expression.  Print out any matches.  Equivalent to apropos -r printf.
```
> looking fo man page to reset password as a system admin
```
$man -k password | grep 8
chgpasswd (8)        - update group passwords in batch mode
chpasswd (8)         - update passwords in batch mode
cracklib-check (8)   - Check passwords using libcrack2
create-cracklib-dict (8) - Check passwords using libcrack2
grpconv (8)          - convert to and from shadow passwords and groups
grpunconv (8)        - convert to and from shadow passwords and groups
grub2-setpassword (8) - Generate the user.cfg file containing the hashed grub bootloader password.
pam_cracklib (8)     - PAM module to check the password against dictionary words
pam_pwhistory (8)    - PAM module to remember last passwords
pam_pwquality (8)    - PAM module to perform password quality checking
pam_unix (8)         - Module for traditional password authentication
password-auth-ac (5) - Common configuration files for PAMified services written by authconfig(8)
pwck (8)             - verify integrity of password files
pwconv (8)           - convert to and from shadow passwords and groups
pwhistory_helper (8) - Helper binary that transfers password hashes from passwd or shadow to opasswd
pwunconv (8)         - convert to and from shadow passwords and groups
saslpasswd2 (8)      - set a user's sasl password
systemd-ask-password-console.path (8) - Query the user for system passwords on the console and via wall
systemd-ask-password-console.service (8) - Query the user for system passwords on the console and via wall
systemd-ask-password-wall.path (8) - Query the user for system passwords on the console and via wall
systemd-ask-password-wall.service (8) - Query the user for system passwords on the console and via wall
unix_chkpwd (8)      - Helper binary that verifies the password of the current user
unix_update (8)      - Helper binary that updates the password of a given user
vigr (8)             - edit the password, group, shadow-password or shadow-group file
vipw (8)             - edit the password, group, shadow-password or shadow-group file
$
```
## how to read options
- without any below: mandatory
- |: or
- UPPER CASE: pls replace this with something else
- ...: it means you can have more than one option
- []: optional
- Size[m|UNIT]: this is size, either in MB or other UNIT

**example:**
```
lvcreate -L|--size Size[m|UNIT] VG
           [ -l|--extents Number[PERCENT] ]
           [    --type linear ]
           [ COMMON_OPTIONS ]
           [ PV ... ]
```	
> this means lvcreate, either -L or --size, size in MB or other unit, VG. For example: lvcreate -L 10GB data001  
> optionally, you might add -l or --extents with a percentage number  
> optionally, you might add --type linear  
> optionally you might add other common options  
> optionally you might add PV as well  

# 6-vim

## options
- Esc
- i: insert mode
- v: visual mode
- O: insert newline above
- o: insert newline below
- :wq: save and exist
- :q!: unsave and exist
- dd: cut a line, or use SHIFT+v and d
- yy: copy a line, or use SHIFT+v and y
- gg: go to begining of file
- G: go to end of file
- ^: go to begining of a line
- $: go to end of a line
- p:  paste from dd, yy and its alternative approach
- u: undo
- ctrl+r: revert
- /text: search text top to bottom
- ?text: search text bottom to top
- %s/old/new/g: replace old with new

# 7-Globbing and Wildcards 
|name|character|number of characters|
|---|---|---|
|*|any|any|
|?|any|1|
|[hm]|h or m|1|
|[!hm]|not h nor m|1|
|[0-9]|0 to 9|1|

