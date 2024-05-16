# Labo03 - Run a first container

## Pedagogical intent

In this lab, you'll:

* Get to grips with the first Docker commands,
* Run your first Docker
* Familiarize yourself with port publishing

---

Note: the docker engine must be running

## Task 01 - Get to grips with the first Docker commands

* List all images present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
//TODO
```

* Get the official Nginx image using this command

[INPUT]
```bash
docker pull nginx
```

[OUTPUT]
```
//TODO
```

Note : do you see the different layer uploaded ?

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
//TODO
```

Note : 188 MB is the size of your image... check it.

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
//TODO
```

* List all Docker

[INPUT]
```
docker ps -a
```

[OUTPUT]
```
//TODO
```

## Task 02 - Run the container

* Run Nginx Docker

[INPUT]
```
docker run nginx
```

[OUTPUT]
```
//TODO
```

* Can you reach the default page of nginx

Note : By default, Nginx is listening on port 80

[INPUT]
```
curl localhost
```

[OUTPUT]
```
//TODO
```

* Stop this first attempt

[INPUT]
```
docker stop <id>
```

[OUTPUT]
```
//TODO
```

## Task 03 - Familiarize yourself with port publishing

* Make it possible to reach nginx with this command

[Publish a port](https://docs.docker.com/network/#published-ports)

[INPUT]
```
curl localhost:8080
```

[OUTPUT]
```
//TODO
```

* Stop and delete the container

[INPUT]
```
//TODO delete the container
```

[OUTPUT]
```
//TODO
```

* Delete the image

[INPUT]
```
//TODO delete the image
```

[OUTPUT]
```
//TODO
```
