# git

## init
- Tạo một `local repository` tại `working directory`
```
git init
```

## remote
- Ánh xạ kho lưu trữ local và online (local repository và remote repository)
```
git remote add origin <url git repository>
```

## clone
- Sao chép từ `remote repository` về `working directory`
```
git clone <url remote repository>
```

## status
- Trạng thái của các file
```
git status
```

## add
- Thêm một file
```
gid add <tên file>
```
- Thêm tất cả file
```
git add --all (hoặc .)
```

## reset
- Trở về trạng thái ban đầu trước khi chỉnh sửa của một file tại local
```git
git reset <tên file>
```
- Trở về trạng thái của các file tại lần commit chỉ định:
  - Đưa `branch hiện tại` trở về trạng thái của `commit-hash-code` chỉ định và các file ở trạng thái đã `add`
   ```
   git reset --soft <commit hash code>
   ```
  - Đưa `branch hiện tại` trở về trạng thái của `commit-hash-code` chỉ định và các file ở trạng thái chưa `add`
  ```
  git reset --mixed <commit hash code>
  ```
  - Xóa toàn bộ các commit trước đó, đưa `branch hiện tại` trở về trạng thái của `commit-hash-code` chỉ định và các file ở trạng thái chưa `add`
  ```
  git reset --hard <commit hash code>
  ```

## revert
- Tạo ra một commit mới đảo ngược lại những thay đổi trong commit được chỉ định
```
git revert <commit hash code>
```

## commit
- Tạo mới một commit
```
git commit -m "<commit content>"
```

## log
- Hiển thị các commit
```
git log
```

## show
- Hiển thị nội dung của một commit
```
git show <commit hash code>
```

## push
- Đẩy các commit lên `remote branch`
```
git push <tên remote> <tên branch>
```

## branch
- Branch mặc định là `master`
- Có 2 loại branch:
  - `local branch`: branch nằm trên máy tính của chúng ta
  - `remote branch`: branch nằm trên máy chủ từ xa
- Liệt kê danh sách branch
```
git branch
```
- Tạo mới branch:
```
git branch <tên branch>
```
- Xóa branch:
```
git branch -D <tên branch>
```

## checkout
- Chuyển `remote branch` khác
```
git checkout <tên branch cần chuyển qua>
```
- Nếu bạn chưa có branch cần chuyển, bạn cũng có thể vừa tạo vừa chuyển qua chỉ với 1 lệnh
```
git checkout -b <tên branch cần chuyển qua>
```

## merge
- Gộp 2 branch lại với nhau
```
git merge <tên branch>
```
- Các bước hợp nhất một branch đến branch đích:
  - Step 1: `git checkout <tên branch đích>`
  - Step 2: `git merge <tên branch cần hợp nhất đến branch đích>`
  
## rebase
- Gộp một vài commit thành một commit duy nhất
```
git rebase -i <commit hash code>
```
`Note:` với `commit hash code` là hash code của commit cuối cùng của nhóm cần gộp

## fetch
- Tiến hành kéo các thay đổi từ trên `remote server` về `local` của chúng ta nhưng không tự động `merge`
``` 
git fetch <tên remote> <tên remote branch>
```

## pull
- Tiến hành kéo các thay đổi từ trên `remote server` về `local` của chúng ta và đồng thời tiến hành `merge` các thay đổi đó ngay
``` 
git pull <tên remote> <tên remote branch>
```
- `git pull` = `git fetch` + `git merge`
