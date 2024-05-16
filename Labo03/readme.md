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
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
sail-8.2/app         latest    2faad95ff07d   2 months ago    978MB
mysql/mysql-server   8.0       1d9c2219ff69   16 months ago   496MB
```

* Get the official Nginx image using this command

[INPUT]
```bash
docker pull nginx
```

[OUTPUT]
```
Digest: sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
```

Note : do you see the different layer uploaded ?

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
nginx                latest    e784f4560448   12 days ago     188MB
sail-8.2/app         latest    2faad95ff07d   2 months ago    978MB
mysql/mysql-server   8.0       1d9c2219ff69   16 months ago   496MB
```

Note : 188 MB is the size of your image... check it.

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
nginx                latest    e784f4560448   12 days ago     188MB
sail-8.2/app         latest    2faad95ff07d   2 months ago    978MB
mysql/mysql-server   8.0       1d9c2219ff69   16 months ago   496MB
```

* List all Docker

[INPUT]
```
docker ps -a
```

[OUTPUT]
```
5bdaee27da3f   sail-8.2/app             "start-container"        3 weeks ago   Exited (255) 3 weeks ago   0.0.0.0:5173->5173/tcp, 8000/tcp, 0.0.0.0:8080->80/tcp   matuxor-laravel.test-1
5f5bf3d0b919   mysql/mysql-server:8.0   "/entrypoint.sh mysq…"   3 weeks ago   Exited (255) 3 weeks ago   33060-33061/tcp, 0.0.0.0:3307->3306/tcp                  matuxor-mysql-1
```

## Task 02 - Run the container

* Run Nginx Docker

[INPUT]
```
docker run nginx
```

[OUTPUT]
```
it run
```

* Can you reach the default page of nginx

Note : By default, Nginx is listening on port 80

[INPUT]
```
curl localhost
```

[OUTPUT]
```
curl : Impossible de se connecter au serveur distant
Au caractère Ligne:1 : 1
+ curl localhost
+ ~~~~~~~~~~~~~~
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand
```

* Stop this first attempt

[INPUT]
```
docker stop <id>
```

[OUTPUT]
```
cab15965b333c6c07909d35af48cb8d2ec07dc47c9e07a351d117a8da0f6180c
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
StatusCode        : 200
StatusDescription : OK
Content           : <!DOCTYPE html>
                    <html>
                    <head>
                    <title>Welcome to nginx!</title>
                    <style>
                    html { color-scheme: light dark; }
                    body { width: 35em; margin: 0 auto;
                    font-family: Tahoma, Verdana, Arial, sans-serif; }
                    </style...
RawContent        : HTTP/1.1 200 OK
                    Connection: keep-alive
                    Accept-Ranges: bytes
                    Content-Length: 615
                    Content-Type: text/html
                    Date: Thu, 16 May 2024 06:45:14 GMT
                    ETag: "661e8b67-267"
                    Last-Modified: Tue, 16 Apr 2024 ...
Forms             : {}
Headers           : {[Connection, keep-alive], [Accept-Ranges, bytes], [Content-Length, 615], [Content-Type, text/html]...}
Images            : {}
InputFields       : {}
Links             : {@{innerHTML=nginx.org; innerText=nginx.org; outerHTML=<A href="http://nginx.org/">nginx.org</A>; outerText=nginx.org; tagName=A; href=http://nginx.org/}, @{innerHTML=nginx.com; innerText=nginx.com;
                    outerHTML=<A href="http://nginx.com/">nginx.com</A>; outerText=nginx.com; tagName=A; href=http://nginx.com/}}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 615
```

* Stop and delete the container

[INPUT]
```
docker stop cab15965b333c6c07909d35af48cb8d2ec07dc47c9e07a351d117a8da0f6180c
docker rm cab15965b333c6c07909d35af48cb8d2ec07dc47c9e07a351d117a8da0f6180c
```

[OUTPUT]
```
cab15965b333c6c07909d35af48cb8d2ec07dc47c9e07a351d117a8da0f6180c
```

* Delete the image

[INPUT]
```
docker rmi e784f4560448 -f
```

[OUTPUT]
```
PS C:\SchoolPJS\Vir1Labs> docker rmi e784f4560448
Error response from daemon: conflict: unable to delete e784f4560448 (must be forced) - image is being used by stopped container eaa089f87200
PS C:\SchoolPJS\Vir1Labs> docker rmi e784f4560448 -f
Untagged: nginx:latest
Untagged: nginx@sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Deleted: sha256:e784f4560448b14a66f55c26e1b4dad2c2877cc73d001b7cd0b18e24a700a070
PS C:\SchoolPJS\Vir1Labs>
```
