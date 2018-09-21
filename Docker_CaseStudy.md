# Docker Case Study
### Automate infra allocation for L&D

### **Requirements**
-   Dynamic Allocation of Linux systems for users
-   Each user should have independent Linux System
-   Specific training environment should be created in Container
-   User should not allow to access other containers/images
-   User should not allow to access docker command
-   Monitor participants containers
-   Debug/live demo for the participants if they have any doubts/bug in running applications.
-   Automate container creation and deletion.
## Creating the container image
```
docker create -it --name <name> ubuntu /bin/bash
docker start <name>
docker attach <name>
```
### Setup Linux containers for users
1.  Dynamic allocation of Linux systems for users can be achieved by the shell script  `user_containers.sh`.Such a script would create docker for each container.
2. Fill the entries in  `users.txt`  with usernames and run the shell script  `sh createContainers.sh -x`. This creates a docker container corresponding to each username from  `users.txt`.
3. `users.txt`

```
 Rishikesh
 Rahil
 Swastik
```
-   `user_containers.sh`

```
echo -n "enter user file name: "
read file

while read user
  do
      docker create -it --name $user <Img> /bin/bash
  done < $file
```  
 The user can then start using the allocated container by doing the following
 ```
#! /bin/bash
echo -n "Enter your username : "
read name
docker start $name
docker attach $name
```

### Monitoring the Container :
```
#! /bin/bash

echo -n "Enter the container name to be monitored : "
read name
docker logs -f $name

```

### Deletion of Containers :
```
echo -n "Enter the user list file : "
read file

while read user
  do
    docker stop $user
    docker rm $user
  done > $file

```
Execute by using the command :
```
sh <shell script>
```
