# Getting started

## Update the project
To update the project, you need to **rebuild** your image, so it will have 
the latest changes, and then run a **new container** based on that image.

### Delete docker container (if running):

#### Get the container ID
```
docker ps
```
#### Stop and remove(`rm`) container
`-f` (short for --force) stops the container\
`rm` remove container
```
docker rm -f <the-container-id>
```

### Create new image and run new container:
#### Create a new image
`.` stands for current file\
`-t` flag tags your image
```
 docker build -t <tag-name-for-image> .
```
#### Run new container
`-d` (short for --detach) runs the container in the background\
`-p` (short for --publish) creates a port mapping between the host and the container
`run` run new container based on provided image
```
docker run -dp 127.0.0.1:3000:3000 <image-tag|id>
```

## Persist the state
To persist the state, you need to create a **volume**
and mount it with the container
#### Create a volume
```
docker volume create <volume-name>
```
#### Run container with the volume
```
docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=<volume-name>,target=<path/to/where/store/data> <image-tag|id>
```