## Làm việc với Linux

### Những lệnh Ubuntu cơ bản:

#### 1. ls

- `ls`: Liệt kê toàn bộ file/folder trong folder hiện tại.
- `ls -l`: Liệt kê chi tiết hơn ls.
- `ls -a`: Liệt kê cả file ẩn.
- `ls -R`: Liệt kê cả những file/folder con.

#### 2. cd

- `cd`: Di chuyển giữa các folder.
- `cd + tab tab`: Liệt kê tất cả đường dẫn thư mục con.
- `cd ..`: Quay trở lại một cấp.
- `cd folder/subfolder`: Đi vào thư mục con.
- `cd -`: Back lại folder trước đó.
- `cd /`: Trở về thư mục gốc
- `~$`: Account hiện tại đang login.

#### 3. clear

- `clear`: Làm sạch terminal.

#### 4. dir

- `mkdir [folder-name]`: Tạo folder con nằm trong folder hiện tại.
- `mkdir [folder-name]/[sub-folder]/...`: Tạo folder nhiều tầng.
- `touch [file-name]`: Tạo ra một file bên trong folder hiện tại.

#### 5. vi

- `vi`: Xem thông tin Vim editor.
- `vi [file-name]`: Tạo một file bằng Vim editor / chỉnh sửa file có sẵn.
- `:q`: Thoát Vim.
- `:q!`: Thoát và không lưu.
- `:x`: Vừa lưu vừa thoát.
- `:w`: Lưu file.
- Nhấn 'i' để insert nội dung file.
- Nhấn 'ESC' để thoát insert.

#### 6. cat (đầu ra stout)

- `cat [file-name]`: In ra terminal nội dung của một file.
- `cat [file-name] [file-name] ...`: In ra nội dung của nhiều file.
- `cat [file-name] [file-name] > [file-name]`: Ghi nội dung của nhiều
  file vào một file mới.
- `cat [file-name] [file-name]| grep [search-content]`: Tìm xem trong
  một hoặc nhiều file có nội dung đang tìm kiếm hay không.

#### 7. echo (đầu ra stout)

- `echo "content"`: In ra terminal content.
- `echo "content" > [file-name]`: Ghi content vào một file.
- `echo "content" >> [file-name]`: Ghi thêm nội dung vào một file.

#### 8. tail

- `tail [file-name]`: In ra terminal 10 dòng cuối cùng của file.
- `tail -n [lineNumber] [file-name]`: Chỉ định số dòng cần in ra.
- `tail -f [file-name]`: Follow theo nội dung file.

#### 9. cp

- `cp [file-name] [new-file]`: Copy một file sang một file mới.
- `cp [file-name] [path]/[new-file]`: Copy một file sang một file
  mới trong folder khác. Nếu không điền tên file mới thì sẽ sử dụng
  lại tên file cũ.
- `cp -r [folder-name] [path]/[new-folder]`: Copy folder.
- `sudo cp [file-name] /home/`: Copy vào thư mục hạn chế quyền.

#### 10. mv

- `mv [old-name] [new-name]`: Đổi tên file/folder.
- `mv [file/folder] [folder-name]/`: Di chuyển file/folder sang
  folder khác.
- `mv [file/folder] [folder-name]`: Di chuyển file/folder sang folder
  khác với tên mới.

#### 11. rm

- `rmdir [folder/file-name]`: Xóa folder/file.
- `rm -r [folder-name]`: Xóa cả folder con của folder muốn xóa.

#### 12. chmod (phân quyền)

| Ký hiệu | Kiểu file              |
| ------- | ---------------------- |
| -       | File thông thường      |
| d       | Directory              |
| l       | Liên kết mềm           |
| b       | Chặn file đặc biệt     |
| d       | File đặc biệt về ký tự |

- `sudo chmod u=rwx,g=rx,o=r [file]`: Phân quyền cho owner
  (user class - lớp người dùng), group (group class - lớp nhóm), others.
- Ex:
  ```
  -rw-r--r--
  => Owner (chủ sỡ hữu): có quyền read, write (rw-)
  => Group (nhóm): có quyền read (r--)
  => Others (khác): có quyền read (r--)
  ```
