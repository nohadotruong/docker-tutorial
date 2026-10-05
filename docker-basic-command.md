Dưới đây là danh sách các lệnh Docker cơ bản và được sử dụng nhiều nhất trong quá trình phát triển phần mềm, chia theo từng nhóm công việc cụ thể.

---

### 1. Quản lý Container (Chạy, Theo dõi & Thao tác)

* **`docker ps`**: Liệt kê các container đang chạy.
* `docker ps -a`: Liệt kê tất cả container (kể cả những container đã dừng).


* **`docker run`**: Tạo và khởi chạy một container mới từ image.
* `docker run -d -p 8080:80 --name my-app nginx`: Chạy ngầm (`-d`), map cổng (`-p host:container`), đặt tên (`--name`).


* **`docker exec`**: Truy cập hoặc chạy lệnh bên trong một container đang chạy.
* `docker exec -it <container_id_hoặc_name> bash` (hoặc `sh`): Truy cập terminal của container.


* **`docker logs`**: Xem nhật ký (logs) của container để debug.
* `docker logs -f <container_id>`: Theo dõi log theo thời gian thực (`-f`).


* **`docker stop <container_id>`**: Dừng container đang chạy.
* **`docker start <container_id>`**: Khởi chạy lại container đã dừng.
* **`docker rm <container_id>`**: Xóa một container đã dừng.
* `docker rm -f <container_id>`: Ép xóa container kể cả khi đang chạy.



---

### 2. Quản lý Docker Image

* **`docker images`**: Liệt kê danh sách các image đang có ở máy địa phương.
* **`docker build`**: Build một image từ `Dockerfile`.
* `docker build -t my-app:v1 .`: Build image với tên/tag là `my-app:v1` tại thư mục hiện tại (`.`).


* **`docker pull <image_name>`**: Tải image từ Docker Hub về máy (ví dụ: `docker pull postgres:latest`).
* **`docker rmi <image_id>`**: Xóa một image khỏi máy.

---

### 3. Docker Compose (Dành cho dự án nhiều service như App + Database)

* **`docker compose up`**: Khởi chạy tất cả các dịch vụ được định nghĩa trong `docker-compose.yml`.
* `docker compose up -d`: Chạy tất cả các dịch vụ ở chế độ ngầm (background).
* `docker compose up --build`: Rebuild lại image trước khi khởi chạy.


* **`docker compose down`**: Dừng và xóa toàn bộ container, network được tạo bởi `docker compose`.
* **`docker compose logs -f <service_name>`**: Xem log của một dịch vụ cụ thể trong compose.
* **`docker compose exec <service_name> <command>`**: Chạy lệnh trong container của dịch vụ (ví dụ: `docker compose exec db psql -U postgres`).

---

### 4. Dọn dẹp Tài nguyên System

* **`docker system prune`**: Xóa các container đã dừng, network không dùng và dangling images để giải phóng dung lượng đĩa.
* `docker system prune -a --volumes`: Dọn dẹp triệt để (bao gồm tất cả image không sử dụng và volume).