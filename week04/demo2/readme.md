# Demo 2 : Run Ubuntu container
In this demo an Unbutu 14.04 is pulled to local machine and run bash
## 1. Pull Image : from dockerhub
```bash
$docker pull ubuntu:trusty
```
## 2. Run the container
-  The `-it` instructs Docker to allocate a pseudo-TTY connected to the container’s stdin; creating an interactive bash shell in the container
-  The `--rm` instructs Docker to automatically remove the container when it exits
-  The `ls` instructs Docker to prompt `ls` after enter bash shell
```bash
$sudo docker run -it ubuntu:trusty
$sudo docker run -it --rm ubuntu:trusty
$sudo docker run -it --rm ubuntu:trusty ls
```
## 3. Check version of OS
```bash
$cat /etc/os-release
```