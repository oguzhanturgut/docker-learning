# Docker Notes

Delete all  containers `docker container rm $(docker container ls -aq) -f` 

Mount volume

`docker run -d  --rm -v $(pwd):/usr/share/nginx/html --name web1 nginx:alpine`

List all networks

`docker network ls`

Create new custom network

`docker network create --driver bridge alpine-network`

Show properties of network

`docker network inspect alpine-network`

Run container using custom network

`docker run -dit --name c1 --network alpine-network alpine sh`

Create Macvlan network - directly connected to the physical network

`docker network create -d macvlan --subnet=192.16.86.0/24 --gateway=172.16.86.1 -o parent=eth1 pub_net`

Overlay Networks allow you to combine multiple separate Docker hosts into one logical network and containers can communicate across hosts.

```angular2
docker swarm init --advertise-addr=<Manager IP>

docker network ls

docker network create -d overlay nginx-net

docker service create --name my-nginx --publish target=80,published=80 replicas=3 --network nginx-net nginx

docker network ls

docker service ps my-nginx

```

