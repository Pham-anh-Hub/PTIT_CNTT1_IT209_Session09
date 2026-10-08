# Bài 4: Lưu trữ dữ liệu đơn giản với Docker Volume

### 1. Tạo volume mới tên là easy-volume 
```bash
docker volume create easy-volume
```

### 2. Dùng 1 container Alpine ghi nội dung vào volume
```bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt
```

### 3. Dùng 1 container Alpine thứ hai đọc lại tệp đó: 
```bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
```




## Kết quả:
```bash
user_docker@ip-172-31-42-200:~$ cd homework/session_09/ex3
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker volume create easy-volume
easy-volume
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
6d0606d1815c: Download complete
797dd00a0fc7: Download complete
Digest: sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6
Status: Downloaded newer image for alpine:latest
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker run --rm -v easy-volume:/data alpine cat /data/test.txt
Luu tru du lieu Docker
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$  du lieu Docker' > /data/test.txt"
> Unable to find image 'alpine:latest' locally
> latest: Pulling from library/alpine
> 6d0606d1815c: Download complete
> 797dd00a0fc7: Download complete
> Digest: sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6
> Status: Downloaded newer image for alpine:latest
> user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker run --rm -v easy-volume:/data alpine cat /data/test.txt
>
>
> ^C
user_docker@ip-172-31-42-200:~/homework/session_09/ex3$ docker volume ls
DRIVER    VOLUME NAME
local     easy-volume
```