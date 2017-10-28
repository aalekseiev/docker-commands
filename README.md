# docker-commands
Some of my useful docker commands

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
