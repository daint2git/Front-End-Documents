# git

## init
- Tạo một `local repository` tại `working directory`
```
git init
```

## remote
- Liệt kê các remote urls
```
git remote -v
```
- Thêm  remote repository
```
git remote add <tên remote repository> https://github.com/{user}/{repository}.git
// tên remote repository thường là origin
```

## clone
- Sao chép một remote repository đến thư mục mới có tên giống repository (thư mục được tự động tạo mới)
```
git clone https://github.com/{user}/{repository}.git
```
- Sao chép một remote repository đến thư mục hiện tại
```
git clone https://github.com/{user}/{repository}.git .
```

## status
- Kiểm tra trạng thái của các file tại `working directory`
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
  
Note: 
- Trở về trạng thái của các file trước khi commit (chưa add)
```
git reset HEAD~1
```
- Trở về trạng thái của các file trước khi commit (đã add)
```
git reset --soft HEAD^
```

## revert
- Tạo ra một commit mới đảo ngược lại những thay đổi trong commit được chỉ định
```
git revert <commit hash code>
```

## commit
- Thêm mới một commit
```
git commit -m "<commit message>"
```
- Đổi tên `commit message` của commit cuối
```
git commit --amend -m "<new commit message>"
```

## log
- Xem lịch sử commit
```
git log
```
- Xem lịch sử commit (với mỗi commit trên 1 dòng)
```
git log --oneline
```
- Xem lịch sử commit (cho 2 lần commits gần nhất)
```
git log -2
```

## show
- Xem nội dung của một commit được chỉ định
```
git show <commit hash code>
```

## push
- Đẩy các commit lên `remote branch`
```
git push <tên remote repository> <tên remote branch>
// tên remote repository thường là origin
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
- Tạo mới branch
```
git branch <tên branch>
```
- Xóa branch
```
git branch -D <tên branch>
```

## checkout
- Chuyển `branch` khác
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
- Tiến hành kéo các thay đổi từ trên `remote server` về `local`
- Không tự động `merge`
``` 
git fetch <tên remote repository> <tên remote branch>
// tên remote repository thường là origin
```

## pull
- Tiến hành kéo các thay đổi từ trên `remote server` về `local`
- Tự động `merge` các thay đổi đó ngay
``` 
git pull <tên remote repository> <tên remote branch>
// tên remote repository thường là origin
```
- `git pull` = `git fetch` + `git merge`

## diff
- Xem thay đổi của một file được chỉ định
```
git diff <tên file>
```
- Xem thay đổi của những file hiện tại (chưa được add)
```
git diff
```
- Xem thay đổi của những file hiện tại (đã được add nhưng chưa commit)
```
git diff --cached
```
- Xem thay đổi giữa 2 commits
```
git diff <commit hash code 1> <commit hash code 2>
```

## clean
- Remove untracked files (e.g., new files, generated files)
```
git clean -f
```
- Remove untracked directories (e.g., new or automatically generated directories)
```
git clean -fd
```
## How do I discard unstaged changes in Git?
```
git clean -df
git checkout -- .
```
