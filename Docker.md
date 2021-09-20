# docker

#### Install docker ######

`sudo apt install docker.io docker-compose`
`docker version`
`sudo usermod -a -G docker $USER`
`docker run hello-world`

*fix: Failed to start docker.service: Unit docker.service is masked.*
sudo systemctl unmask docker.service
sudo systemctl unmask docker.socket
sudo systemctl start docker.service
//
sudo systemctl start docker
//
sudo screen -ls
//
docker ps
docker ps --filter ancestor=hyperledger/fabric-peer:latest --format '{{.Names}}'
docker inspect --format="{{.LogPath}}" peer0.org1.example.com
docker inspect net_peer0.org1.example.com


docker logs peer0.org1.aahk.aidb.digital-transaction.org
docker logs -f orderer.example.com

docker exec -it cli bash
docker exec -it peer0.org2.dtl1.pg.digital-transaction.org bash

//

```bash
docker rmi -f $(docker images -qa)
docker rm -f $(docker ps -aq) #ID
docker rm -f $(sudo -S docker ps -aq  --filter ancestor=redis) #Name
docker volume ls
docker volume prune -f
```

~~

restart an existing container after it exited and your changes are still there.

```bash
docker start  `docker ps -q -l` # restart it in the background
docker attach `docker ps -q -l` # reattach the terminal & stdin
```

```
docker start -a -i `docker ps -q -l`
```

Explanation:

`docker start` start a container (requires name or ID)
`-a` attach to container
`-i` interactive mode
`docker ps` List containers
`-q` list only container IDs
`-l` list only last created container

//
apt update
apt install net-tools


./setup-docker-images.sh -d

/bin/bash -c './scripts/script.sh mychannel'


docker logs -f orderer1.example.com
peer channel create -o orderer0.example.com:7050 -c aidbc -f ./channel-artifacts/channel.tx --tls true --cafile /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer0.example.com/msp/tlscacerts/tlsca.example.com-cert.pem

peer channel create -o orderer1.example.com:7050 -c aidbc -f ./channel-artifacts/channel.tx --tls true --cafile /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer1.example.com/msp/tlscacerts/tlsca.example.com-cert.pem

peer chaincode invoke -o orderer0.example.com:7050 -n aidbcc -c '{"Args":["get","test/try"]}'
peer chaincode invoke -o orderer0.example.com:7050 --tls true --cafile /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer0.example.com/msp/tlscacerts/tlsca.example.com-cert.pem -C aidbc -n aidbcc --peerAddresses peer0.org2.example.com:7051 --tlsRootCertFiles /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt -c '{"Args":["get", "test/try"]}'

peer chaincode invoke -o orderer1.example.com:7050 --tls true --cafile /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer1.example.com/msp/tlscacerts/tlsca.example.com-cert.pem -C aidbc -n aidbcc --peerAddresses peer0.org2.example.com:7051 --tlsRootCertFiles /opt/gopath/src/bitbucket.org/digital-transaction/mychain/peer/crypto/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt -c '{"Args":["get", "test/try"]}'

docker pull hyperledger/fabric-kafka:0.4.10
docker login -u dtlengineers
docker tag hyperledger/fabric-kafka:0.4.10 mychaindev/kafka:0.4.10
docker push mychaindev/kafka:0.4.10


docker pull hyperledger/fabric-zookeeper:0.4.10
docker login -u dtlengineers
docker tag hyperledger/fabric-zookeeper:0.4.10 mychaindev/zookeeper:0.4.10
docker push mychaindev/zookeeper:0.4.10


