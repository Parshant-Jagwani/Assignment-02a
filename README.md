
# ASSIGNMENT-2a  BY: Parshant J

### T1: Create a new Docker network named "my_network" using the bridge driver. (2 marks) 
#### cmd #### 
``` 
docker network create --driver=bridge my_network 
```
#### Out-put ####
```
PS C:\Users\parsh> docker network create --driver=bridge my_network
0289c9b40171807ebadc958fd6e48b7b85cc97978bd0c45660677908081de031
```
#### Ans: #### 
_**'docker network create --driver=bridge my_network'** command creates a new Docker network named "my_network" using the bridge driver. The bridge driver is a default network driver in Docker that facilitates communication between containers on the same host._

### T2: Create a new Docker container using the "nginx" image and connect it to the "my_network" network. Name the container "nginx_container".  (4 marks) 
#### cmd 
``` 
docker run --name nginx_cont_for_my_network --network my_network -p 8080:80 -d nginx
```
#### Out-put ####
```
PS C:\Users\parsh> docker run --name nginx_cont_for_my_network --network my_network -p 8080:80 -d nginx
032c5c5c8c87840de0dfde5ec6d7f2df176570dc364a36082f071a71c040a1b0
PS C:\Users\parsh> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
032c5c5c8c87   nginx     "/docker-entrypoint.…"   14 seconds ago   Up 13 seconds   0.0.0.0:8080->80/tcp   nginx_cont_for_my_network
```
#### Ans: #### 
_**'docker run --name nginx_cont_for_my_network --network my_network -p 8080:80 -d nginx'** command runs a Docker container named "nginx_container" using the "nginx" image. The container is connected to the "my_network" network, and port 8080 on the host is mapped to port 80 on the container. The -d flag runs the container in detached mode._

