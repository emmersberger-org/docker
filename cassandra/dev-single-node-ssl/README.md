#Description
This repo contains the Dockerfile and all other rlevant certs required to create a single node
docker cassandra container that works for ssl connections

#Prerequisites
* Install docker-machine. You can just install docker toolbox.  Docker machine comes with docker toolbox https://www.docker.com/docker-toolbox
* Insatll DevCenter from dataStatx. This is optional. You will need this to run cql queries. However  in the last step there is a way to do this using another container

#Install and start docker machine on local box
Docker machine comes as part of the docker toolbox. https://docs.docker.com/machine/


#Get script to generate docker machine env
Assuming that the name of the docker machine you created is **default**
`docker-machine env default`

#Run the script 
This will get your docker machine ready to run docker
`eval "$(docker-machine env default)"`

#Get ip address of your docker machine. You will need this later to connect to your container from dev center
`docker-machine ls default`

#Build cassandra docker image
`cd /<path to docker repo>/cassandra/dev-single-node-ssl`
`docker build -t cassandra/singlenodessl .`


#Start the single node cassandra by mapping out the configuration from the repo to the container
```docker run -d \
    -v /<path to docker repo>/cassandra/dev-single-node-ssl/cassandraconfig/:/etc/cassandra \
    -p 9142:9142 -p 9171:9171 \
    --name dev-cassandra-ssl \
    cassandra/singlenodessl:latest
```

#Configure Dev Center
Use the ip address of the docker machine to configure cqlsh connection to the cassandra local cluster



