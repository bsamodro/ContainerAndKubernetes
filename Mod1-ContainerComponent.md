# Module 1 - Container Components
|User|Password|
|---|---|
|lab||


## Container Components

1. Go to Working Directory
```
cd lab1
```
The full path sould be `/home/ubuntu/nginx-api-gateway-for-k8s/task_01`

2. Edit DockerFile
```
vim Dockerfile
```
To enter interactive mode press i. You should now see INSERT in the bottom left of your web shell. Copy-Paste following code

<details>
<summary>DockerFile</summary>
  
```
FROM nginx
RUN rm -f /etc/nginx/conf.d/default.conf

COPY web.conf /etc/nginx/conf.d/web.conf
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 83/tcp
```
</details>

To close and save the file, press the escape (ESC) key to quit interactive mode. Press the : (colon) key to bring up the vim prompt, then issue the write and quite command: wq. You can exit vim without saving changes by pressing : (colon) and issuing the quit forcefully command: q!

3. Build, tag and run the new container

Podman Build
```
podman build -t appworld:v1 .
```
List Image
```
podman images
```
Run Container
```
podman run -p 83:83 --name app -dit appworld:v1
```
<details>
<summary>Sample</summary>
79869cbf10fe9424cafbc33a64af2ff812215b0bdad69379bb3d661360460628
</details>

4. Show and test new container

a. Show Container
```
podman ps -a
```
b. Curl Container
```
curl http://localhost:83
```

c. Container logs

```
podman logs app
```
<details>
<summary>Logs</summary>
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf is not a file or does not exist
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/12/30 21:08:02 [notice] 1#1: using the "epoll" event method
2023/12/30 21:08:02 [notice] 1#1: nginx/1.25.3
2023/12/30 21:08:02 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14)
2023/12/30 21:08:02 [notice] 1#1: OS: Linux 5.15.0-1051-aws
2023/12/30 21:08:02 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/12/30 21:08:02 [notice] 1#1: start worker processes
2023/12/30 21:08:02 [notice] 1#1: start worker process 15
2023/12/30 21:08:02 [notice] 1#1: start worker process 16
2023/12/30 21:08:02 [notice] 1#1: start worker process 17
2023/12/30 21:08:02 [notice] 1#1: start worker process 18
10.88.0.1 - - [30/Dec/2023:21:08:20 +0000] "GET / HTTP/1.1" 200 117 "-" "curl/7.68.0" "-"
</details>
