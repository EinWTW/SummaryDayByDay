

# Linux Commands

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

#### Kill ps

Getting right process IDs with:

```sh
pgrep -f [part_of_a_command_name]
```

If the result is as expected. Go with:

```sh
pkill -f [part_of_a_command_name]
```

`$ kill -9 pid`

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

#### WC

count lines of output

```sh
wc -l
```

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

`$ mv old_name new_name #rename a file or directory`
`$ sudo apt-get -q -y -f build-dep` 

`$ sudo gparted`
`$ sudo fdisk -l`



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







#################### ssh AWS ###################
ssh-keygen -t rsa -b 2048
ls ~/.ssh/
sudo shutdown -P now
sudo poweroff
sudo halt

ssh ubuntu@1n10.node.digital-transaction.org
sudo scp -i ~/.ssh/id_rsa index.html console.css console.js ubuntu@1n10.node.digital-transaction.org:/home/ubuntu/projects/aidb/src/aidb-console/public/
ssh ubuntu@103.11.89.179 -v ##debug
ssh ubuntu@peer0.org1.dtl1.aidb.digital-transaction.org

--delete
##################### gen rsa ##########################
openssl genrsa -out private.pem 4096
openssl rsa -in private.pem -outform PEM -pubout -out public.pem

	publicKeyPem := []byte(`-----BEGIN PUBLIC KEY-----

MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAy8k7sgUlv2n7FVJtn+sX
38CYYRSpahVGkS43JyMuRPkplAAlD+xEHe08yTDHvhBHIOfTwpp1xRY5HmGFAtB8
fEmjmxIVx2cTYic6rMxa7FrfKgGXzTWQEaCouuOQ8WO41yzYs9PRxNJDWileVD2j
SULAg3lROtGpAQ/67SCEXceNZf9pqrzzuYice3zZutMDmdVHy8gTEED5bcRaevJ2
JhWXJxk0XaqPDWzmbbHx0lz0zvrlV4mvzkbUUHsnPWtAJxU7so43TDMc6QryO6Pw
8B3Iivp8+fDvfVUv3tY4rt4G1rUNEM33Ssl8EdEzHMTQ/3i4FrESsBTOHo2yWUxZ
fhQU2h9fbzgSuIofHM48XXgEHPnnWCt58ttMsNu0D4YC0BpSiwQXCKSB6TuvJ+tp
9mlXtCxxjge4vf0GE8P9LUhKB0nZuXNyJWCIIWMNsXXGvixhAGaSQOsFHkiTw2iH
ruQPFc4WplYcauvEcFzxb/pw51OEtAy99+MORdr6d73rzDVAFQwO0x64VSJeGVyV
vJxM3Ll2iny0/hSaOXnvUHKyqZmI2Yi6rQwlbh12h24jFB1OqrH24QXt2acxp7nZ
0J+Zkz6b3nH1zqSjx0m8+Sisj2RHaxz4sOI/sBhp2FVIUFsxri+d2WRgiTZM6UPo
4ErguLY2hMVuVdG3Br4jzTkCAwEAAQ==
-----END PUBLIC KEY-----`)

##################### vgo
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
source ~/.profile

##################### test
ulimit -n 20480
go run tps.go put https://api-dtl1.pg.digital-transaction.org/v1 1450 200

####################   api-gateway    ######################
sudo pkill api-gateway
touch /etc/parallelchain/debug exists

----config.user.sh
export PGUARD_CLIENT_CONN_POOL_SIZE=400
export PGUARD_LOG_LEVEL=debug

#################### test deploy  ###################
sudo apt-get install python3-pip python-pip
pip install pycrypto
pip3 install pycrypto

sudo pip install selenium
sudo pip3 install selenium
pip3 install requests

#lockfile
sudo apt-get install procmail

sudo apt install jq

ln -s /home/ubuntu/testspace/parallelguard-test/src/sdk/go/ parallelguard-sdk-go

sudo systemctl status apache2
sudo apt install php libapache2-mod-php
sudo apt-get install apache2
sudo service apache2 restart

/etc/apache2/
sudo a2enmod ssl
sudo systemctl restart apache2
sudo mkdir /etc/apache2/ssl

###To disable apache2 simply type:
sudo update-rc.d apache2 disable
###To remove apache2 simply type:
sudo update-rc.d -f  apache2 remove

sdk
rsa-sys
ln -s aidb.py

php php-curl
go/

sudo apt-get install php7.2-curl
################## git ###################
git remote update
git status -uno
//remember pass
$ git config credential.helper store
git config --global credential.helper 'cache --timeout 7200'

#################### vim #################### 
:set number
:s/^/new text /	Insert "new text " at the beginning of the line.
:s/$/ new text/	Append " new text" to the end of the line.

#################### port ##########################
netstat -tulnp | grep <port no>
lsof -i:3000
netstat -ptn | grep EST | wc -l
netstat -n | grep -i 7051 | grep -i time_wait | wc -l

sudo tar -xvf go1.10.1.linux-amd64.tar.gz
sudo mv go /usr/local


export GOROOT=/usr/local/go
export GOPATH=$HOME/Projects/aidb
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH

###################### cron job #######################
0 1 ? * MON-FRI *

####################### letsencrypt #########################
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

################### Tools ###################
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

which python
export PATH=~/.local/bin:$PATH

 mkdir -p go/src/github.com/digital-transaction
~/go/src/github.com/digital-transaction$ ln -s ~/projects/aidb/src/sdk/go ./aidb-sdk-go


################################
if [[ $SINGLE_NODE =~ peer([[:digit:]]+).org([[:digit:]]+) ]]; then
    peer_single="${BASH_REMATCH[1]}"
    org_single="${BASH_REMATCH[2]}"

