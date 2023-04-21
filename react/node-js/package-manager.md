# NPM là gì

NPM (Node Package Manager) là một trình quản lý gói (package manager) phổ biến cho Node.js. Nó được sử dụng để quản lý các thư viện, module, package cần thiết cho ứng dụng Node.js. NPM có thể tự động tải và cài đặt các thư viện được liệt kê trong file package.json, đồng thời quản lý phiên bản và phân giải các dependencies giữa các thư viện, đảm bảo sự ổn định và tương thích trong quá trình phát triển ứng dụng. Ngoài ra, NPM cũng cung cấp cho người dùng các tính năng như publish, install, uninstall, update package.

- `npm init:` Khởi tạo một package mới và tạo ra file package.json.

- `npm install:` Cài đặt tất cả các module được khai báo trong file package.json.

- `npm install <package-name>:` Cài đặt một package cụ thể.

- `npm install <package-name>@<version-number>:` Cài đặt một phiên bản cụ thể của package.

- `npm install --save <package-name>:` Cài đặt một package và thêm nó vào file dependencies trong file package.json.

- `npm install --save-dev <package-name>:` Cài đặt một package và thêm nó vào file devDependencies trong file package.json.

- `npm update:` Cập nhật tất cả các package lên phiên bản mới nhất.

- `npm update <package-name>:` Cập nhật một package cụ thể lên phiên bản mới nhất.

- `npm uninstall <package-name>:` Gỡ bỏ một package cụ thể.

- `npm search <keyword>:` Tìm kiếm các package có liên quan đến từ khóa.

- `npm outdated:` Kiểm tra các package đã cài đặt nhưng phiên bản đã cũ.

- `npm publish:` Đăng tải package lên registry.

- `npm login:` Đăng nhập vào tài khoản npm.

- `npm whoami:` Hiển thị tên người dùng đang đăng nhập.

- `npm version:` Tăng phiên bản của package.

- `npm run <script-name>:` Chạy một script đã được định nghĩa trong package.json.

- `npm config:` Quản lý cấu hình npm.

- `npm help:` Hiển thị trợ giúp.

## NPM vs NPX

Điểm khác biệt chính giữa NPM và NPX là NPM được sử dụng để quản lý các package Node.js, trong khi đó, NPX được sử dụng để thực thi các package Node.js tạm thời và không cần phải cài đặt chúng.

| NPM | NPX |
|-----|:---:|
|NPM (Node Package Manager) được sử dụng để quản lý các package Node.js|NPX (Node Package Execute) được sử dụng để thực thi các package Node.js|
|NPM có thể cài đặt và quản lý các package Node.js ở cấp toàn cục hoặc cục bộ|NPX cung cấp cách thực thi các package Node.js tạm thời và không cần phải cài đặt chúng|
|NPM yêu cầu phải cài đặt các package trước khi sử dụng chúng|NPX không yêu cầu cài đặt các package trước khi thực thi chúng, chỉ cần chạy lệnh `npx <package>`|
|NPM được sử dụng cho các mục đích như cài đặt, cập nhật, xóa các package|NPX được sử dụng cho các mục đích như kiểm tra version của package, thực thi các file script hoặc các lệnh command line|

## NPM vs YARN
Yarn là một package manager cho việc quản lý các dependencies trong ứng dụng JavaScript. Yarn được phát triển bởi Facebook và được thiết kế để giải quyết một số vấn đề mà NPM gặp phải.

Một số tính năng của Yarn bao gồm:

- Tốc độ nhanh hơn so với NPM
- Có khả năng hoạt động offline
- Có khả năng xây dựng dependency tree nhanh hơn
- Có khả năng xử lý các conflict dependencies một cách hiệu quả hơn
- Cung cấp lockfile format cho việc đảm bảo tính nhất quán giữa các máy tính