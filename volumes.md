# Docker Volumes

## Problem Statement

It is a very common requirement to persist(permanant store) the data in a Docker container beyond the lifetime of the container. However, the file system of a Docker container is deleted/removed when the container dies/down. All the logs files would be removed.

![image](https://github.com/jalaluddinmohammed/Docker-Zero-to-Hero/assets/145260536/798f3441-5c85-4f6a-b7a4-9d42f2c127b2)

Container can access the host CPU, memory etc.. but there is a way to access host file system  and store data on it, it can be acheieved using volumes and mount point.

## Solution

There are 2 different ways how docker solves this problem.

1. Volumes
2. Bind Directory on a host as a Mount

### Volumes 

Volumes aims to solve the same problem by providing a way to store data on the host file system, separate from the container's file system, 
so that the data can persist even if the container is deleted and recreated.

![image](https://user-images.githubusercontent.com/43399466/218018334-286d8949-d155-4d55-80bc-24827b02f9b1.png)


Volumes can be created and managed using the docker volume command. You can create a new volume using the following command:

```
docker volume create <volume_name>
```

Once a volume is created, you can mount it to a container using the -v or --mount option when running a docker run command. 

For example:

```
docker run -it -v <volume_name>:/data <image_name> /bin/bash
```

This command will mount the volume <volume_name> to the /data directory in the container. Any data written to the /data directory
inside the container will be persisted in the volume on the host file system.


![image](https://github.com/jalaluddinmohammed/Docker-Zero-to-Hero/assets/145260536/21242105-34ca-4d7d-978d-a9e737bf8ec4)


![image](https://github.com/jalaluddinmohammed/Docker-Zero-to-Hero/assets/145260536/83f871c2-2f62-4511-96ee-ee338554e714)


### Bind Directory on a host as a Mount

Bind mounts also aims to solve the same problem but in a complete different way.

Using this way, user can mount a directory from the host file system into a container. Bind mounts have the same behavior as volumes, but
are specified using a host path instead of a volume name. 

For example, 

```
docker run -it -v <host_path>:<container_path> <image_name> /bin/bash
```

## Key Differences between Volumes and Bind Directory on a host as a Mount

Volumes are managed, created, mounted and deleted using the Docker API. However, Volumes are more flexible than bind mounts, as 
they can be managed and backed up separately from the host file system, and can be moved between containers and hosts.

Volumes provides high performance.

In a nutshell, Bind Directory on a host as a Mount are appropriate for simple use cases where you need to mount a directory from the host file system into
a container, while volumes are better suited for more complex use cases where you need more control over the data being persisted
in the container.


docker -v <....>

docker  --mount 

Above both commands are same, better to use --mount which is easy to understand.

Bind mount are used for development only because when you deploy the container to PROD then there is not need to have same folder structure on the PROD system. So mainly for source code updates while doing developments then bind mounts are handy. When you update the source code on the docker host file system then an restart of the container helps to automatically replicate the data in the docker host file system to container own file system.

To delete the volume, we need to stop the container, delete the container and then delete volume.

also, when you create volume, the local path is automatically created by the host file system ( it can be s3 or remote file system on ec2)