- Các quyền trong Unix:
  - read: đọc - khả năng mở và xem nội dung file (4)
  - write: ghi - khả năng mở và sửa đổi nội dung file (2)
  - execute: thực thi - khả năng chạy như một chương trình thực thi (1).
- Nếu không có quyền nào biểu tượng dấu (-) sẽ được sử dụng (0).
- Phân quyền sử dụng ký hiệu số:
  - 0: Không có quyền nào được cho phép.
  - +1: Nếu lớp có thể thực thi file.
  - +2: Nếu lớp có thể ghi vào file.
  - +4: Nếu lớp có thể đọc file.
- Ex:
  ```
  sudo chmod 754 [file]
  => Owner: tất cả các quyền read, write, execute
  => Group: có quyền read, execute
  => Others: chỉ có quyền đọc
  ```

#### 13. chown (gán quyền sở hữu một file cho user khác)

- `-rw-r--r-- 1 root root 0 Feb 20 17:35 chownSample.txt`
  - `-rw-r--r--`: file permission (quyền sở hữu của file)
  - `root`: file sở hữu bởi user root.
  - `root`: user này thuộc về nhóm có tên root.
- `chown user filename(s)`: Thay đổi owner của file (chủ sỡ hữu của file)
- `chown :group filename(s)`: Thay đổi group owner.
- `sudo chown root:root [file-name]`: Thay đổi owner và group.

#### 14. man (tra cứu command ubuntu)

- `man [commandName]`: chi tiết về một lệnh.
- `wget [linkImage]`: Tải ảnh.

#### 15. apt (quản lý thư viện trong ubuntu)

- `sudo apt install [package-name]`: Cài đặt một gói hoặc thư viện.
- `sudo apt remove [package-name]`: Gỡ cài đặt.
- `sudo apt autoremove`: Gỡ bỏ những package phụ liên quan.

#### 16. kill (tắt một tiến trình khi bị treo)

- `ps aux`: Những tiến trình đang chạy.
- `kill PID`: Tắt một tiến trình đang chạy (PID - process id). Mặc
  định tín hiệu sẽ là 15.
- `kill -15/9 PID`: Tắt một tiến trình theo tín hiệu (signals)
  - SIGTERM (15): Yêu cầu một chương trình ngừng chạy và cho nó
    thời gian để lưu tất cả tiến trình.
  - SIGKILL (9): Bắt buộc các chương trình dừng ngay lập tức. Tiến
    trình chưa được lưu sẽ bị mất.

#### 17. ping

- Sử dụng ping để kiểm tra trạng thái kết nối của mình với server.
- Ex: `ping google.com` kiểm tra xem có thể kết nối với Google hay
  không và đo thời gian phản hồi.

#### 18. uname

- In thông tin chi tiết về hệ thống Linux như tên máy, hệ điều hành,
  nhân, ...
- Syntax: `uname -a`.

#### 19. passwd

- `passwd`: Đổi mật khẩu của user hiện tại.

#### 15. top

- `top`: Hiển thị danh sách các tiến trình đang chạy và mỗi tiến
  trình sử dụng bao nhiêu CPU.
- `htop`: Hiển thị chi tiết hơn.

#### 16. df

- `df -m` or `df -h`: Nhận báo cáo về việc sử dụng dung lượng ổ đĩa của hệ thống.

#### 17. free

- `free -h`: Hiển thị thông tin về ram.

#### 18. nvm

- `nvm list-remote`: Hiển thị những phiên bản node có sẵn.
- `nvm install [version]`: Cài đặt một version theo ý muốn.
- `nvm list`: Hiển thị các phiên bản mà chúng ta đã cài đặt.

### Những mẹo gõ lệnh:

- Nhấn `tab` để tự động hoàn thành.
- `cd tab tab` list ra các đường dẫn trong folder.
- Nhấn `crl + a/ crl + e`: di chuyển về đầu/cuối command.
- Chạy nhiều dòng lệnh cùng lúc: `cmd1;cmd2;cdm3...`, `cmd1 && cmd2`.
