# git

Git là một trong những Hệ thống Quản lý Phiên bản Phân tán, được phát triển bởi Linus Torvalds vào năm 2005, vốn được phát triển nhằm quản lý mã nguồn (source code) của Linux. Trên Git, ta có thể lưu trạng thái của file dưới dạng lịch sử cập nhật. Vì thế, có thể đưa file đã chỉnh sửa một lần về trạng thái cũ hay có thể biết được file đã được chỉnh sửa chỗ nào.

## repository and branch

- Repository: Repository (nhà kho) hay được gọi tắt là `Repo` đơn giản là nơi chứa/cơ sở dữ liệu (database) tất cả những thông tin cần thiết để duy trì và quản lý các sửa đổi và lịch sử của dự án.
- Repository có các loại
  - Remote repository: Là repository để chia sẻ giữa nhiều người và bố trí trên server chuyên dụng.
  - Local repository: Là repository bố trí trên máy local của bạn, dành cho một người dùng sử dụng.
- Branch: Là phân nhánh ghi lại luồng thay đổi của lịch sử, các hoạt động trên mỗi branch sẽ không ảnh hưởng lên các branch khác nên có thể tiến hành nhiều thay đổi đồng thời trên một repository, giúp giải quyết được nhiều nhiệm vụ cùng lúc.
- Branch có các loại
  - Local branch: Là nhánh ở local, tồn tại trên máy local của bạn và tất nhiên chỉ bạn mới có thể nhìn thấy.
  - Local tracking branch: Là một nhánh local để theo dõi các nhánh khác. Điều này để cam kết rằng bạn có thể push lên/pull về các commit các nhánh khác.
  - Remote branch: là branch lưu ở remote. Branch này có thể fetch về local nhưng không tạo thêm branch ở local.
  - Remote tracking branch: là một bản sao cục bộ (local) của một nhánh remote.

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

- Thêm remote repository

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

```
// Kiểm tra trạng thái của các file tại `working directory`
git status
```

## add

```
// Thêm một file
git add <tên file>

// Thêm tất cả file
git add --all
or
git add .
```

## reset

```git
// Trở về trạng thái ban đầu trước khi chỉnh sửa của một file tại local
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

- Loại bỏ tập tin đã đưa vào stage

```
git reset HEAD <file_name>
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

```
// Tạo commit đảo ngược commit có commit đã chọn, commit chỉ định bị xoá bỏ, các commit mới hơn vẫn được giữ nguyên
git revert <commit hash code>
```

## commit

```
// Thêm mới một commit
git commit -m "<commit message>"

// Đổi tên `commit message` của commit cuối
git commit --amend -m "<new commit message>"
```

## log

```
// Xem lịch sử commit
git log

// Xem lịch sử commit (với mỗi commit trên 1 dòng)
git log --oneline

// Xem lịch sử commit (cho 2 lần commits gần nhất)
git log -2
```

## show

```
// Xem nội dung của một commit được chỉ định
git show <commit hash code>
```

## push

```
// Đẩy các commit lên `remote branch`
git push <tên remote repository> <tên remote branch>

// tên remote repository thường là origin
```

## branch

- Branch mặc định là `master`
- Liệt kê danh sách branch

```
git branch
```

- Tạo mới branch

```
git branch <tên branch>
```

- Xóa một local branch

```
// branch đang ở trạng thái fully merged
git branch -d <tên branch>
or
// branch ở trạng thái not fully merged
git branch -D <tên branch>
or
git branch --delete <tên branch>
```

- Xóa một remote branch

```
git push --delete <tên remote> <tên branch>
or
git push <tên remote> --delete <tên branch>
```

> **Note**
>
> - Khi bạn tạo một branch và thực hiện một số commit trên đó và chưa thực hiện thao tác merge vào branch master thì nó sẽ đang ở trạng thái `not fully merged`, còn bạn đã merge rồi thì sẽ ở trạng thái `fully merged`.

## checkout

```
// Chuyển `branch` khác
git checkout <tên branch cần chuyển qua>

// Nếu bạn chưa có branch cần chuyển, bạn cũng có thể vừa tạo vừa chuyển qua chỉ với 1 lệnh
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
(với <commit hash code> là hash code của commit cuối cùng của nhóm cần gộp)
or
git rebase -i HEAD~<index>
```

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
git clean -fx
```

- Remove untracked directories (e.g., new or automatically generated directories)

```
git clean -fd
```

## stash

- được sử dụng khi muốn lưu lại các thay đổi nhưng chưa commit, thường rất hữu dụng khi bạn muốn đổi sang 1 branch khác mà lại đang làm dở ở branch hiện tại.

```
// Xem danh sách stash
git stash list [<options>]
// Apply stash gần nhất và xóa stash đó
git stash pop
// Apply stash
git stash apply stash@{<index>}
// Xem nội dung stash
git stash show stash@{<index>}
// Xóa stash
git stash drop stash@{<index>}
// Xóa toàn bộ stash
git stash clear
// Lưu toàn bộ nội dung công việc đang làm dở, sử dụng lệnh
git stash save
or
git stash
```

## How do I discard unstaged changes in Git?

```
git clean -df
git checkout -- .
```

## Revert đến commit trước (sau khi đã push lên git)

```
# Reset the index to the desired commit
git reset --hard <commit>

# Move the branch pointer back to the previous HEAD
git reset --soft HEAD@{1}

# Commit the changes
git commit -m "Revert to <commit>"
```

```
git reset --hard <commit id can den>

git push --force
```

## Please enter a commit message to explain why this merge is necessary, especially if it merges an updated upstream into a topic branch

```
1. press "i"
2. write your merge message
3. press "esc"
4. write ":wq"
5. then press enter
```

## Git pull after git rebase
```
git checkout feature/branch
git fetch origin feature/branch
git reset --hard origin/feature/branch

// then if you want to bring in changes in the master branch,
git rebase origin/master
```

## Khi git push tại một nơi nào đó
```
git remote set-url origin https://yourname@github.com/yourname/yourrepo.git
// or
git remote set-url origin https://yourname:password@github.com/yourname/yourrepo.git
```

## 3 trạng thái của Git

- `Committed` có nghĩa là dữ liệu đã được lưu trữ một cách an toàn trong cơ sở dữ liệu, tức là những gì bạn đã commit thành công
- `Staged` là bạn đã đánh dấu sẽ commit phiên bản hiện tại của một tập tin đã chỉnh sửa trong lần commit sắp tới. Trạng thái này xảy ra khi bạn sử dụng lệnh `git add <file_name>` nhưng chưa commit
- `Modified` có nghĩa là bạn đã thay đổi tập tin nhưng chưa commit vào cơ sở dữ liệu, tức là bạn chưa sử dụng lênh `git add` và `git commit`

### Ví dụ

- Commited - modify + add + commit

```
git checkout test-branch
git add demo.txt
git commit -m "Sua file demo.txt"
```

- Staged - modify + add

```
git checkout test-branch
git add demo.txt
```

- Modified - modify + ko làm gì

```
git checkout test-branch
```
