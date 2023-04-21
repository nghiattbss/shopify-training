# NodeJS là gì

Node.js là một nền tảng phát triển ứng dụng web được xây dựng trên JavaScript Engine (V8 Engine) của Google Chrome. Node.js cho phép phát triển các ứng dụng web và máy chủ bằng ngôn ngữ JavaScript. 

## Cách setup

## Trên windows

### Bước 1: Tải xuống bản cài đặt Node.js

- Truy cập trang web chính thức của Node.js tại địa chỉ [https://nodejs.org/en/download/](https://github.com/calamuslabs/injective-calamus-finance.git).
- Tải xuống bản cài đặt Node.js cho Windows. Bạn có thể chọn bản 32-bit hoặc 64-bit tùy thuộc vào hệ điều hành của bạn.
### Bước 2: Cài đặt Node.js

- Sau khi tải xuống bản cài đặt, bạn mở file cài đặt đó bằng quyền Administrator.
- Trong hộp thoại cài đặt, chọn "Run" để bắt đầu quá trình cài đặt Node.js trên máy tính của bạn.
- Tiếp tục quá trình cài đặt bằng cách chọn các tùy chọn mặc định hoặc tùy chỉnh theo nhu cầu của bạn.
### Bước 3: Kiểm tra cài đặt Node.js

- Mở Command Prompt hoặc PowerShell trên Windows.
- Nhập lệnh sau để kiểm tra phiên bản Node.js đã cài đặt trên máy tính của bạn: node -v.
- Nhập lệnh sau để kiểm tra phiên bản npm (Node Package Manager) đã cài đặt trên máy tính của bạn: npm -v.
- Ngoài cách cài đặt trên trang web chính thức, bạn cũng có thể cài đặt Node.js bằng một số công cụ quản lý gói như Chocolatey hoặc NVM (Node Version Manager).

### Trên Linux

Sử dụng các lệnh sau:
- `sudo apt-get update`
- `sudo apt-get install curl`
- `curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
  sudo apt-get install -y nodejs`

Lưu ý: Bạn có thể thay đổi phiên bản của NodeJS bằng cách thay đổi số phiên bản trong lệnh setup_x.x (vd: setup_16.x để cài đặt phiên bản NodeJS 16).

- Kiểm tra phiên bản: `node -v`

### Cài đặt sử dụng NVM trên Linux

- Cài đặt NVM: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash`
- Khởi động lại terminal hoặc nhập lệnh sau để sử dụng NVM ngay lập tức: `source ~/.bashrc`
- Kiểm tra phiên bản NVM đã được cài đặt bằng lệnh: `nvm --version`
- Cài đặt phiên bản NodeJS mới nhất bằng lệnh: `nvm install node`
- Kiểm tra phiên bản NodeJS đã được cài đặt bằng lệnh: `node --version`
- Để sử dụng phiên bản NodeJS vừa cài đặt, nhập lệnh sau: `nvm use node`