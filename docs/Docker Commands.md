# Docker Commands Cheat Sheet

| Chức năng | Lệnh | Mô tả |
|---|---|---|
| Xem container chạy | `docker ps` | Danh sách container running |
| Xem tất cả container | `docker ps -a` | Bao gồm stopped |
| Stop container | `docker stop myapp` | Dừng container |
| Start container | `docker start myapp` | Khởi động lại |
| Restart container | `docker restart myapp` | Restart container |
| Xóa container | `docker rm myapp` | Remove container |
| Force remove | `docker rm -f myapp` | Force remove |
| Xem logs | `docker logs myapp` | Xem log |
| Follow logs | `docker logs -f myapp` | Xem log realtime |
| Exec bash | `docker exec -it myapp bash` | Vào shell container |
| Exec sh | `docker exec -it myapp sh` | Vào shell sh |
| **Docker Images** |  |  |
| Build image | `docker build -t myapp .` | Build image |
| Tag image | `docker tag app v1` | Gắn tag image |
| Push image | `docker push myrepo/app` | Push image |
| Pull image | `docker pull myrepo/app` | Pull image |
| Kiểm tra version Docker | `docker --version` | Hiển thị phiên bản Docker |
| Xem thông tin Docker | `docker info` | Thông tin hệ thống Docker |
| Xem image | `docker images` | Liệt kê image |
| Pull image | `docker pull nginx` | Tải image từ Docker Hub |
| Xóa image | `docker rmi nginx` | Xóa image |
| Chạy container | `docker run nginx` | Chạy container |
| Chạy background | `docker run -d nginx` | Chạy nền |
| Đặt tên container | `docker run --name myapp nginx` | Đặt tên container |
| Mapping port | `docker run -p 8080:80 nginx` | Map port host-container |
| Mount volume | `docker run -v /data:/app nginx` | Gắn thư mục |
| Truyền env | `docker run -e KEY=VALUE nginx` | Set biến môi trường |
| Inspect container | `docker inspect myapp` | Chi tiết container |
| Xem resource | `docker stats` | CPU/RAM usage |
| Copy file vào container | `docker cp file.txt myapp:/tmp/` | Copy host → container |
| Copy file ra host | `docker cp myapp:/tmp/a.txt .` | Copy container → host |
| Xem network | `docker network ls` | Danh sách network |
| Tạo network | `docker network create net1` | Tạo network |
| Xóa network | `docker network rm net1` | Xóa network |
| Xem volume | `docker volume ls` | Danh sách volume |
| Tạo volume | `docker volume create vol1` | Tạo volume |
| Xóa volume | `docker volume rm vol1` | Xóa volume |
| Dọn container stop | `docker container prune` | Xóa stopped container |
| Dọn image unused | `docker image prune` | Xóa image unused |
| Dọn toàn bộ | `docker system prune -a` | Cleanup toàn bộ |
| **Docker Compose** |  |  |
| Compose up | `docker compose up -d` | Start compose |
| Compose down | `docker compose down` | Stop compose |
| Compose logs | `docker compose logs -f` | Logs compose |
| Compose restart | `docker compose restart` | Restart compose |
| Compose ps | `docker compose ps` | Xem service compose |

---

# Docker Run Thường Dùng

| Mục đích | Lệnh |
|---|---|
| Chạy nginx | `docker run -d -p 8080:80 nginx` |
| Chạy mysql | `docker run -d -e MYSQL_ROOT_PASSWORD=123456 mysql:8` |
| Chạy redis | `docker run -d redis` |
| Chạy ubuntu shell | `docker run -it ubuntu bash` |
| Auto restart | `docker run --restart unless-stopped nginx` |

---

# Docker Compose Mẫu

```yaml
version: '3'

services:
  nginx:
    image: nginx
    ports:
      - "8080:80"

  redis:
    image: redis
```
