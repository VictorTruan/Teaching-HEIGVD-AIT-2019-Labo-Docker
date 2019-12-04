title: Lab 04 - Docker
---

## Lab 03 - Docker

#### Table of content

#### Introduction

#### Chapter 0
[M1]Do you think we can use the current solution for a production environment? What are the main problems when deploying it in a production environment?
``` 
This is not a good idea to use our previous solution in production because it alwayshave 2 servers and never more or less.
When a lot of client are going to connect, ourserver could be under too many trafics and could not handle new requests so the newclient won't have any answer.
In the other case when there is no user, we still have twonode up which are beeing used for nothing and cost money for nothing.
```
[M2] Describe what you need to do to add new webapp container to the infrastructure. Give the exact steps of what you have to do without modifiying the way the things are done. Hint: You probably have to modify some configuration and script files in a Docker image.

```
To add a new image we have some file to change, thoses are the files and the modifications we have done :
1) Modification of "docker-compose.yml" so we can add a node name webapp3 which use envvar from haproxy.
```
![](img/AIT_Labo04_Image01.png)

```
2) Modification of /ha/scripts/run.sh so it know which node to use.
```
![](img/AIT_Labo04_Image02.png)

```
3) Modification of /ha/config/haproxy.cfg.
```
![](img/AIT_Labo04_Image03.png)

```
4) We need to change the .env file to add the servers3 env variables.
```
![](img/AIT_Labo04_Image04.png)

[M3] Based on your previous answers, you have detected some issues in the current solution. Now propose a better approach at a high level.
```
There is too much files to modify, the procedure is too heavy. And we also need to restart all the infrastructure.

It should be a good idea to make thing smoother, for example the load balancer should automatically add new nodes discovered in the network.
```

[M4] You probably noticed that the list of web application nodes is hardcoded in the load balancer configuration. How can we manage the web app nodes in a more dynamic fashion?
```
We can make a system where each new node query the load balancer to tell that he is available to handle load, and then the laod balancer adds them.
```

[M5] Do you think our current solution is able to run additional management processes beside the main web server / load balancer process in a container? If no, what is missing / required to reach the goal? If yes, how to proceed to run for example a log forwarding process?
```
Yes, we can find a workaround, we can edit the 'run.sh' script and add instruction to log the node activities.
But this not an optimal solution.
```

[M6] What happens if we add more web server nodes? Do you think it is really dynamic? It's far away from being a dynamic configuration. Can you propose a solution to solve this?
(Répondre à la deuxième partie)
```
It's not dynamic since we have to restart the load balancer,
```

Deliverables:

1)
![](img/AIT_Labo04_Image05.png)

2)
https://github.com/VictorTruan/Teaching-HEIGVD-AIT-2019-Labo-Docker

#### Chapter 1

#### Chapter 2

#### Chapter 3

#### Chapter 4

#### Chapter 5

#### Chapter 6


#### Difficulties


#### Conclusion.