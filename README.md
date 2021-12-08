# dockerLoadBalancer
Percobaan penerapan haproxy sebagai load balancer dengan 2 container untuk app dan database

Docker example with Apache, MySql 8.0, PhpMyAdmin and Php

- You can use MariaDB 10.1 if you checkout to the tag `mariadb-10.1`
- You can use MySql 5.7 if you checkout to the tag `mysql5.7`

I use docker stack as an orchestrator. To run these containers:

```
docker stack deploy --compose-file docker-compose.yml simplecrud
```
Using docker service scale to many replicas. To test load balancer soon:

```
docker service scale simplecrud_app_www=5
docker service scale simplecrud_app=5
```

Running haproxy with docker image from docker hub. To as Load Balancer between multiple container apps:

```
docker run -dit --name haproxy -v $(pwd):/usr/local/etc/haproxy:ro --network simplecrud_afif-net -p 8080:85 haproxy:lts-alpine
```

Open web browser to look at a simple php example at [http://localhost:8080](http://192.168.123.54:8080)

<!-- Trouble shoot :
 add volume to worker node 
 Enjoy ! -->
