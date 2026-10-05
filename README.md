**Docker** là nền tảng đóng gói phần mềm và các phụ thuộc (dependencies) của nó vào một môi trường độc lập gọi là **Container**.

Mục đích chính của Docker là giải quyết triệt để sự cố kinh điển: *"Code chạy ngon trên máy tôi nhưng sang máy người khác lại lỗi"*.

---

### 1. 3 Khái niệm cốt lõi bắt buộc phải biết

* **Dockerfile**: File kịch bản chứa các dòng lệnh hướng dẫn Docker từng bước để tạo ra một **Image** (giống như bản thiết kế hay công thức nấu ăn).
* **Image**: Bản đóng gói tĩnh chứa mã nguồn, môi trường thực thi, thư viện và file cấu hình. Image chỉ đọc (read-only) và có thể chia sẻ lên Docker Hub.
* **Container**: Thể hiện đang chạy (runtime instance) của một Image. Bạn có thể hiểu Image là "lớp/class" còn Container là "đối tượng/object".

```
[Dockerfile] ---> (Build) ---> [Image] ---> (Run) ---> [Container]

```

---

### 2. Sự khác biệt giữa Container và Virtual Machine (VM)

| Tiêu chí | Virtual Machine (Máy ảo) | Docker Container |
| --- | --- | --- |
| **Hệ điều hành** | Mỗi VM chạy một OS riêng (Guest OS nặng vài GB) | Dùng chung Kernel OS của máy host (nhẹ vài MB - vài trăm MB) |
| **Tốc độ khởi động** | Tốn vài phút | Vài giây hoặc miligiây |
| **Tài nguyên** | Tốn nhiều CPU, RAM, ổ cứng | Rất ít, tối ưu hiệu năng |

---

### 3. Workflow cơ bản khi làm việc với Docker

1. **Viết `Dockerfile**` ở thư mục gốc dự án:
```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]

```


2. **Build Image**:
```bash
docker build -t my-app .

```


3. **Chạy Container**:
```bash
docker run -d -p 3000:3000 --name app-test my-app

```



---

### 4. 5 Lệnh Docker dùng nhiều nhất

* `docker ps`: Xem danh sách container đang chạy.
* `docker run`: Tạo và chạy container mới từ image.
* `docker exec -it <tên_container> bash`: Chui vào terminal bên trong container đang chạy.
* `docker logs -f <tên_container>`: Xem log realtime để debug.
* `docker compose up -d`: Chạy toàn bộ hệ thống gồm nhiều container (App + DB) chỉ bằng 1 lệnh.