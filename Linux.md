

# Linux Commands

#### Linux system

##### init

CPU reset  - Firmware Loader - Kernel_start() - '/bin/init' - termi/exception handle

pstree

##### fork

create a state machine

##### execve

reset a state machine(argv, envp)

execve("/bin/bash", "-c", "env", NULL)

##### exit

destroy state machine

exit(0): atexit

_exit(0): exit_group

syscall(SYS_exit, 0): terminate the current thread

##### xeyes

##### strace

--observe program running

gcc strace

#### .bashrc

```
# FORMAT
HISTTIMEFORMAT="%Y-%M-%D %T"

# GO ENV
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin
# Go 1.16 requires use of Go modules by default, to still allow working as before
#export GO111MODULE=off
export GO111MODULE=on
#export GOFLAGS=-mod=readonly
export GOFLAGS=-mod=mod
#export GOFLAGS=-mod=vendor

# solc
PATH=$PATH:~/.local/bin
# solana
export PATH="/home/tianwen/.local/share/solana/install/active_release/bin:$PATH"

# My alias:
alias cdmy="cd $HOME/go/src/github.com/wtwinlab && ll"

. "$HOME/.cargo/env"

```



#### System version

```
lsb_release -a
```

```
lspci
ls --color
ls -l --color
```

#### Reboot

shutdown command is specify a time of shutdown/reboot,

reboot at 1:30pm 

```
sudo shutdown -r 13:30
```

to reboot in 40 minutes

```
sudo shutdown -r +40
```

#### Debugfs

```
debugfs /dev/hda2
```

#### Exploit

```
exploit
```

#### Task_struct

```
task_struct
tasks
```

#### Rookit

```

```

ava

```

```



#### Tips

```
history
!number (history command id)
!!

Ctrl -
Ctrl shift +
Ctrl l (=clear)

Ctrl+Z
fg
pushd
popd

truncate s 0 filename # empty file
some output | column -t # display output in col
tail -f -n 50 filename

cmd1 && cmd2
cmd1; cmd2
```

brew

```
git clone https://github.com/Homebrew/linuxbrew.git ~/.linuxbrew

export PATH="$HOME/.linuxbrew/bin:$PATH"
export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"
export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"
```

#### 

#### DNS/Gateway

```
# DNS servers
systemd-resolve --status
# Gateway, default route
ip r | grep ^def
# ip, netmask
ifconfig


#192.168.50.1, 
ping 8.8.8.8
#DNS 8.8.8.8,8.8.4.4
# restart
sudo service NetworkManager restart
# Unit network-manager.service not found.
sudo apt install network-manager

#!!!!!!!
sudo cp resolv.conf.forticlient.backup resolv.conf

# nslookup
nslookup 172.25.121.135
host 172.25.121.135
dig -x 172.25.121.135

ipconfig /flushdns

```

r-24-123-25-172.d1.comp.nus.edu.sg

remove "resolvconf" and then install:

```
sudo apt-get remove --purge resolvconf && sudo apt-get install resolvconf

systemd-resolve --status
vim /etc/resolv.conf

systemctl restart resolvconf
resolvectl status
sudo iptables -I INPUT -s localhost -d 127.0.0.53 -j ACCEPT
```

To release the current IP address:

```
$ sudo dhclient -r
```

To obtain a fresh lease:

```
$ sudo dhclient 
```



```
sudo ifconfig wlp9s0 down

sudo ifconfig wlp9s0 up
```



```
netstat -rn


> Kernel IP routing table

> Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

> 0.0.0.0         172.26.186.1    0.0.0.0         UG        0 0          0 enp0s31f6

> 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 enp0s31f6

> 172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0

> 172.18.0.0      0.0.0.0         255.255.0.0     U         0 0          0 br-59a163f3f807

> 172.26.186.0    0.0.0.0         255.255.254.0   U         0 0          0 enp0s31f6

> 192.168.20.0    0.0.0.0         255.255.255.0   U         0 0          0 ovs-br1


172.18.0.0 subnet that clashes with our DNS.
Note that 172.16.0.0/12 is routeable in N. 
192.168.0.0/16 is also routeable in S. 
Do not use these subnets.

```

###### delete default route

```
sudo ip route del default
```

#### iptable

```
ip addr show enp0s3

ip route show

ip route list

route -n 
```

###### ip route del

```
sudo ip route del 172.18.0.0/16
sudo ip route del default
sudo ip route del 10.0.2.15 via 192.168.43.223 dev enp0s3
```

###### ifdown & ifup

```
sudo ifdown enp0s3 && sudo ifup enp0s3
```

add iproute2 to image and expose net capability

```
#Dockerfile
RUN apk add iproute2
```

#### telnet

```
telnet 172.25.123.120 7070

```



#### netstat

```
netstat -tlnup | grep -i 3306
```



#### Ping

ping -c 1 192.168.20.3

