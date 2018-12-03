# Docker

- có hai khái niệm chính cần hiểu, đó là `image` và `container`

## Docker bao gồm các thành phần chính
- `Docker Engine` dùng để tạo ra Docker image và chạy Docker container.
- `Docker Hub` dịch vụ lưu trữ giúp chứa các Docker image.

## Docker mang lại những giá trị gì
- Với Docker, chúng ta có thể đóng gói mọi ứng dụng vd như webapp, backend, MySQL, BigData…thành các containers và có thể chạy ở `hầu hết` các môi trường vd như Linux, Mac, Window…
- Docker Containers có một API cho phép quản trị các container từ bên ngoài. Giúp cho chúng ta có thể dễ dàng quản lí, thay đổi, chỉnh sửa các container.
- Hầu hết các ứng dụng Linux có thể chạy với Docker Containers.
- Docker Containers có tốc độ chạy nhanh hơn hẳn các VMs truyền thống (theo kiểu Hypervisor). Điều này là một ưu điểm nổi bật nhất của Docker.

## Image
- Là một dạng tập hợp các tệp của ứng dụng, được tạo ra bởi `Docker engine`.
- Nội dung của các `Docker image` sẽ không bị thay đổi khi di chuyển.
- Là một template chỉ cho phép đọc.
- Docker image được dùng để tạo các `Docker container`.

> **Giải thích thêm**
> - Tương tự như file .gho để ghost win mà mấy ông cài win dạo hay dùng.
> - Image này không phải là một file vật lý mà nó chỉ được chứa trong Docker.
> - Một image bao gồm hệ điều hành (Windows, CentOS, Ubuntu, …) và các môi trường lập trình được cài sẵn (httpd, mysqld, nginx, python, git, …).
> - Docker hub là nơi lưu giữ và chia sẻ các file images này (hiện có khoảng 300.000 images), có thể download Docker images của người khác tại đây.

## Container
- Là một dạng runtime của các `Docker image`, dùng để làm môi trường chạy ứng dụng.
- Một `Docker container` giữ mọi thứ chúng ta cần để chạy một app.
- `Docker container` có thể có các trạng thái `run, started, stopped, moved và deleted`.

> **Giải thích thêm**
> - Tương tự như một máy ảo, xuất hiện khi mình khởi chạy `image`.
> - Tốc độ khởi chạy container nhanh hơn tốc độ khởi chạy máy ảo rất nhiều và bạn có thể thoải mái chạy 4,5 container mà không sợ treo máy.
> - Các files và settings được sử dụng trong container được lưu, sử dụng lại, gọi chung là images của docker.

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
- Là một file dạng text, không có đuôi và chứa một tập các câu lệnh để tạo một Image trong Docker.

> **Giải thích thêm**
> - Giúp thiết lập `cấu trúc` cho `Docker image`
> - Quy định `Docker image` được khởi tạo `từ đâu`, gồm `những gì` trong đó.
> - Từ những câu lệnh trong Dockerfile, Docker có thể thực hiện `đóng gói` một `Docker image` theo yêu cầu tùy biến của riêng bạn.

## Cách viết Dockerfile

### Thiết lập image gốc
Ví dụ:
```
FROM ubuntu:16.04
```
### Cài đặt ứng dụng

| Lệnh | Ý nghĩa |
|--------|------|
| RUN | thực thi một câu lệnh nào đó trong quá trình `build image` |
| CMD | thực thi một câu lệnh trong quá trình bật `container` |
| ENTRYPOINT | thực thi một số câu lệnh trong quá trình bật `container`, những câu lệnh này sẽ được viết trong file `.sh` |

> **Lưu ý**
> - Mỗi Dockerfile `chỉ có` một câu lệnh `CMD`, nếu như có `nhiều hơn` thì chỉ có câu lệnh `cuối cùng` được sử dụng
> - Một `câu hỏi` đặt ra là nếu tôi muốn khởi động `nhiều ứng dụng` khi bật container thì sao ? Lúc đó hãy nghĩ tới `ENTRYPOINT`

### Cấu hình

| Lệnh | Ý nghĩa |
|--------|------|
| ENV | Định nghĩa biến môi trường trong `Container` |
| EXPOSE | `Container` sẽ lắng nghe trên các cổng mạng được chỉ định khi chạy |
| ADD | Copy `file, thư mục, remote file` vào một ví trí nào đó trên `Container` |
| COPY | Copy `file, thư mục` từ host machine vào `Image`. Có thể sử dụng url cho tập tin cần copy |
| WORKDIR | Định nghĩa directory cho `CMD` |
| VOLUME | Mount thư mục từ máy host vào container. |

## Cách sử dụng Dockerfile

### Build docker image từ Dockerfile

Cú pháp:
```
docker build -t <image_name> .
```
Ví dụ:
```
docker build -t ubuntu_nginx .
```
- `-t` giúp bạn có thể chọn tên cho image bạn tạo ra
- `.` cho biết file Dockerfile đang ở cùng đường dẫn

### Tạo container từ image

```
docker run -v <forder_in_computer>:<forder_in_container> -p <port_in_computer>:<port_in_container> -it <image_name>
```
Trong đó:
- `-v` thể hiện việc mount volume, dữ liệu từ thư mục của máy thật có thể được truy cập từ thư mục của máy ảo.
- `-p` cổng mạng từ máy thật để dẫn tới cổng mạng của máy ảo đang chạy.
- `-t` chạy container và mở terminal bằng /bin/bash.

Ví dụ vào localhost mặc định của nginx:
```
docker run -p 9000:80 -it nginx
```
