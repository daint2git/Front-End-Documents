# Docker

- có hai khái niệm chính cần hiểu, đó là `image` và `container`

## Container

- Tương tự như một máy ảo, xuất hiện khi mình khởi chạy `image`.
- Tốc độ khởi chạy container nhanh hơn tốc độ khởi chạy máy ảo rất nhiều và bạn có thể thoải mái chạy 4,5 container mà không sợ treo máy.
- Các files và settings được sử dụng trong container được lưu, sử dụng lại, gọi chung là images của docker.

## Image

- Tương tự như file .gho để ghost win mà mấy ông cài win dạo hay dùng.
- Image này không phải là một file vật lý mà nó chỉ được chứa trong Docker.
- Một image bao gồm hệ điều hành (Windows, CentOS, Ubuntu, …) và các môi trường lập trình được cài sẵn (httpd, mysqld, nginx, python, git, …).
- Docker hub là nơi lưu giữ và chia sẻ các file images này (hiện có khoảng 300.000 images)

## Các câu lệnh trong Docker

| Lệnh | Ý nghĩa |
|--------|------|
| `docker pull {image_name}` | Pull một image từ Docker Hub |
| `docker run --name {container_name} -p {host_port}:{container_port} -v {/host_path}:{/container_path} -it {image_name}` | Tạo mới một container, đồng thời khởi động với tùy chọn cổng và volume |
| `docker images` | Liệt kê các images hiện có |
| `docker rmi {image_id/name}` | Xóa một image |
| `docker rmi $(docker images -q)` | Xóa các images hiện có |
| `docker container ls` | Liệt kê các containers hiện có |
| `docker ps` | Liệt kê các container đang chạy |
| `docker ps -a` | Liệt kê các container đã tắt |
| `docker rm -f {container_id/name}` | Xóa một container |
| `docker rm $(docker ps -a -q)` | Xóa các containers hiện có |
| `docker start {new_container_name}` | Khởi động một container |
| `docker exec -it {new_container_name} /bin/bash` | Truy cập vào container đang chạy |

## Dockerfile
- là một file dạng text, không có đuôi, giúp thiết lập `cấu trúc` cho `docker image` nhờ chứa một tập hợp các `câu lệnh`.
- Từ những câu lệnh đó, Docker có thể thực hiện `đóng gói` một docker images theo yêu cầu tùy biến của riêng bạn.
- Như vậy Dockerfile sẽ `quy định` Docker image được khởi tạo `từ đâu`, gồm `những gì` trong đó.

## Cách viết Dockerfile

### Thiết lập image gốc
Ví dụ:
```
FROM ubuntu:16.04
```
### Cài đặt ứng dụng

| Lệnh | Ý nghĩa |
|--------|------|
| RUN | thực thi một câu lệnh nào đó trong quá trình build images. |
| CMD | thực thi một câu lệnh trong quá trình bật container. |
| ENTRYPOINT | thực thi một số câu lệnh trong quá trình start container, những câu lệnh này sẽ được viết trong file .sh. |

Lưu ý:
- Mỗi Dockerfile `chỉ có` một câu lệnh CMD, nếu như có `nhiều hơn` một câu lệnh CMD thì chỉ có câu lệnh CMD `cuối cùng` được sử dụng.
- Một `câu hỏi` đặt ra là nếu tôi muốn khởi động `nhiều ứng dụng` khi start container thì sao, lúc đó hay nghĩ tới `ENTRYPOINT`

### Cấu hình

| Lệnh | Ý nghĩa |
|--------|------|
| EXPOSE | Container sẽ lắng nghe trên các cổng mạng được chỉ định khi chạy |
| ADD | Copy file, thư mục, remote file thêm chúng vào filesystem của image. |
| COPY | Copy file, thư mục từ host machine vào image. Có thể sử dụng url cho tập tin cần copy. |
| WORKDIR | Định nghĩa directory cho `CMD` |
| VOLUME | Mount thư mục từ máy host vào container. |

## Cách sử dụng Dockerfile

### Build docker image từ Dockerfile

```
docker build -t <image_name> .
```
Ví dụ:
```
docker build -t ubuntu_nginx .
```
- Tùy chọn `-t` giúp bạn có thể chọn tên cho image bạn tạo ra.
- Tùy chọn `.` cho biết file Dockerfile đang ở cùng đường dẫn.

### Tạo container từ image

```
docker run -v <forder_in_computer>:<forder_in_container> -p <port_in_computer>:<port_in_container> -it <image_name>
```
Trong đó:
- -v : Thể hiện việc mount volume, dữ liệu từ thư mục từ máy thật có thể được truy cập từ thư mục của máy ảo.
- -p: Cổng mạng từ máy thật để dẫn tới cổng mạng của máy ảo đang chạy.
- -t: Chạy container và mở terminal bằng /bin/bash

Ví dụ vào localhost mặc định của nginx:
```
docker run -p 9000:80 -it nginx
```

# Docker Hub

- Nơi lưu trữ và chia sẻ các image của Docker, nhưng không chỉ có vậy

