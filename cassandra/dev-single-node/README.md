#Description
This repo contains a Dockerfile that will create a local cassandra container configured minus the SSL configuration

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
`cd <path to docker repo>/cassandra/dev-single-node`
`docker build -t cassandra/singlenode .`


#Start the single node cassandra by mapping out the configuration from the repo to the container
```docker run -d \
    -v /<path to docker repo>/cassandra/dev-single-node/cassandraconfig/:/etc/cassandra \
    -p 9042:9042 \
    --name dev-cassandra \
    cassandra/singlenode:latest
```

#Configure Dev Center
Use the ip address of the docker machine to configure cqlsh connection to the cassandra local cluster



