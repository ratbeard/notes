boot2docker: osx script to install and manage the vagrant image running the docker deamon

Setup:
http://docs.docker.io/en/latest/installation/mac/#macosx

already had docker client installed.
installed boot2docker.  ~10 minutes to download
forwarded dockers default port range to virtual box.  Note it takes a while, I thought it had stalled and killed it.
Logged in:

		boot2docker up
		boot2docker ssh  # docker / tcuser

Needed to export this variable!

		export DOCKER_HOST=tcp://127.0.0.1:4243

Pull ubuntu base image and run hello world

		docker pull ubuntu

I ctrl+c'd out for some reason and then when I tried to pull again I got an error.
Apparently aborting continues in the background, but I restarted docker server and re-pulled.
See https://github.com/dotcloud/docker/issues/3115

		boot2docker stop
		boot2docker start

Created a group `docker` and added my user to be able to run commands w/o sudo.
Adding a group on osx is weird.
On linux:

		sudo groupadd docker
		sudo gpasswd -a ${USER} docker


Hellow world:

		docker run ubuntu /bin/echo hello world

Run an image as a daemon
		
		C=$(docker run -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done;")
		docker logs $C
		docker attach -sig-proxy=false $C
		docker ps
		docker stop $C

Building nodejs image for imgoblin

		# Create Dockerfile:
		# DOCKER-VERSION
		# FROM source image
		# RUN commands 
		# ADD app source
		# Expose 7777
		# CMD to start server

		docker build -t ratbeard/imgoblin .

Run it!

		docker run -d -p 49777:7777 ratbeard/imagoblin

What is the difference between entrypoint, cmd, run?

## phusion/baseimage

run inside docker:

	docker run  -t -i phusion/baseimage /sbin/my_init -- bash -l


## Volumes

How to manage data inside an image.  Use a data-only container and mount it as
a volume.  Can also mount a directory from the host, but this is not allowed
inside a Dockerfile due to portability of container issues.

Not subject to copy-on-write, faster for large files.
`docker cp` to copy data out. `docker inspect` - ? 

HUGE snaggles getting this to work:

- if the volume directory is empty, permissions don't apply.  https://github.com/dotcloud/docker/issues/2969
- forgot to kill the old data image name so I wasn't actually testing any of my Dockerfile changes

Useful:

		# Test out change to data container:
		docker build -t ratbeard/imgoblin-db .
		docker run -name imgoblin-db1 ratbeard/imgoblin-db  # get error
		docker rm <container id>
		docker run -name imgoblin-db1 ratbeard/imgoblin-db
				
		docker kill $(docker ps --no-trunc | grep api | awk '{print $1}')
		docker run -d -p 7777:7777 --volumes-from=imgoblin-db1 ratbeard/imgoblin-api



http://blog.docker.io/2013/09/docker-at-djangocon-us-2013/
good slides
...

[1] http://stackoverflow.com/questions/16047306/how-is-docker-io-different-from-a-normal-virtual-machine
[http://r.32k.io/adf](amazon app delivery system)

http://devo.ps/blog/2013/09/25/vagrant-docker-and-ansible-wtf.html
	good guide for getting to deploy an app w/ vagrant docker and ansible.
