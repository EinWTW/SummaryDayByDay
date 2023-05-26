# docker

#### Install docker ######

```
sudo apt install docker.io docker-compose
docker version
sudo usermod -a -G docker $USER
docker run hello-world
```

*fix: Failed to start docker.service: Unit docker.service is masked.*
sudo systemctl unmask docker.service
sudo systemctl unmask docker.socket
sudo systemctl start docker.service
//
sudo systemctl start docker
//
sudo screen -ls

#### Run with docker

```
e.g.
$ docker run --restart always -d -p 7770-7771:7770-7771 --name conode -v ~/conode_data:/conode_data dedis/conode:latest
```

#### Mount Point

```
src/hardhat$ docker run -it -v ./:/share trailofbits/eth-security-toolbox

```



#### Start container

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

Restart an existing container after it exited and your changes are still there.

```bash
docker start  `docker ps -q -l` # restart it in the background
docker attach `docker ps -q -l` # reattach the terminal & stdin
```



#### Docker ps

```bash
docker ps
docker ps --filter ancestor=hyperledger/fabric-peer:latest --format '{{.Names}}'

```

#### Docker log

```
docker logs peer0.org1
docker logs -f orderer.example.com

docker inspect --format="{{.LogPath}}" peer0.org1.example.com
docker inspect net_peer0.org1.example.com


docker exec -it cli bash
docker exec -it peer0.org2 bash
```

#### Docker flag 

--rm

```
--rm is used when you need the container to be deleted after the task
$ docker --rm
```



#### Remove container/image/volume

```bash
docker rm -f $(docker ps -aq) #ID
docker rm -f $(sudo -S docker ps -aq  --filter ancestor=redis) #Name


docker rmi -f $(docker images -qa)
docker image prune
#docker images purge

docker volume ls
docker volume prune -f
```



#### Docker login

```
docker login repository_details
```



#### Docker Compose 

1. Build the docker container:

   ```
   docker-compose build
   ```

2. Run the docker compose stack which includes kafka and zookeeper:

   ```
   docker-compose down; docker-compose up
   ```
   
   #### 

#### Container ID/IP

```
# Identify the container ID
CONTAINER_ID=$(docker container ls | grep graph-node | cut -d' ' -f1)

# Identify container IP
docker inspect   -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' satya5

```



//
apt update
apt install net-tools


./setup-docker-images.sh -d

/bin/bash -c './scripts/script.sh mychannel'

docker logs -f orderer1.example.com
peer channel create -o orderer0.example.com:7050 -c aidbc -f ./channel-artifacts/channel.tx --tls true --cafile /opt/gopath/src/bitbucket.org/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer0.example.com/msp/tlscacerts/tlsca.example.com-cert.pem

peer channel create -o orderer1.example.com:7050 -c aidbc -f ./channel-artifacts/channel.tx --tls true --cafile /opt/gopath/src/bitbucket.org/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer1.example.com/msp/tlscacerts/tlsca.example.com-cert.pem

peer chaincode invoke -o orderer0.example.com:7050 -n aidbcc -c '{"Args":["get","test/try"]}'
peer chaincode invoke -o orderer0.example.com:7050 --tls true --cafile /opt/gopath/src/bitbucket.org/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer0.example.com/msp/tlscacerts/tlsca.example.com-cert.pem -C aidbc -n aidbcc --peerAddresses peer0.org2.example.com:7051 --tlsRootCertFiles /opt/gopath/src/bitbucket.org/mychain/peer/crypto/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt -c '{"Args":["get", "test/try"]}'

peer chaincode invoke -o orderer1.example.com:7050 --tls true --cafile /opt/gopath/src/bitbucket.org/mychain/peer/crypto/ordererOrganizations/example.com/orderers/orderer1.example.com/msp/tlscacerts/tlsca.example.com-cert.pem -C aidbc -n aidbcc --peerAddresses peer0.org2.example.com:7051 --tlsRootCertFiles /opt/gopath/src/bitbucket.org/mychain/peer/crypto/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt -c '{"Args":["get", "test/try"]}'

docker pull hyperledger/fabric-kafka:0.4.10
docker login -u engineers
docker tag hyperledger/fabric-kafka:0.4.10 mychaindev/kafka:0.4.10
docker push mychaindev/kafka:0.4.10

docker pull hyperledger/fabric-zookeeper:0.4.10
docker login -u engineers
docker tag hyperledger/fabric-zookeeper:0.4.10 mychaindev/zookeeper:0.4.10
docker push mychaindev/zookeeper:0.4.10



