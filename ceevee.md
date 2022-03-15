# ceevee
## My version of Hello 
- [repo](https://github.com/J0hnnieWa1ker/resumetemplate)
- [image](https://quay.io/repository/j0hnniewa1ker/ceevee)

### Commands this demo covers
help | podman docs
---- | ----
`podman --help` | https://docs.docker.com/engine/reference/commandline/cli/
`podman run --help` | https://docs.docker.com/engine/reference/run/
`podman ps --help` | https://docs.docker.com/engine/reference/commandline/ps/
`podman stats --help` | https://docs.docker.com/engine/reference/commandline/stats/
`podman stop --help` | https://docs.docker.com/engine/reference/commandline/stop/
`podman start --help` | https://docs.docker.com/engine/reference/commandline/start/
`podman rm --help` | https://docs.docker.com/engine/reference/commandline/rm/

### Run a command in a new container
Did you run this in the [README](README.md)? Try it again.

`podman run --name ceevee --rm -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
```
podman: Error response from daemon: Conflict. The container name "/ceevee" is already in use by container "1aaf5fb8664ae7f16201ef10ecfa7e4f17c4a0c31fa658cbb283731c0a02b595". You have to remove (or rename) that container to be able to reuse that name.
See 'podman run --help'.
```
If it wasn't already running, run it again.

`podman run --help`

### List containers
`podman ps`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS         PORTS                                   NAMES
23cc2befcc92   quay.io/j0hnniewa1ker/ceevee   "/podman-entrypoint.…"   15 minutes ago   Up 15 minutes   0.0.0.0:8083->80/tcp, :::8083->80/tcp   ceevee
```
`podman ps --help`
### Display a live stream of container(s) resource usage statistics
`podman stats`
```
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT     MEM %     NET I/O          BLOCK I/O         PIDS
1aaf5fb8664a   ceevee    0.00%     4.094MiB / 3.842GiB   0.10%     29.6kB / 317kB   12.3kB / 8.19kB   5
```
ctrl-c to quit

`podman stats --help`
### Stop one or more running containers
`podman stop ceevee`

`podman stop --help`

### Run ceevee without the --rm (Automatically remove the container when it exits)
`podman run --name ceevee -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`

`podman stop ceevee`

`podman run --name ceevee -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
```
podman: Error response from daemon: Conflict. The container name "/ceevee" is already in use by container "2ad61fe5424d1232055fbdacdfaa4ce29dfa06530002baf5668f76648da5bb28". You have to remove (or rename) that container to be able to reuse that name.
See 'podman run --help'.
```
### Show all containers (default shows just running)
`podman ps -a`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS                     PORTS     NAMES
2ad61fe5424d   quay.io/j0hnniewa1ker/ceevee   "/podman-entrypoint.…"   7 minutes ago   Exited (0) 7 minutes ago             ceevee
```
`podman start ceevee`
```
ceevee
```
`podman start --help`

`podman ps -a`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS                  PORTS                                   NAMES
2ad61fe5424d   quay.io/j0hnniewa1ker/ceevee   "/podman-entrypoint.…"   10 minutes ago   Up About a minute       0.0.0.0:8083->80/tcp, :::8083->80/tcp   ceevee
```
### Remove one or more containers
`podman rm ceevee`
```
Error response from daemon: You cannot remove a running container 2ad61fe5424d1232055fbdacdfaa4ce29dfa06530002baf5668f76648da5bb28. Stop the container before attempting removal or force remove
```
`podman rm --help`

`podman rm -f ceevee` or `podman stop ceevee && podman rm ceevee`
```
ceevee
```
`podman ps -a`
```      
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

### Run ceevee without the `--name ceevee` (Assign a name to the container)
`podman run -d -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
``` 
2c166fd4e5c86717e518aaf2f73ade5e79437976d01aa913cabaf06d9cf2a6aa
```
`podman ps`
```
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS          PORTS                                   NAMES
2c166fd4e5c8   quay.io/j0hnniewa1ker/ceevee   "/podman-entrypoint.…"   33 seconds ago   Up 32 seconds   0.0.0.0:8083->80/tcp, :::8083->80/tcp   xenodochial_nightingale
```
without the --name a container will get a random name like `xenodochial_nightingale`. you can run commands using it or the ID `2c166fd4e5c8`

`podman rm -f 2c166fd4e5c8`
```
2c166fd4e5c8
```
### Run ceevee without the `-d` (Run container in background and print container ID)
`podman run --name ceevee -p 8083:80 quay.io/j0hnniewa1ker/ceevee`
``` 
/podman-entrypoint.sh: /podman-entrypoint.d/ is not empty, will attempt to perform configuration
/podman-entrypoint.sh: Looking for shell scripts in /podman-entrypoint.d/
/podman-entrypoint.sh: Launching /podman-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/podman-entrypoint.sh: Launching /podman-entrypoint.d/20-envsubst-on-templates.sh
/podman-entrypoint.sh: Launching /podman-entrypoint.d/30-tune-worker-processes.sh
/podman-entrypoint.sh: Configuration complete; ready for start up
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
```
Without the -d (detached) switch the container process will attach to the console and display the `STDIN`, `STDOUT` and `STDERR` output.

open http://localhost:8083 in a browser
```
...
(Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15" "-"
172.17.0.1 - - [08/Mar/2022:16:16:29 +0000] "GET /service-worker.js HTTP/1.1" 200 3164 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15" "-"
172.17.0.1 - - [08/Mar/2022:16:16:29 +0000] "GET /index.html?_sw-precache=f00b29756c4118ca323482891a193d6f HTTP/1.1" 200 1680 "http://localhost:8083/service-worker.js" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15" "-"
172.17.0.1 - - [08/Mar/2022:16:16:29 +0000] "GET /favicon.ico HTTP/1.1" 200 3870 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15" "-"
```
ctrl-c to quit


How to see the output when running a detached container and the -p (Publish a container's port(s) to the host): [nexus3](nexus3.md)