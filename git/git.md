# git

## init
- Tạo kho lưu trữ local: `git init`

## remote
- Ánh xạ kho lưu trữ local và online (local repository và remote repository): `git remote add origin <url git repository>`

## clone
- Sao chép từ `remote repository` về `working directory`: `git clone <url remote repository>`

## status
- Trạng thái của các file: `git status`

## add
- Thêm một file: `gid add <tên file>`
- Thêm tất cả file: `git add --all (hoặc .)`

## reset
- Trở về trạng thái ban đầu trước khi chỉnh sửa của một file tại local: `git reset <tên file>`
- Trở về trạng thái của các file tại lần commit chỉ định:
  - Các file ở trạng thái đã add: `git reset --soft <ID commit>`
  - Các file ở trạng thái chưa add: `git reset --mixed <ID commit>`
  - Các file ở trạng thái chưa add và Xóa commit đó: `git reset --hard <ID commit>`

## revert
- Trở về các file tại lần commit chỉ định: `git revert <ID commit>`

## commit
- Tạo mới một commit: `git commit -m "<nội dung commit>"`

## log
- Hiển thị các commit: `git log`

## show
- Hiển thị nội dung của một commit `git show <ID commit>`

## push
- Đẩy các commit lên branch`git push origin <tên branch>`

## branch
- Liệt kê danh sách branch: `git branch`
- Tạo mới branch: `git branch <tên branch>`
- Xóa branch: `git branch -D <tên branch>`

## checkout
- Chuyển branch khác: `git checkout <tên branch cần chuyển qua>`
- Nếu bạn chưa có branch cần chuyển, bạn cũng có thể vừa tạo vừa chuyển qua chỉ với 1 lệnh: `git checkout -b <tên branch cần chuyển qua>`

## merge
- Hợp nhất branch đến branch đích:
  - Step 1: `git checkout <tên branch đích>`
  - Step 2: `git merge <tên branch cần hợp nhất đến branch đích>`

## pull
- Kéo tất cả các file được thêm mới và chỉnh sửa với trạng thái mới nhất từ `remote repository` về `working directory`: `git pull origin <tên branch>`