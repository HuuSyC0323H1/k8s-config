# Static Web Application (STG)

Trang web tĩnh hiện đại, nhẹ nhàng, tối ưu hóa responsive, giao diện Light/Dark mode và sẵn sàng triển khai trên Kubernetes/Docker.

## 📁 Cấu trúc thư mục

```text
static-web-app/
├── index.html        # Trang giao diện chính
├── css/
│   └── style.css     # CSS Variables, hiệu ứng, responsive, dark/light theme
├── js/
│   └── main.js       # Script chuyển theme, menu mobile, tương tác form
├── nginx.conf        # Cấu hình Nginx tối ưu cache & endpoint /healthz cho K8s
├── Dockerfile        # File build image Nginx Alpine siêu nhẹ
└── README.md         # Tài liệu hướng dẫn
```

## 🚀 Cách chạy và kiểm tra

### 1. Mở trực tiếp trên trình duyệt
Bạn có thể mở trực tiếp file `index.html` bằng bất kỳ trình duyệt nào (Chrome, Edge, Firefox, ...).

### 2. Chạy với máy chủ cục bộ (Local Server)
Sử dụng Python:
```bash
python -m http.server 8080
```
Sau đó truy cập [http://localhost:8080](http://localhost:8080).

### 3. Build & Run với Docker
```bash
# Build image
docker build -t static-web-app:stg .

# Run container
docker run -d -p 8080:80 --name static-web-stg static-web-app:stg
```

### 4. Triển khai Kubernetes (K8s)
File `nginx.conf` đã cung cấp sẵn endpoint `/healthz` để cấu hình `livenessProbe` và `readinessProbe` trong Pod Deployment.
