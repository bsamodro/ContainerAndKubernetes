# Module 1 - Container Components
|User|Password|
|---|---|
|lab|f5Appw0rld!|

## Access Jumphost

1. Connect to Jumphost then open Webshell
<img width="1000" alt="VSwithPolicy" src="https://github.com/bsamodro/ContainerAndKubernetes/blob/25149847079af251784e5fe6808f3ef1e043335c/images/jumphost_webshell2.png">

## Container

2. Go to Working Directory
```
cd lab1
```
  The full path sould be `/lab1`

3. Edit DockerFile
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

4. Build, tag and run the new container

- Podman Build
```
podman build -t appworld:v1 .
```
- List Image
```
podman images
```
- Run Container
```
podman run -p 83:83 --name app -dit appworld:v1
```

5. Show and test new container

- Show Container
```
podman ps -a
```
- Curl Container
```
curl http://localhost:83
```

- Container logs

```
podman logs app
```
