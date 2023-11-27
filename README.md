# yara-senior-devops-assignment
Yara Senior Devops Assignment

 ## About
 
This repository contains two projects: a Docker Compose project and a Helm chart.

The Docker Compose project has two environments, each deploying a WordPress site and a Hello World Node.js app.

The WordPress site includes a MariaDB database and an Nginx server.

The Helm chart deploys a Redis deployment exposed by a ClusterIP service. It also includes a cronJob that runs a script deployed as a ConfigMap to add dummy data to the Redis deployment. Additionally, there's a secret to store the password.

Below are instructions to test each project:

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
 You should see a Hello World! message displayed



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
