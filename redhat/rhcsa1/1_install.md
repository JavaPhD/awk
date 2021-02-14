# 1-Install RedHat

## configure networking to contact a DHCP server
![install-networking](pics/install-networking.png)

## configure partitions
1. select **custom**   
![custom-partition](pics/custom-partition.png)
2. swap partition  
![swap-partition](pics/swap-partition.png)
3. swap partition type  
> filesystem: **swap**  
![swap-type](pics/swap-type.png)
4. root partition  
![root-partition](pics/root-partition.png)
5. root partition type  
> filesystem: **xfs**  
![root-type](pics/root-type.png)
6. swap summary  
![summary-swap](pics/summary-swap.png)
7. root summary  
![summary-root](pics/summary-root.png)
8. partition complete  
![done-partition](pics/done-partition.png)

# 2-Login
> For newly built system, use **su -* to open root shell to add admin into wheel group, then admin can use **sudo -i** to become superuser
## su -
```
## open new shell for root, enter root password
$su -
Password: 
Last failed login: Fri Feb 12 23:04:00 EST 2021 on pts/1
There was 1 failed login attempt since the last successful login.
[root@garyhost ~]# 

```
## sudo -i
```
## as per sudo rule, enter user own password to become superuser
$sudo -i
[sudo] password for tichen: 
$
```