### T3.	Verify that the "nginx" default page is accessible on your host machine at http://localhost:8080. (2 marks)
_Output is shown bellow👇_
![Screenshot of a comment on a GitHub issue showing an image.](https://github.com/Parshant-Jagwani/Assignment-02a/blob/main/T3-Nginx8080.png)
### T4.	Create a new Docker container using the "httpd" image and connect it to the "my_network" network. Name the container "httpd_container". (4 marks)
#### CMD:
``` docker run --name httpd_container --network my_network -p 8081:80 -d httpd ```
#### Out-put ####
```
PS C:\Users\parsh> docker run --name httpd_container --network my_network -p 8081:80 -d httpd
Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
2f44b7a888fa: Already exists
376771e8483c: Pull complete
4f4fb700ef54: Pull complete
6a6627aecff0: Pull complete
152f4888b550: Pull complete
fd0579f22872: Pull complete
Digest: sha256:ba846154ade27292d216cce2d21f1c7e589f3b66a4a643bff0cdd348efd17aa3
```
#### Ans: #### 
_**'docker run --name httpd_container --network my_network -p 8081:80 -d httpd'** command creates a Docker container named "httpd_container" using the "httpd" image. The container is connected to the "my_network" network, and port 8081 on the host is mapped to port 80 on the container. The -d flag runs the container in detached mode._

### T5.	Verify that the "httpd" default page is accessible on your host machine at http://localhost:8081. (2 marks)
_Output is shown bellow👇_
![Screenshot of a comment on a GitHub issue showing an image.](https://github.com/Parshant-Jagwani/Assignment-02a/blob/main/T5-httpd-8081.png)

### T6.	Use the "docker network inspect" command to display information about the "my_network" network. Document your findings in the README.md file. (4 marks)
#### CMD
```
docker network inspect my_network 
```
#### Output / Findings
```
[
    {
        "Name": "my_network",
        "Id": "0289c9b40171807ebadc958fd6e48b7b85cc97978bd0c45660677908081de031",
        "Created": "2024-01-26T08:45:39.383832996Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "032c5c5c8c87840de0dfde5ec6d7f2df176570dc364a36082f071a71c040a1b0": {
                "Name": "nginx_cont_for_my_network",
                "EndpointID": "941d91f14494df7dd6d19d9b18e59690bd9c7acfeb04e65acf8498473b99bad2",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "70456f6f8c6cb2c21bb2fc704341fd6d6151b2329edfdeeac80c9439853b7933": {
                "Name": "httpd_container",
                "EndpointID": "85f748b44983c4ebe17260e19ed73e33e2e4229f9bf97ae887188d044bd9f25e",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```
#### Ans: #### 
_**'docker network inspect my_network'** command retrieves and displays detailed information about the "my_network" Docker network, including its configuration, connected containers, and other relevant details._

### T7.	Stop and remove the "nginx_container" container. (2 marks)
#### CMDs
```
docker stop nginx_cont_for_my_network
docker rm nginx_cont_for_my_network
```
#### Output / Findings
```
PS C:\Users\parsh> docker stop nginx_cont_for_my_network
nginx_cont_for_my_network
PS C:\Users\parsh> docker rm nginx_cont_for_my_network
nginx_cont_for_my_network
```
#### Ans: #### 
_**'docker stop nginx_cont_for_my_network'** command stops the Docker container named "nginx_cont_for_my_network." The docker stop command gracefully halts the execution of the specified container._

_**'docker rm nginx_cont_for_my_network'** command removes the Docker container named "nginx_cont_for_my_network." The docker rm command deletes the specified container, freeing up resources and removing the container from the system._

### T8.	Create a new Docker container using the "nginx" image and connect it to the "my_network" network. Name the container "nginx_container_2". (4 marks)
#### CMD
```
docker run --name nginx_container_2 --network my_network -p 8082:80 -d nginx
```
#### Output / Findings
```
PS C:\Users\parsh> docker run --name nginx_container_2 --network my_network -p 8082:80 -d nginx
4ff6bf6be1a5b9c938fccdd873778577b516cb4570763eb6eaf470f600a022fc
```
#### Ans: #### 
_**'docker run --name nginx_container_2 --network my_network -p 8082:80 -d nginx'** creates a new Docker container named "nginx_container_2" using the "nginx" image. The container is connected to the "my_network" network, and port 8082 on the host is mapped to port 80 on the container._

### T9.	Verify that the "nginx" default page is accessible on your host machine at http://localhost:8082. (2 marks)

_Output is shown bellow👇_
![Screenshot of a comment on a GitHub issue showing an image.](https://github.com/Parshant-Jagwani/Assignment-02a/blob/main/T9-Nginx8082.png)

### T10.	Use the "docker container ls" command to display information about all running containers. Document your findings in the README.md file. (4 marks)

```
PS C:\Users\parsh> docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED             STATUS             PORTS                  NAMES
4ff6bf6be1a5   nginx     "/docker-entrypoint.…"   2 minutes ago       Up 2 minutes       0.0.0.0:8082->80/tcp   nginx_container_2
70456f6f8c6c   httpd     "httpd-foreground"       About an hour ago   Up About an hour   0.0.0.0:8081->80/tcp   httpd_container
PS C:\Users\parsh> docker container ls  | Out-File -FilePath C:\Users\parsh\OneDrive\Desktop\README.md
```
#### Ans: #### 

_**'docker container ls'** lists information about all running containers. It provides details such as the container ID, names, image names, status, and ports._

_**'|'** The pipe operator takes the output from the previous command and passes it as input to the next command._

_**'Out-File -FilePath C:\Users\parsh\OneDrive\Desktop\README.md '** This PowerShell cmdlet is used to write the output to a file. it writes the output of the docker container ls command to a file named README.md on the desktop._

### T11.	Stop and remove all containers. (2 marks)
#### CMD
```
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```
#### Output / Findings
```
PS C:\Users\parsh> docker stop $(docker ps -aq)
4ff6bf6be1a5
70456f6f8c6c
b492f4bbfc62
90715e84e8ef
da970f2b376b
6ac1f518ce2b
bcd56333614a
fd2d4ea50448
1b4670e0bf98
35449051089b
88b25537e616
a97be49904ea
713bf475d402
f0c72a06a2ac
f3b317707248
e504e32c9c6e
085b90062cb9
99290431779a
PS C:\Users\parsh> docker rm $(docker ps -aq)
4ff6bf6be1a5
70456f6f8c6c
b492f4bbfc62
90715e84e8ef
da970f2b376b
6ac1f518ce2b
bcd56333614a
fd2d4ea50448
1b4670e0bf98
35449051089b
88b25537e616
a97be49904ea
713bf475d402
f0c72a06a2ac
f3b317707248
e504e32c9c6e
085b90062cb9
99290431779a
```
#### Ans: #### 

_**'docker stop $(docker ps -aq)'** Stops all running Docker containers. The $(docker ps -aq) part uses a subshell to fetch the IDs of all containers and passes them to the docker stop command.._

_**'docker rm $(docker ps -aq)'** This command removes all Docker containers. Similar to the previous command, it uses the $(docker ps -aq) part to fetch the IDs of all containers and passes them to the docker rm command._

### T12.	Cleanup: Remove the "my_network" network. (2 marks)
#### CMD
```
docker network rm my_network
```
#### Output / Findings
```
PS C:\Users\parsh> docker network rm my_network
my_network
```
#### Ans: #### 
_**'docker network rm my_network'** Removes the Docker network named "my_network," cleaning up the network created in the earlier steps._
