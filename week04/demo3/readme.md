# Demo 3 : Python (Build / Run)
In this demo we are going to build a new image from a Dockerfile using base image

## 1. create a directory : demo3
```bash
$mkdir demo3
$cd demo3
``` 
## 2. create a Dockerfile
create a Dockerfile for the following code
```Dockerfile
# Dockerfile
FROM python:3.7-alpine
CMD ["python","--version"]
```
* ```FROM python:3.7-alpine``` from python image tag ```3.7-alpine```
* ```CMD ["python","--version"]``` start a new process using bash command ```$python --version```


## 3. build an image
- create a new image locally and name it as ```python``` and tag ```3.7``` using the Dockerfile in directory `week04\demo3`
- `-t` means Name and optionally a tag in the 'name:tag' format
- if `Dockerfile` is in the current directory, use (.) instead
```bash
$docker build -t python:3.7 week04\demo3
$docker build -t python:3.7 .
```

## 4. spawn container from image
- start a container from the image. 
- ```-it``` is interactive mode. 
- ```--rm``` is remove container when process stop.
```bash
$docker run -it --rm python:3.7
```