# vertica install on AWS
## connect to AWS instance
### chmod 400 vertica.pem
### ssh -i "vertica.pem" ec2-user@[ec2instance].[region].compute.amazonaws.com
### e.g. ssh -i "vertica.pem" ec2-user@ec2-13-231-154-234.ap-northeast-1.compute.amazonaws.com

## create mount point for vertica
### [ec2-user@ip-172-31-42-217 /]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       10G  925M  9.1G  10% /
devtmpfs        474M     0  474M   0% /dev
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           496M   13M  483M   3% /run
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/0
tmpfs           100M     0  100M   0% /run/user/1000

### [ec2-user@ip-172-31-42-217 /]$ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk 
|-xvda1 202:1    0   1M  0 part 
`-xvda2 202:2    0  10G  0 part /
xvdb    202:16   0  20G  0 disk 

### [ec2-user@ip-172-31-42-217 /]$ sudo mkdir /vertica
### [ec2-user@ip-172-31-42-217 /]$ sudo mkfs -t ext4 /dev/xvdb
### [ec2-user@ip-172-31-42-217 /]$ sudo mount /dev/xvdb /vertica
### [ec2-user@ip-172-31-42-217 /]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       10G  925M  9.1G  10% /
devtmpfs        474M     0  474M   0% /dev
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           496M   13M  483M   3% /run
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/0
tmpfs           100M     0  100M   0% /run/user/1000
/dev/xvdb        20G   45M   19G   1% /vertica

### 

