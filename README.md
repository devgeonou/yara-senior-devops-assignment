# yara-senior-devops-assignment
Yara Senior Devops Assignment

 ## Test Redis-chart
 
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
