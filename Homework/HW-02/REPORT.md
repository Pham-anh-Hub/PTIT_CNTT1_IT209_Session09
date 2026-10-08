# Bài 2: Khởi chạy Web Server Nginx với Port Mapping

```bash
user_docker@ip-172-31-42-200:~$ docker run -d -p 8080:80 --name my-web nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
e72112c14215: Pull complete
9a9a644fdd6a: Pull complete
64c8194480fe: Pull complete
e76228b47809: Pull complete
745dfb2690dd: Pull complete
e2de96513ba9: Pull complete
d9aae54b5831: Pull complete
6c53d0b2a666: Pull complete
0deea27e58d9: Download complete
d54d3939625e: Download complete
Digest: sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1abeac2
Status: Downloaded newer image for nginx:alpine
4e7ca79fb776d2d7b0efce86529c4b68317561e4e4b4368f351f75fec2d9d751


user_docker@ip-172-31-42-200:~$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
4e7ca79fb776   nginx:alpine   "/docker-entrypoint.…"   17 seconds ago   Up 17 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web
user_docker@ip-172-31-42-200:~$ curl http://localhost:8080
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy,
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>



user_docker@ip-172-31-42-200:~$ docker stop my-web && docker rm my-web
my-web
my-web
```