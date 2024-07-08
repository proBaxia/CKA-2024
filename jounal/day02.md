frist creat a folder and save `day02`

# How To  Dockerize a sample appllcation project

#### Clone a sammple to-do app

 (docker/getting-started.git){https://github.com/docker/getting-started-app.git}

- enter the repo you clone `getting-started-app`and write a `Dockerfile`

![alt text](images/image.png)

`Dockerfile`

~~~bash
FROM node:18-alpine

WORKDIR /app

COPY . .

RUN yarn install --production

CMD [*node*,  *src/index.js*]

EXPOSE 3000
~~~

- build the image using `docker build` 
~~~
docker build -t day02-todo .
~~~


![alt text](images/image-1.png)


view the image with 
~~~
docker images
~~~

![alt text](images/image-2.png)

- we have to push the image to the image repostory 
- login to your Docker and create a new repository `probaxia/todorepo`

![alt text](images/image-3.png)

- tag and push to your doker hub repo
~~~
docker tag day02-todo:latest probaxia/todorepo:latest
~~~

![alt text](images/image-4.png)

~~~
docker push probaxia/todorepo:latest
~~~

![alt text](images/image-6.png)

![alt text](images/image-5.png)

- pull the image from docker hub and run it on your terminal 

~~~
docker pull probaxia/todorepo:latest
~~~

![alt text](images/image-7.png)

~~~
docker run -dp 3000:3000 probaxia/todorepo:latest
~~~

- view your running container 
~~~
docker ps
~~~ 

![alt text](images/image-8.png)

- to access your application 

~~~
http://localhost:3000/
~~~

![alt text](images/image-9.png)

- To troubleshoot you docker container 

~~~
docker exec -it container_ID bash

~~~

![alt text](images/image-10.png)
- by defalt you will enter your container  root `/app`

- get out from your root container

~~~
exit 
~~~
![alt text](images/image-11.png)
