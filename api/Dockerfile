# Sử dụng một base image có Python 3.9
FROM python:3.11-slim

# Đặt biến môi trường để tắt lời nhắc nhập đầu vào của các công cụ CLI
ENV PYTHONUNBUFFERED 1

# Cài đặt các gói phụ thuộc hệ thống
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Tạo và đặt thư mục làm việc
WORKDIR /backend/app

# Sao chép tệp requirements.txt vào thư mục làm việc
COPY requirements.txt .

# Cài đặt các gói phụ thuộc từ requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Sao chép toàn bộ mã nguồn vào thư mục làm việc
COPY . .

# Mở cổng 8000
EXPOSE 8000

# Lệnh để chạy ứng dụng FastAPI
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]