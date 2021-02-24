## Architecture

user, through permissions, acess kernel space, then drivers, then hardware  
process, through syscall, access kernel space, then drivers, then hardware  
root user, directory access kernel space, then drivers, then hardware  


shell (permission for user, process and root user) enable access to kernel,driver and hardware  

You may login through  
- GUI
- console
- virtual terminals (e.g. PuTTY)

## terminals

In old days, arrive at datacenter, plugin a cable and use terminal (i.e. keyboard+monitor) to access the server.  

Nowdays, use virtual terminals.  

terminal is a device which access server /dev/tty  

**toggle between terminals**  
- method 1: ctl+alt+(Fn)+F1/F2/F3....
- method 2: as root, chvt 1/2/3...

**pts,tty and :0**  
- :0: the full GUI
- pts: ssh connection or telnet connection, just remb those are pseudo
- tty: direct connect, like console


## su
- su -: enter the password for root
- sudo -i: enter the password for your account

**sudo rules**  
- %: group
- +: netgroup
- : the actual user id or hostname

```
root	ALL=(ALL) 	ALL
%wheel	ALL=(ALL)	ALL
```

## ssh

```
$ll .ssh/
total 16
-rw-r--r--. 1 tichen tichen  397 Feb 24 08:05 authorized_keys <-- store public keys for passwordless login
-rw-------. 1 tichen tichen 1679 Jan 29 02:13 id_rsa <-- private key
-rw-r--r--. 1 tichen tichen  397 Jan 29 02:13 id_rsa.pub <-- public key
-rw-r--r--. 1 tichen tichen 1368 Feb 24 07:53 known_hosts <-- store host key after initial connection
```


