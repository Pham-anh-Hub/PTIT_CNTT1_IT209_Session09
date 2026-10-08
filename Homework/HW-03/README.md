# Bài 3: Tối ưu hóa dung lượng Image và Layer Caching với Multi-stage Build

```bash
user_docker@ip-172-31-42-200:~$ mkdir -p homework/session_09/ex3
user_docker@ip-172-31-42-200:~$ cd homework/session_09/ex3
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ echo "<h1>Hello Docker Session 09!</h1>" > index.html
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ cat << 'EOF' > Dockerfile
> FROM nginx:alpine
> COPY index.html /usr/share/nginx/html/index.html
> EOF
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker build -t my-html-app:v1 .
[+] Building 1.9s (7/7) FINISHED                                                                         docker:default
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 104B                                                                               0.0s
 => [internal] load metadata for docker.io/library/nginx:alpine                                                    0.0s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load build context                                                                                  0.1s
 => => transferring context: 71B                                                                                   0.0s
 => [1/2] FROM docker.io/library/nginx:alpine@sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1ab  1.2s
 => => resolve docker.io/library/nginx:alpine@sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1ab  0.0s
 => => extracting sha256:e2de96513ba9eb53b431787ec8a65cdde380ac4772a3e4c4b714dcfde2a102b5                          0.1s
 => => extracting sha256:d9aae54b58315e84b9c3ac5f00bad6610e0e28ad9ff28fcde694647e0be13131                          0.1s
 => => extracting sha256:6c53d0b2a666ed8f8fad8d9982e30cf24eb085036c17b27591665ca25e1ba40c                          0.0s
 => => extracting sha256:745dfb2690dd8627e1593941caccc756f14943df7930a478beb4e808c5695cb9                          0.0s
 => => extracting sha256:9a9a644fdd6a3681d43dace44c8cfef374cfd7b24f433113379ea483692498a8                          0.0s
 => => extracting sha256:64c8194480fee2c03e01cc561cf5542733627d2c7de493a028139677025f975c                          0.0s
 => => extracting sha256:e76228b47809e8a4bd37a6ba52a04d282d8c72ddf0ff9e8b83fd6318631abd52                          0.0s
 => => extracting sha256:e72112c14215406dc7f23ef8e5cfdfddeb8662176167382ad64ec86f52b7a88e                          0.6s
 => [2/2] COPY index.html /usr/share/nginx/html/index.html                                                         0.1s
 => exporting to image                                                                                             0.3s
 => => exporting layers                                                                                            0.1s
 => => exporting manifest sha256:9e38799ad5045a420373b7b560a56ce74d79176345db95a1c9823bddeeed07ef                  0.0s
 => => exporting config sha256:db15963b20fa5b772ee007218f26530a5b29228a3964f192653c05fb5b41866e                    0.0s
 => => exporting attestation manifest sha256:d418293e3ffff3a6cd27b7d3d69c77e1a49707f3fcdb2b1c5406765d491c64bd      0.0s
 => => exporting manifest list sha256:24f765718332e1e94ba0f9c3737ca6310683e5426182e189a9b48770ea06355c             0.0s
 => => naming to docker.io/library/my-html-app:v1                                                                  0.0s
 => => unpacking to docker.io/library/my-html-app:v1                                                               0.0s
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker run -d -p 8081:80 --name html-app my-html-app:v1
5d15d416a4c524e5f3c3a7faccf6137c1fca749e473d8d9fab875e14ace2962c
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ curl http://localhost:8081
<h1>Hello Docker Session 09!</h1>
```