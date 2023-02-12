# Demo 4 : Micro webserver with flask
Please check comment in the Dockefile

## 1. Create required Files
- requirements.txt
```
flask==2.2
```
- app.py
```python
# app.py
from flask import Flask, jsonify
import datetime as dt
app = Flask(__name__)

@app.route('/')
def index():
    return 'Hello World!'

@app.route('/date')
def mydate():
    x= dt.datetime.now()
    return jsonify(
        weekday=x.weekday(),
        day=x.day,
        month=x.month,
        year=x.year
    )

if __name__ == "__main__":
    app.run(host="0.0.0.0", debug=True)
```
- Dockerfile
```Dockerfile
#Dockerfile
#from python image
FROM python:3.7-alpine

#make a new directory
RUN mkdir /app
#copy code app.py and requirements.txt from current directory in host to /app in container
COPY app.py /app
COPY requirements.txt /app
#container change working directory to /app
WORKDIR /app

#install python model in requiremts.txt
RUN pip install -r requirements.txt
#allow network interface of container port 5000 to connect to the host network
EXPOSE 5000

#start the main process in container
CMD ["python","app.py"]

``` 


## 2. build an image
create a new image locally and name it as ```myflask``` and tag ```1.1``` using the Dockerfile in current directory (. means current directory)
```bash
$cd demo4
$docker build -t myflask:1.1 .
```

## 3.run container from image
start a container from the image. 
```bash
$docker run -it --rm -p 8000:5000 myflask:1.1
```
* ```-it``` is interactive mode.
* ```--rm``` is remove container when process stop.
* ```-p 8000:5000``` forward host port 8000 to container port 5000

## 4. check result in browser
* go to http://localhost:8000/ you should see "Hello World"
* go to http://localhost:8000/date you should see datetime in JSON format as following
```json
{
  "day": 24,
  "month": 1,
  "weekday": 1,
  "year": 2023
}
``` 