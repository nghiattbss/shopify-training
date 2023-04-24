# Git
Là một công cụ để quản lý source code, giúp nhiều Developers có thể làm việc cộng tác với nhau.

Có thể sử dụng dịch vụ của Github hoặc Bitbucket.

# Lệnh cơ bản
- **git init:** Khởi tạo một repository mới.

- **git clone**: Tải về một repository đã tồn tại từ một remote repository (như GitHub).

- **git add:** Thêm file vào staging area để chuẩn bị cho commit.

- **git commit:** Lưu lại thay đổi của staging area vào repository.

- **git status:** Kiểm tra trạng thái của repository hiện tại.

- **git push:** Đẩy những thay đổi từ repository local lên remote repository.

- **git pull:** Tải về những thay đổi mới nhất từ remote repository và cập nhật repository local.

- **git branch:** Liệt kê các nhánh hiện có trong repository.

- **git checkout:** Chuyển đổi giữa các nhánh hoặc commit khác nhau trong repository.

- **git merge:** Kết hợp các nhánh khác nhau trong repository lại với nhau.

- **git reset:** Loại bỏ các thay đổi chưa được commit trong staging area hoặc repository.

- **git log:** Xem lịch sử commit của repository.

# Xử lý Conflict khi merge

Để xử lý conflict khi merge code, bạn có thể thực hiện các bước sau:

- Đầu tiên, hãy kiểm tra nhánh mà bạn đang cố gắng merge vào nhánh hiện tại. Bạn có thể sử dụng lệnh `git status` để kiểm tra.

- Sử dụng lệnh git merge để merge nhánh khác vào nhánh hiện tại. Khi đó, Git sẽ tạo ra một file thông báo conflict. Bạn có thể sử dụng lệnh `git status` để xem danh sách các file bị conflict.

- Mở file conflict và tìm các dòng bị conflict. Git sẽ đánh dấu các sửa đổi của bạn và của nhánh khác bằng các dấu nháy đơn `<<<<<<<, =======,` và `>>>>>>>.`

- Xác định sửa đổi nào là đúng và sửa các dòng bị conflict trong file. Sau khi bạn đã sửa các conflict, lưu file.

- Sử dụng lệnh `git add` để đánh dấu các file đã được sửa đổi, và sau đó sử dụng lệnh `git commit` để hoàn thành quá trình merge.

- Nếu cần, bạn có thể sử dụng lệnh `git log` để xem lịch sử merge của nhánh hiện tại.

Lưu ý rằng khi xử lý conflict, bạn nên chọn sửa đổi nào là đúng và không nên xoá bất kỳ sửa đổi nào của nhánh khác mà không hiểu rõ tác động của nó đến ứng dụng của bạn.

# Naming convention

- Khi đặt tên nhánh (branch), nên đặt theo quy tắc: loại_task/mã_số_task. Ví dụ: feature/dashboard-1234, bugfix/dashboard-1235
- Khi commit: message phải mô tả ngắn gọn ý nghĩa đoạn code đã commit.

Chi tiết sẽ được training trong quá trình on-job training.