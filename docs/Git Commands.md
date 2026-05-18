# 📋 Git Cheatsheet

> Tổng hợp các lệnh Git thường dùng

---

## 🔧 Cấu hình ban đầu

```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email@example.com"
git config --global core.editor "code --wait"   # Dùng VS Code làm editor
git config --list                                # Xem toàn bộ cấu hình
```

---

## 📁 Khởi tạo Repository

```bash
git init                        # Tạo repo mới ở thư mục hiện tại
git clone <url>                 # Clone repo từ remote
git clone <url> <tên-thư-mục>  # Clone và đặt tên thư mục
```

---

## 📊 Trạng thái & Lịch sử

```bash
git status                      # Xem trạng thái working tree
git log                         # Xem lịch sử commit
git log --oneline               # Lịch sử rút gọn 1 dòng/commit
git log --oneline --graph       # Lịch sử dạng cây nhánh
git log --author="Tên"          # Lọc commit theo tác giả
git diff                        # Xem thay đổi chưa stage
git diff --staged               # Xem thay đổi đã stage
git show <commit-hash>          # Xem chi tiết 1 commit
```

---

## ➕ Staging & Commit

```bash
git add <file>                  # Stage 1 file
git add .                       # Stage tất cả thay đổi
git add -p                      # Stage từng phần (interactive)
git restore --staged <file>     # Bỏ stage 1 file
git commit -m "message"         # Commit với message
git commit -am "message"        # Stage + Commit cùng lúc
git commit --amend -m "message" # Sửa commit gần nhất
```

---

## 🌿 Branch

```bash
git branch                      # Liệt kê branch local
git branch -a                   # Liệt kê tất cả branch (local + remote)
git branch <tên>                # Tạo branch mới
git branch -d <tên>             # Xóa branch (an toàn)
git branch -D <tên>             # Xóa branch (bắt buộc)
git branch -m <tên-cũ> <tên-mới> # Đổi tên branch
git switch <tên>                # Chuyển sang branch
git switch -c <tên>             # Tạo và chuyển sang branch mới
git checkout <tên>              # (Cũ) Chuyển sang branch
git checkout -b <tên>           # (Cũ) Tạo và chuyển sang branch mới
```

---

## 🔀 Merge & Rebase

```bash
git merge <branch>              # Merge branch vào branch hiện tại
git merge --no-ff <branch>      # Merge với merge commit (không fast-forward)
git merge --squash <branch>     # Gộp tất cả commit thành 1 trước khi merge
git merge --abort               # Hủy merge đang bị conflict
git rebase <branch>             # Rebase lên branch
git rebase -i HEAD~<n>          # Interactive rebase n commit gần nhất
git rebase --abort              # Hủy rebase
git rebase --continue           # Tiếp tục sau khi xử lý conflict
```

---

## 🌐 Remote

```bash
git remote -v                           # Xem danh sách remote
git remote add origin <url>             # Thêm remote
git remote remove <tên>                 # Xóa remote
git remote rename <tên-cũ> <tên-mới>   # Đổi tên remote
git fetch                               # Tải về nhưng không merge
git fetch --prune                       # Xóa remote branch đã bị xóa
git pull                                # Fetch + merge
git pull --rebase                       # Fetch + rebase
git push origin <branch>                # Push branch lên remote
git push -u origin <branch>             # Push và set upstream
git push --force-with-lease             # Force push an toàn
git push origin --delete <branch>       # Xóa branch trên remote
```

---

## 💾 Stash

```bash
git stash                       # Lưu tạm thay đổi chưa commit
git stash save "mô tả"          # Lưu tạm với mô tả
git stash list                  # Xem danh sách stash
git stash pop                   # Lấy lại stash mới nhất và xóa
git stash apply stash@{n}       # Áp dụng stash thứ n (không xóa)
git stash drop stash@{n}        # Xóa stash thứ n
git stash clear                 # Xóa toàn bộ stash
```

---

## ⏪ Hoàn tác

```bash
git restore <file>              # Huỷ thay đổi chưa stage
git restore --staged <file>     # Bỏ stage file
git revert <commit-hash>        # Tạo commit mới để hoàn tác
git reset --soft HEAD~1         # Hoàn tác commit, giữ thay đổi (staged)
git reset --mixed HEAD~1        # Hoàn tác commit, giữ thay đổi (unstaged)
git reset --hard HEAD~1         # Hoàn tác commit, xóa thay đổi ⚠️
git clean -fd                   # Xóa file/thư mục untracked ⚠️
```

---

## 🏷️ Tag

```bash
git tag                         # Liệt kê tất cả tag
git tag <tên>                   # Tạo lightweight tag
git tag -a <tên> -m "message"   # Tạo annotated tag
git tag -a <tên> <commit-hash>  # Tag một commit cũ
git push origin <tên-tag>       # Push tag lên remote
git push origin --tags          # Push tất cả tag
git tag -d <tên>                # Xóa tag local
git push origin --delete <tên>  # Xóa tag trên remote
```

---

## 🔍 Tìm kiếm & Debug

```bash
git grep "từ khóa"              # Tìm kiếm trong code
git log -S "từ khóa"            # Tìm commit có thêm/xóa từ khóa
git blame <file>                # Xem ai sửa từng dòng
git bisect start                # Bắt đầu tìm commit gây lỗi
git bisect good <commit>        # Đánh dấu commit tốt
git bisect bad <commit>         # Đánh dấu commit lỗi
git bisect reset                # Kết thúc bisect
```

---

## 📄 .gitignore

```bash
# Bỏ qua file/thư mục
*.log
node_modules/
.env
build/
dist/

git rm --cached <file>          # Bỏ track file đã commit (giữ file local)
git check-ignore -v <file>      # Kiểm tra file bị ignore bởi rule nào
```

---

## ⚡ Alias hữu ích

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --all"
git config --global alias.undo "reset --soft HEAD~1"
```

---

## 🔄 Workflow thường gặp

### Feature branch
```bash
git switch -c feature/ten-tinh-nang   # Tạo branch mới
# ... code ...
git add . && git commit -m "feat: mô tả"
git push -u origin feature/ten-tinh-nang
# Tạo Pull Request trên GitHub/GitLab
```

### Xử lý conflict
```bash
git pull origin main            # Kéo code mới nhất
# Sửa conflict trong file
git add <file-conflict>
git commit -m "fix: resolve conflict"
```

### Hotfix nhanh
```bash
git stash                       # Lưu tạm công việc hiện tại
git switch main
git switch -c hotfix/ten-loi
# ... sửa lỗi ...
git commit -m "fix: mô tả lỗi"
git switch main && git merge hotfix/ten-loi
git stash pop                   # Lấy lại công việc cũ
```

### Clean/Xóa toàn bộ remote, thay bằng local
```bash
rm -rf .git                                 # Xóa git history, thực hiện ở máy local
git init                                    # Init lại
git add .                                   # Add lại
git commit -m "Initial commit"              # Commit mới
git branch -M main                          # Tạo lại branch
git remote add origin https://github.com/nkht10/dockers.git
git push -u --force origin main
```




---

> ⚠️ Các lệnh có dấu **⚠️** có thể gây **mất dữ liệu vĩnh viễn**, hãy cẩn thận khi dùng!
