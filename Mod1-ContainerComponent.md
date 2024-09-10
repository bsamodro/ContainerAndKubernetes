# Module 1 - Container Components
|User|Password|
|---|---|
|lab||


## Container Components

1.
```
cd lab1
```
The full path sould be `/home/ubuntu/nginx-api-gateway-for-k8s/task_01`

2.
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