ip link show

ip r s

#### check listening port ####

`$ ps auxww`

`$ ps aux | grep` 

`$ ps [pid]`

`$ ps -M [pid]`

`$ ps aufx | less -S`

`$ ps -ef | grep bitcoind`

`$ ps -aef --forest`

`$ lsof -i`

`$ lsof -i tcp:3000`

`$ sudo lsof -i:9092`

`$ sudo netstat -ntupl | grep :443`

`$ lscpu`

`$ ss -t`

`$ netstat -l`

`$ netstat -vatn`

`$ netstat -vaun`

`$ netstat -nap    # see all listening ports of the server`

`netstat -nlp|grep 2181`

`$ netstat -tanp | grep -w 8333`

`$ nslookup bitseed.xf2.org`

`$ netstat -ao | find "8443"`

`$ nc localhost 5500`

```
ls /proc | less 
```

Lsof obtains data about open UNIX dialect files by reading the kernel's proc structure information, following it to the related user structure, then reading the open file structures stored (usually) in the user structure. Typically lsof uses the kernel memory devices, /dev/kmem, /dev/mem, etc. to read kernel data.

#### ps

```
pstree

ps -Flww -p 1700

pidstat -p 101754 -d 
pidstat -p 101754 3

cd /proc/1700
ls
cat /proc/1700/status
```

#### Kill ps

Getting right process IDs with:

```sh
pgrep -f [part_of_a_command_name]
```

If the result is as expected. Go with:

```sh
pkill -f [part_of_a_command_name]
```

`$ killall -9 command`



#### Run background

```
nuhup ./script.sh &
```

```
nohup [command] & disown
```

#### Exit Kill

kill background jobs, you can add this line to shell script.

```sh
trap 'kill $(jobs -p)' EXIT
```

```sh
trap "trap - SIGTERM && kill -- -$$" SIGINT SIGTERM EXIT
```

