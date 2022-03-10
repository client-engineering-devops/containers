# nexus3

https://hub.docker.com/r/sonatype/nexus3

`podman run -d -p 8081:8081 --name nexus sonatype/nexus3`
```
✔ docker.io/sonatype/nexus3:latest
Trying to pull docker.io/sonatype/nexus3:latest...
Getting image source signatures
Copying blob 0d875a68bf99 done  
Copying blob a970fe737b83 done  
Copying blob 8dfe9326f733 done  
Copying blob c1a2af48c694 done  
Copying blob 18238e9f24c5 done  
Copying config 1e1d45f195 done  
Writing manifest to image destination
Storing signatures
7ad23835aa006be052766d83fc2bd9a5fb030c5d5eeb9a00bdf7c43ba08207c9
```
### Retrieves logs for one or more containers.
`podman logs -f nexus`
```
2022-03-10 01:35:10,526+0000 INFO  [jetty-main-1] *SYSTEM org.eclipse.jetty.server.Server - Started @47435ms
2022-03-10 01:35:10,526+0000 INFO  [jetty-main-1] *SYSTEM org.sonatype.nexus.bootstrap.jetty.JettyServer - 
-------------------------------------------------

Started Sonatype Nexus OSS 3.38.0-01

-------------------------------------------------
```
ctrl-c to quit

`podman logs --help`
### Execute the specified command inside a running container.
`podman exec -it nexus bash`
```
bash-4.4$ less /nexus-data/admin.password 
bash: less: command not found
bash-4.4$ cat /nexus-data/admin.password 
e578e9fc-ba78-4299-86a4-e6bbd303650ebash-4.4$ exit
```
`podman exec --help`

open http://localhost:8081 in a browser

sign in and create a user for yourself

`podman stop nexus`
```
nexus
```
http://localhost:8081 is no longer accessable

`podman start nexus`
```
nexus
```

`podman logs -f nexus` to see when it's ready

http://localhost:8081 can you login?

`podman rm -f nexus`
```
7ad23835aa006be052766d83fc2bd9a5fb030c5d5eeb9a00bdf7c43ba08207c9
```

`podman run -d -p 8081:8081 --name nexus sonatype/nexus3`
```
8c0bb9941a42b14bc1727a3711363fd96e9445bb2263c453d4873140824dd765
```
`podman logs -f nexus` to see when it's ready

http://localhost:8081 can you login?

Containers have a read/write layer that is retained if you stop them but if you delete the container is dissapears.

`podman rm -f nexus`

### Volumes are created in and can be shared between containers
`podman volume --help`

`podman run --help`
-  -v, --volume stringArray     Bind mount a volume into the container
-  -P, --publish-all            Publish all exposed ports to random ports on the host interface


Introducing a twist with adding port 80, and touch about Rootless containers 

### Publish all exposed ports to random ports on the host interface
`podman run -d -p 8081:8081 -p 80:8082 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`
```
Error: rootlessport cannot expose privileged port 80, you can add 'net.ipv4.ip_unprivileged_port_start=80' to /etc/sysctl.conf (currently 1024), or choose a larger port number (>= 1024): listen tcp 0.0.0.0:80: bind: permission denied
```
`sudo podman run -d -p 8081:8081 -p 80:8082 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`
```
d362f8abbcee8018ee2e5ff83ad7c93341d0b275f45f86e481ed11433202b958
```

`sudo podman volume ls`
DRIVER      VOLUME NAME
local       nexus-data

`podman volume --help`

`sudo podman volume inspect nexus-data`
```
[
    {
        "Name": "nexus-data",
        "Driver": "local",
        "Mountpoint": "/var/lib/containers/storage/volumes/nexus-data/_data",
        "CreatedAt": "2022-03-09T19:08:39.681345199-08:00",
        "Labels": {},
        "Scope": "local",
        "Options": {},
        "UID": 200,
        "GID": 200
    }
]
```
`sudo cat /var/lib/containers/storage/volumes/nexus-data/_data/admin.password`

`sudo podman logs -f nexus` to see when it's ready

open http://localhost:8081 in a browser

- Create User
- Create Repository: docker (hosted)
  - Create HTTP: with port 8082
  - Allow anonymous docker pull ( Docker Bearer Token Realm required )
- Docker Bearer Token Realm required




`podman stop -t 120 nexus`
```
nexus
```
`podman rm nexus`
```
b82889f42a66bedf12b102e5726315e6205eba5b9da85fbda86a108ef17ae305
```


`podman run -d -p 8081:8081 -p 80:8082 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`
```
Error: rootlessport cannot expose privileged port 80, you can add 'net.ipv4.ip_unprivileged_port_start=80' to /etc/sysctl.conf (currently 1024), or choose a larger port number (>= 1024): listen tcp 0.0.0.0:80: bind: permission denied
```


`sudo podman volume inspect nexus-data`
```
[
    {
        "Name": "nexus-data",
        "Driver": "local",
        "Mountpoint": "/var/lib/containers/storage/volumes/nexus-data/_data",
        "CreatedAt": "2022-03-09T18:52:48.363338074-08:00",
        "Labels": {},
        "Scope": "local",
        "Options": {},
        "UID": 200,
        "GID": 200
    }
]
```






_____________________________________________________

`podman run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`


`docker run -d -p 8081:8081 -p 8082:8082 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`

docker login localhost:8082


https://projectatomic.io/blog/2018/05/podman-tls/
https://www.techrepublic.com/article/how-to-set-up-a-local-image-repository-with-podman/
https://www.redhat.com/sysadmin/manage-container-registries