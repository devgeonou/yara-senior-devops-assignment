# yara-senior-devops-assignment
Yara Senior Devops Assignment

 ## About
 
 This repository contains two projects a docker compose project and a helm chart.

 The docker compose project has 2 environmets and each deploys a wordpress site and a hello world, node app.
 
 The wordpress site has a mariadb database and a nginx server.

 The helm chart deploys a redis deployment exposed by a clusterIP service and it has a cronJob that runs a script deployed as a configMap that adds dummy data to the redis deployment, it also has a secret to store the password.

 below there are instructions to test each project:

 ## Test docker-env

 ### Clone the repo
 
 ```
 git clone https://github.com/devgeonou/yara-senior-devops-assignment.git
 ```

 ### Change directory to docker-env
 
 ```
 cd yara-senior-devops-assignment/
 cd docker-env/
 ```
 ### Launch environments
 
 ```
 docker-compose -f docker-compose.dev2.yml -f docker-compose.dev1.yml up -d

 ```

 ### Access Wordpress
 
 ```
 curl -L localhost:8086
 curl -L localhost:8085

 ```
 
 You should see the wordpress installation page

 ### Access Node App
 
 ```
 curl -L localhost:8080
 curl -L localhost:8090

 ```
 You should see a Hello Wrold! message displayed



 ## Test redis-chart
 
 ### Clone the repo
 
 ```
 git clone https://github.com/devgeonou/yara-senior-devops-assignment.git
 ```
 ### Change directory to redis-chart
 
 ```
 cd yara-senior-devops-assignment/
 cd redis-chart/
 ```
 
 ### Install helm
 
 ```
 helm install [RELEASE_NAME] ./ 
 ```
 
 ### Get the redis password
 
 ```
 kubectl get secrets
 kubectl get secret redis-secret -o jsonpath="{.data.redis-password}" | base64 --decode
 ```
 
 ### Get redis cluster ip
 
 ```
 kubectl get services
 ```
 
 ### Log into the redis server
 
 ```
 apt install redis-tools
 redis-cli -h [CLUSTERIP] -p 6379 -a [SECRET]
 ```
 
 ### Retrieve the dummy data
 
 ```
 KEYS *
 ```
