# Docker
- Là một nền tảng mở dành cho các lập trình viên, quản trị hệ thống dùng để xây dựng, vận chuyển và chạy các ứng dụng phân tán

## Docker bao gồm các thành phần chính
- `Docker Engine`
  - Là thành phần chính của Docker, như một công cụ để đóng gói ứng dụng
  - Dùng để tạo ra Docker image và chạy Docker container
- `Docker Hub` là dịch vụ cloud để chia sẻ ứng dụng và tự động hóa chuỗi các công việc liên tục, có thể thao tác pull/push với các images

## Docker mang lại những giá trị gì
- Có thể đóng gói mọi ứng dụng vd như webapp, backend, MySQL, BigData…thành các containers và có thể chạy ở `hầu hết` các môi trường vd như Linux, Mac, Window…
- Docker Containers có một API cho phép quản trị các container từ bên ngoài. Giúp cho chúng ta có thể dễ dàng quản lí, thay đổi, chỉnh sửa các container
- Hầu hết các ứng dụng Linux có thể chạy với Docker Containers
- Docker Containers có tốc độ chạy nhanh hơn hẳn các VMs truyền thống (theo kiểu Hypervisor). Điều này là một ưu điểm nổi bật nhất của Docker

## Image
- Là một dạng tập hợp các tệp của ứng dụng, được tạo ra bởi `Docker engine`
- Nội dung của các `Docker image` sẽ không bị thay đổi khi di chuyển
- Là một template chỉ cho phép đọc
- Docker image được dùng để tạo các `Docker container`

> **Giải thích thêm**
> - Tương tự như file .gho để ghost win mà mấy ông cài win dạo hay dùng
> - Image này không phải là một file vật lý mà nó chỉ được chứa trong Docker
> - Một image bao gồm hệ điều hành (Windows, CentOS, Ubuntu, …) và các môi trường lập trình được cài sẵn (httpd, mysqld, nginx, python, git, …)
> - Docker hub là nơi lưu giữ và chia sẻ các Docker image (hiện có khoảng 300.000 images)

## Container
- Là một dạng runtime của các `Docker image`, dùng để làm môi trường chạy ứng dụng
- Hoạt động giống như một thư mục (directory), chứa tất cả những thứ cần thiết để một ứng dụng có thể chạy được
- `Docker container` có thể có các trạng thái `run, started, stopped, moved và deleted`

> **Giải thích thêm**
> - Tương tự như một máy ảo, xuất hiện khi mình khởi chạy `image`
> - Tốc độ khởi chạy container nhanh hơn tốc độ khởi chạy máy ảo rất nhiều và bạn có thể thoải mái chạy 4,5 container mà không sợ treo máy
> - Các files và settings được sử dụng trong container được lưu, sử dụng lại, gọi chung là images của docker

## Các câu lệnh trong Docker
| Lệnh | Ý nghĩa |
|--------|------|
| `docker pull {image_name}` | Pull một image từ Docker Hub |
| `docker run --name {container_name} -p {host_port}:{container_port} -v {/host_path}:{/container_path} -it {image_name}` | Tạo mới một container, đồng thời khởi động với tùy chọn cổng và volume |
| `docker images` | Liệt kê các images hiện có |
| `docker images -a` | Liệt kê các images hiện có |
| `docker images -q` | Liệt kê các images hiện có (Chỉ hiển thị số ID của các images) |
| `docker rmi {image_id/name}` | Xóa một image |
| `docker rmi $(docker images -q)` | Xóa các images hiện có |
| `docker container ls` | Liệt kê các containers hiện có |
| `docker ps` | Liệt kê các container đang chạy |
| `docker ps -a` | Liệt kê các container đã tắt |
| `docker rm -f {container_id/name}` | Xóa một container |
| `docker rm $(docker ps -a -q)` | Xóa các containers hiện có |
| `docker start {new_container_name}` | Khởi động một container |
| `docker exec -it {new_container_name} /bin/bash` | Truy cập vào container đang chạy |
| `docker run` | Thao tác đến các images đã tồn tại hoặc có thể truy xuất từ localhost, mỗi lần chạy command sẽ tạo ra một container mới tương ứng |
| `docker start` | Bắt đầu lại container và khởi động cho container chạy cho đến lần xử lý dừng tiếp theo |