- `kill -- -$$` sends a [SIGTERM](http://www.opengroup.org/onlinepubs/009695399/functions/kill.html) to the whole process group, thus killing also descendants.
- Specifying signal `EXIT` is useful when using `set -e` 

#### Use set -e

Every script you write should include set -e at the top. This tells bash that it should exit the script if any statement returns a non-true return value. The benefit of using -e is that it prevents errors snowballing into serious issues when they could have been caught earlier. Again, for readability you may want to use set -o errexit.

Using -e gives you error checking for free. If you forget to check something, bash will do it or you. Unfortunately it means you can’t check $? as bash will never get to the checking code if it isn’t zero. There are other constructs you could use:

```
command || { echo "command failed"; exit 1; }
```

or

```
set +e
command1
command2
set -e
```

- set -e: exits if a command fails
- set -u: errors if an variable is referenced before being set
- set -x: shows the commands that get run

#### WC

count lines of output

```sh
wc -l
```

#### printf

line buffer: \n

full buffer (page): pipeline

cash

setbuf(stdout, NULL)

wait(NULL)

#### Mem ####

`$ top`

`$ htop`

`pwdx 命令根据 pid 找到业务进程路径，进而定位到负责人和项目`

`dmesg -T | grep 'Out of memory'`

`$ vmstat -s #cat /proc/meminfo`

`$ sudo -i`

`$ chmod -R +w,g=rw,o-rw,` 

`#drwxrwsrwx`

`$ chmod -R 2777 trading-system.git/`

`$ mv old_name new_name #rename a file or directory

`$ sudo apt-get -q -y -f build-dep` 

`$ sudo gparted`

`$ sudo fdisk -l`

#### Disk usage

```
df -h

du -h

du -hd 1
```



#### indicator
$ sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
$ sudo apt-get update
$ sudo apt-get install indicator-sysmonitor



#### parse filename ####

We can use these expressions:
path = ${foo%/*}
To get: /tmp/my.dir (like dirname)
file = ${foo##*/}
To get: filename.tar.gz (like basename)
base = ${file%%.*}
To get: filename
ext = ${file#*.}
To get: tar.gz



#### search ####
`$ sudo find / -name 'gnutls.h'`

`$ find . -type f -exec grep 8333 {} \; -print`

`$ find / -name "gradle" 2> /dev/null`

`$ which gradle`

`$ locate`

`$ grep -R 'getblocks' .`

`$ grep -F 'getblocks' **/*.cpp`

`$ tree -d crypto-config`



#### regex ####

[[ $string =~ "My s" ]]

[0-9]+    

[[:digit:]]+



#### curl ####
`$ curl --connect-timeout ${timeout} -sS .... 2>>${reportmsg}` 

`$ time curl -w 'whatismyip.org' | grep "Your IP Address" -a3`

`$ wget`



#### no-pass

```
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER
```



#### sed

###### Replace a line

sed -i '/protected-mode yes/c protected-mode no' test.txt 

###### Insert after a line

sed -i '/protected-mode yes/a protected-mode no' /etc/redis/redis.conf

###### Comment a line

sed -i '/^bind 127\.0\.0\.1 ::1$/s/^/#/' /etc/redis/redis.conf



#### less

```
# go to the end of the file
less -G file
```



#### shutdown

```
sudo shutdown -P now
sudo poweroff
sudo halt
```



#### pipe-max-size

id

id -u

location for tmpfs

/dev/shm

vim /proc/sys/fs/pipe-max-size


####  git 

git remote update

git status -uno

//remember pass

$ git config credential.helper store

git config --global credential.helper 'cache --timeout 7200'



####  vim 

:set number

:s/^/new text /	Insert "new text " at the beginning of the line.

:s/$/ new text/	Append " new text" to the end of the line.



####  port 

netstat -tulnp | grep <port no>

lsof -i:3000

netstat -ptn | grep EST | wc -l

netstat -n | grep -i 7051 | grep -i time_wait | wc -l

sudo tar -xvf go1.10.1.linux-amd64.tar.gz

sudo mv go /usr/local

export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH



#### cron job 

0 1 ? * MON-FRI *

####  letsencrypt 

sudo apt-get install letsencrypt

sudo -H ./letsencrypt-auto certonly --standalone -d server2.freeddns.org -d www.server2.freeddns.org

sudo -H ./letsencrypt-auto certonly --standalone -d 1n6.ddnsfree.com -d www.1n6.ddnsfree.com

sudo wget https://dl.eff.org/certbot-auto -O /usr/sbin/certbot-auto

sudo certbot-auto certonly --standalone -d 1n6.ddnsfree.com -d www.1n6.ddnsfree.com

sudo mkdir -p /etc/hyperledger/certs

sudo cp /etc/letsencrypt/live/1n6.ddnsfree.com/fullchain.pem /etc/hyperledger/certs/server.pem

sudo cp /etc/letsencrypt/live/1n6.ddnsfree.com/privkey.pem /etc/hyperledger/certs/server.key

sudo chmod a+r /etc/hyperledger/certs/server.key

sudo chown -R ubuntu.ubuntu certs



#### Tools

wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

which python

export PATH=~/.local/bin:$PATH

 mkdir -p go/src/github.com/project

~/go/src/github.com/project$ ln -s ~/projects/db/src/sdk/go ./db-sdk-go




####  pattern match
```
if [[ $SINGLE_NODE =~ peer([[:digit:]]+).org([[:digit:]]+) ]]; then
​    peer_single="${BASH_REMATCH[1]}"
​    org_single="${BASH_REMATCH[2]}"

```



#### ssh

genrate keypairs

```
ssh-keygen
ssh-keygen -t rsa -b 2048
ls ~/.ssh/
```

sudo scp -i ~/.ssh/id_rsa index.html console.css console.js ubuntu@node:/home/ubuntu/projects/src//public/
ssh ubuntu@node -v ##debug

--delete

install ssh

```
sudo apt install openssh-server 
sudo service ssh status 
ssh localhost
ssh -v tianwen@enigma.d2.comp.nus.edu.sg
```

###### To Fix: 

kex_exchange_identification: read: Connection reset by peer

```
sudo ufw allow ssh
sudo ufw allow 22
```

###### ssh with password

```
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no enigma.d2.comp.nus.edu.sg
```



####  gen rsa 

openssl genrsa -out private.pem 4096

openssl rsa -in private.pem -outform PEM -pubout -out public.pem

	publicKeyPem := []byte(`-----BEGIN PUBLIC KEY-----
	-----END PUBLIC KEY-----`)


####  vgo

export GOPATH=$HOME/go

export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin

source ~/.profile
	

#### file discriptor test

ulimit -n 20480

go run tps.go put https://localhost:8080/api/v1 1450 200



####  api-gateway

sudo pkill api-gateway

touch /etc/blockchain/debug exists

----config.user.sh
export PG_CLIENT_CONN_POOL_SIZE=400
export PG_LOG_LEVEL=debug



#### lockfile

sudo apt-get install procmail

#### jq

sudo apt install jq

#### softlink

ln -s /home/ubuntu/testspace/src/sdk/go/ sdk-go



#### python3-pip

sudo apt-get install python3-pip python-pip

pip install pycrypto

pip3 install pycrypto

sudo pip install selenium

sudo pip3 install selenium

pip3 install requests



#### test deploy

sudo systemctl status apache2

sudo apt install php libapache2-mod-php

sudo apt-get install apache2

sudo service apache2 restart

/etc/apache2/

sudo a2enmod ssl

sudo systemctl restart apache2

sudo mkdir /etc/apache2/ssl

To disable apache2 simply type: 

sudo update-rc.d apache2 disable

To remove apache2 simply type:

sudo update-rc.d -f  apache2 remove

