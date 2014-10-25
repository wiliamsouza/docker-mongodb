docker-mongodb
------------

Docker mongodb server generic image source. This is based on `ubuntu:14.04` image.

Image
-----

You can `pull` a ready to use image from Docker
[index](https://index.docker.io/u/wiliamsouza/) running:

```
$ docker pull wiliamsouza/mongodb
```

Or build this repository:

```
$ git clone https://github.com/wiliamsouza/docker-mongodb.git
$ cd docker-mongodb/
$ docker build -t wiliamsouza/mongodb .
```

Change `wiliamsouza/mongodb` to your Docker index username.

Container
---------

This image uses volumes and environment variables to control the mongodb server
configuration.

Volumes:

* `/etc/mongodb`: Change server configurations using it.
* `/var/lib/mongodb`: Data goes here.
* `/var/log/mongodb`: Access log from the container using it.

You pass with `-v` docker option. Don't forget to use absolute path here.

Shell access:

```
$ docker run -p 27017:27017 -i \
-v `pwd`/volumes/log:/var/log/mongodb \
-v `pwd`/volumes/lib:/var/lib/mongodb \
-v `pwd`/volumes/etc:/etc/mongodb \
-t wiliamsouza/mongodb /bin/bash
```

The command above will start a container give you a shell. Don't
forget to start the service running the `startup &` script.

Usage:

```
$ docker run --name mongodb -p 27017:27017 -d \
-v `pwd`/volumes/log:/var/log/mongodb \
-v `pwd`/volumes/lib:/var/lib/mongodb \
-v `pwd`/volumes/etc:/etc/mongodb \
-t wiliamsouza/mongodb
```

The command above will start a container and return its ID.
