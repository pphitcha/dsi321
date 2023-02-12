# Demo 1 : Install Docker, then try pull and run docker
## 1. Setup Docker
* For Windows please install WSL and Docker for Desktop. Check the document here https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers
* For Mac install Docker Desktop
* For Ubunto use
```bash
$sudo apt-get update
$sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
## 2. Check Docker version
- It is good the remember the Docker version current in use
```bash
$docker --version
```
## 3. Pull Image
- Pull image(registry) from DockerHub to local manchine : hello world 
- Hello world is just a simple image to print some text on the screen when run
```bash
$docker pull hello-world
```
## 4. List Image
- Show list of images in local machine
```bash
$docker images
```
## 5. Run Image
- Use the image for spawning a container and run.
- Use the image for spawning a container and run (auto remove container when exited).
```bash
$docker run hello-world
$docker run --rm hello-world
```