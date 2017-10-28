# docker-commands
Some of my useful docker commands

Cleaning up previously built image and container
<pre>
#!/bin/bash

export DOCKER_HOST="tcp://${MY_DOCKER_HOST}:2376"

export DOCKER_TLS_VERIFY=1
export DOCKER_CERT_PATH=/var/lib/jenkins/dockerauth/rightway

./docker/docker \
             ps -a

./docker/docker \
             ps -a | grep 'fleet' | \
             cut -f 1 -d ' ' | \
             xargs -I cont ./docker/docker \
                           rm -f cont
./docker/docker \
             images | grep 'fleet' | \
             awk '{ print $3 }' | \
             xargs -I img ./docker/docker \
                           rmi -f img
</pre>

Downloading particular docker version if does not exist in workspace
<pre>
if [ ! -f docker-1.11.2.tgz ]; then
	wget https://get.docker.com/builds/Linux/x86_64/docker-1.11.2.tgz
	tar -zxvf docker-1.11.2.tgz
fi
</pre>