## Dockerfile
- Là một file dạng text (không có đuôi) chứa tập hợp các lệnh để Docker có thể đọc và thực hiện để đóng gói một image theo yêu cầu người dùng

> **Giải thích thêm**
> - Giúp thiết lập `cấu trúc` cho `image`
> - Quy định `image` được khởi tạo `từ đâu`, gồm `những gì` trong đó
> - Từ những câu lệnh trong Dockerfile, Docker có thể thực hiện `đóng gói` một `image` theo yêu cầu tùy biến của riêng bạn

### Các lệnh thông dụng trong Dockerfile
| Lệnh | Ý nghĩa |
|--------|------|
| ENV | Định nghĩa biến môi trường trong `Container` |
| EXPOSE | `Container` sẽ lắng nghe trên các cổng mạng được chỉ định khi chạy |
| ADD | Copy `file, thư mục, remote file` vào một ví trí nào đó trên `Container` |
| COPY | Copy `file, thư mục` từ host machine vào `Image`. Có thể sử dụng url cho tập tin cần copy |
| WORKDIR | Định nghĩa directory cho `CMD` |
| VOLUME | Mount thư mục từ máy host vào container. |
| RUN | thực thi một câu lệnh nào đó trong quá trình `build image` |
| CMD | thực thi một câu lệnh trong quá trình bật `container` |
| ENTRYPOINT | thực thi một số câu lệnh trong quá trình bật `container`, những câu lệnh này sẽ được viết trong file `.sh` |

> **Lưu ý**
> - Mỗi Dockerfile `chỉ có` một câu lệnh `CMD`, nếu như có `nhiều hơn` thì chỉ có câu lệnh `cuối cùng` được sử dụng
> - Một `câu hỏi` đặt ra là nếu tôi muốn khởi động `nhiều ứng dụng` khi bật container thì sao ? Lúc đó hãy nghĩ tới `ENTRYPOINT`

### Cách sử dụng Dockerfile

#### Step 1. Build docker image từ Dockerfile
```
// Cú pháp
docker build -t <image_name> .

// Ví dụ
docker build -t ubuntu_nginx .
```
- `-t` giúp bạn có thể chọn tên cho image bạn tạo ra
- `.` cho biết file Dockerfile đang ở cùng đường dẫn

#### Step 2. Tạo container từ image
```
// Cú pháp
docker run -v <forder_in_computer>:<forder_in_container> -p <port_in_computer>:<port_in_container> -it <image_name>

// Ví dụ vào localhost mặc định của nginx
docker run -p 9000:80 -it nginx
```
- `-v` thể hiện việc mount volume, dữ liệu từ thư mục của máy thật có thể được truy cập từ thư mục của máy ảo
- `-p` cổng mạng từ máy thật để dẫn tới cổng mạng của máy ảo đang chạy
- `-t` chạy container và mở terminal bằng /bin/bash

## Volume
- Được dùng để chia sẻ dữ liệu cho container
> **Ta dùng Docker Volume khi nào ?**
> - Sử dụng volume để gắn (mount) một thư mục nào đó trong host với container
> - Sử dụng volume để chia sẻ dữ liệu giữa host và container
> - Sử dụng volume để chia sẽ dữ liệu giữa các container
> - Backup và Restore volume

## Docker Compose
- Là công cụ giúp định nghĩa và khởi chạy `multi-container Docker applications`
> - Trong Compose, chúng ta sử dụng Compose file để cấu hình application's services. Chỉ với một câu lệnh, lập trình viên có thể dễ dàng create và start toàn bộ các services phục vụ cho việc chạy ứng dụng

### Các câu lệnh trong Docker Compose
| Lệnh | Ý nghĩa |
|--------|------|
| `docker-compose up` | Tạo và khởi động containers |
| `docker-compose build` | Build hoặc rebuild services |
| `docker-compose config` | Xác nhận hoặc hiển thị file config Compose |
| `docker-compose rm` | Loại bỏ, ngừng containers |

