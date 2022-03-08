# ceevee
`docker run --name ceevee --rm -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
```
docker: Error response from daemon: Conflict. The container name "/ceevee" is already in use by container "1aaf5fb8664ae7f16201ef10ecfa7e4f17c4a0c31fa658cbb283731c0a02b595". You have to remove (or rename) that container to be able to reuse that name.
See 'docker run --help'.
```
### List containers
`docker ps`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS         PORTS                                   NAMES
23cc2befcc92   quay.io/j0hnniewa1ker/ceevee   "/docker-entrypoint.…"   15 minutes ago   Up 15 minutes   0.0.0.0:8083->80/tcp, :::8083->80/tcp   ceevee
```
`docker ps --help`
### Display a live stream of container(s) resource usage statistics
`docker stats`
```
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT     MEM %     NET I/O          BLOCK I/O         PIDS
1aaf5fb8664a   ceevee    0.00%     4.094MiB / 3.842GiB   0.10%     29.6kB / 317kB   12.3kB / 8.19kB   5
ctrl-c to quit
```
`docker stats --help`
### Stop one or more running containers
`docker stop ceevee`

`docker stop --help`

### Run ceevee without the --rm (Automatically remove the container when it exits)
`docker run --name ceevee -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`

`docker stop ceevee`

`docker run --name ceevee -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
```
docker: Error response from daemon: Conflict. The container name "/ceevee" is already in use by container "2ad61fe5424d1232055fbdacdfaa4ce29dfa06530002baf5668f76648da5bb28". You have to remove (or rename) that container to be able to reuse that name.
See 'docker run --help'.
```
### Show all containers (default shows just running)
`docker ps -a`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS                     PORTS     NAMES
2ad61fe5424d   quay.io/j0hnniewa1ker/ceevee   "/docker-entrypoint.…"   7 minutes ago   Exited (0) 7 minutes ago             ceevee
```
`docker start ceevee`
```
ceevee
```
`docker ps -a`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS                  PORTS                                   NAMES
2ad61fe5424d   quay.io/j0hnniewa1ker/ceevee   "/docker-entrypoint.…"   10 minutes ago   Up About a minute       0.0.0.0:8083->80/tcp, :::8083->80/tcp   ceevee
```
### Remove one or more containers
`docker rm ceevee`
```
Error response from daemon: You cannot remove a running container 2ad61fe5424d1232055fbdacdfaa4ce29dfa06530002baf5668f76648da5bb28. Stop the container before attempting removal or force remove
```
`docker rm --help`

`docker rm -f ceevee` or `docker stop ceevee && docker rm ceevee`
```
ceevee
```
`docker ps -a`
```      
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

### Run ceevee without the --name `ceevee` (Assign a name to the container)
`docker run -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
``` 
2c166fd4e5c86717e518aaf2f73ade5e79437976d01aa913cabaf06d9cf2a6aa
```
`docker ps`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS          PORTS                                   NAMES
2c166fd4e5c8   quay.io/j0hnniewa1ker/ceevee   "/docker-entrypoint.…"   33 seconds ago   Up 32 seconds   0.0.0.0:8083->80/tcp, :::8083->80/tcp   xenodochial_nightingale
```
without the --name a container will get a random name like `xenodochial_nightingale`. you can run commands using it or the ID `2c166fd4e5c8`

`docker rm -f 2c166fd4e5c8`
```
2c166fd4e5c8
```

`docker run --name ceevee -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
``` 
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/03/08 04:54:19 [notice] 1#1: using the "epoll" event method
2022/03/08 04:54:19 [notice] 1#1: nginx/1.21.6
2022/03/08 04:54:19 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/03/08 04:54:19 [notice] 1#1: OS: Linux 5.10.47-linuxkit
2022/03/08 04:54:19 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/03/08 04:54:19 [notice] 1#1: start worker processes
2022/03/08 04:54:19 [notice] 1#1: start worker process 33
2022/03/08 04:54:19 [notice] 1#1: start worker process 34
2022/03/08 04:54:19 [notice] 1#1: start worker process 35
2022/03/08 04:54:19 [notice] 1#1: start worker process 36
Press Ctrl-P, followed by Ctrl-Q, to detach from your connection. 
```
this isn't working will try in fedora tomorrow