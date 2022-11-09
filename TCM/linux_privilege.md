# initial enumeration

## system enum

uname -a

cat /proc/version
/etc/issue
lscpu
ps aux
ps aux | grep root

## user enum

whoami
id
sudo -l -> какие команды может пользователь выполнить от  `root`
/etc/passwd

cat /etc/passwd | cut -d : -f 1
cat /etc/shadow
cat /etc/group

history

sudo su -

## network enum

ip a
ip r
ip neigh
netstat -ano

## passwd hanting

find / -name id_rsa 2> /dev/null
locate password | more
grep --color=auto -rnv '/' -ie "PASSWORD=" --color=always 2> /dev/null

## automating tools

[LinPeas](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)

[LinEnum](https://github.com/rebootuser/LinEnum)

[Linux Exploit Suggester](https://github.com/mzet-/linux-exploit-suggester)

[Linux Priv Checker](https://github.com/sleventyeleven/linuxprivchecker)

## kernel exploits

[Kernel Exploits](https://github.com/lucyoa/kernel-exploits)



