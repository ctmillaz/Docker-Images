# Docker-Images

## How to run centOS in docker
```
docker run -d centos tail -f /dev/null
```

## Verify image is running
```
docker ps
```
## How to shell into the operating system
## -it flag is for iteractive mode
```
docker exec -it <names> bash
```

------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------

## How to run mySQL in docker

### How to stand up mySQL that allows empty password.  Development Sandbox.
### Go to https://hub.docker.com/_/mysql/
### We will use the latest tag, go to hyperlink and go down to bottom of Dockerfile to see what ports are next to EXPOSE (Remember those)
### Go back to the mysql page and scroll down to

### First create a tmp directory
```
mkdir /home/dev-user/tmp
```

### While in tmp directory run:
###  docker run --name test-mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -v /hom/dev-user/tmp:/var/lib/mysql -p <port_number>
### I've noticed for this you only need the one port without the zero at the end.
### The command that worked for me is:
```
docker run --name test-mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -v /hom/dev-user/tmp:/var/lib/mysql -p 3306 -d mysql
```

### Verify it's running
```
docker ps
```

### Download DBeaver for CentOS
### Once Downloaded choose mysql as the database type.
### For Connection details, Enter:
### Name: 127.0.0.1
###  Host: 127.0.0.1
###  Username: root
###  Password: <Leave Blank>
###  Database: <Leave Blank>
###  Port: <The port you use above (which currenty is 3306)>
###  Keep clicking next to pass the opional settings and Finish.
###  Once finished you should be able to clickon the new mysql database to the left in the panel and see that it drops down to view other folder which means it connected successfully.
### It should let you know it connected succesfully prior to clicking the dropdown.

------------------------------------------------------------------------
------------------------------------------------------------------------
------------------------------------------------------------------------

## How to run RabbitMQ in docker
### https://hub.docker.com/_/rabbitmq/
### Go down to Supported tags and click on the hyperlink for the 3.*-management.
### Scroll to bottom of dockerfile next to EXPOSE there are ports.  Remember these ports as we will need them.
### Go down to Management Plugin on the docker explore rabbitmq page
### Grab the script
### $ docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 -p <port_number> -p <port_number> rabbitmq:3-management
### These are the current ports you can run
```
$ docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 -p 15671 -p 15672 rabbitmq:3-management
```
### If that does work try it without the -p 15672
```
$ docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 -p 15671 rabbitmq:3-management
```