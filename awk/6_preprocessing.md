# if there is BEGIN, "start reading" will only display once at the beginning
```
awk -F: 'BEGIN{print "start reading.."}{print $1 " | " $6}' /etc/passwd | head
start reading..
root | /root
bin | /bin
daemon | /sbin
adm | /var/adm
lp | /var/spool/lpd
sync | /sbin
shutdown | /sbin
halt | /sbin
mail | /var/spool/mail
$
```
# if there is no BEGIN, "start reading" will display after every script execution
```
$awk -F: '{print "start reading.."}{print $1 " | " $6}' /etc/passwd | head
start reading..
root | /root
start reading..
bin | /bin
start reading..
daemon | /sbin
start reading..
adm | /var/adm
start reading..
lp | /var/spool/lpd
$
```
