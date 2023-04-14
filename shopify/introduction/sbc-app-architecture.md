# BSS Shopify App architecture

Hiện tại đang BSS đang triển khai các Shopify App với dạng kiến trúc từ đơn giản tới phức tạp.

Shopify Apps có thể phân ra 2 loại là Standalone và Embedded App. Các Shopify apps hiện có của BSS đều là Standalone App.

Các app đơn giản được chia làm các component:
- APIs: dùng để tương tác với CMS, shopify API, Shopify Webhooks, đôi lúc là cả phần frontend code.
- Database: sử dụng mysql.
- CMS: là một React App, cung cấp giao diện để thao tác với các tính năng.
- Frontend Code: Bao gồm Javascript và liquid code

Các app phức tạp hơn, ngoài các component căn bản, còn tích hợp với các cloud service khác nhau.
.....

[Ảnh 1]

[Ảnh 2]

Giải thích thêm ở đây