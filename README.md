# Git Merge Conflict - Session 04 Exercise 2

## 1. Mục tiêu

Thực hành quản lý branch, tạo Merge Conflict và xử lý xung đột thủ công khi gộp nhánh.

## 2. Các bước thực hiện

### Bước 1: Tạo branch

Tạo nhánh `feature-update` từ `main`:

```bash
git checkout -b feature-update
```

Sau đó cập nhật `README.md` trên nhánh `feature-update` và commit:

```bash
git add README.md
git commit -m "Update README on feature branch"
```

### Bước 2: Cập nhật main

Chuyển về nhánh `main`:

```bash
git checkout main
```

Sửa cùng dòng trong `README.md` và commit:

```bash
git add README.md
git commit -m "Update README on main branch"
```

### Bước 3: Tạo Merge Conflict

Thực hiện merge:

```bash
git merge feature-update
```

Git phát hiện xung đột:

```text
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

### Bước 4: Xử lý Conflict thủ công

Mở `README.md` và xử lý các ký hiệu:

```text
<<<<<<< HEAD
=======
>>>>>>> feature-update
```

Sau khi xử lý, giữ lại nội dung mong muốn:

```text
# Git Merge Conflict - Main Update + Feature Update
```

Đánh dấu conflict đã được giải quyết:

```bash
git add README.md
```

Tạo merge commit:

```bash
git commit -m "Merge feature-update and resolve conflict"
```

## 3. Kiểm tra lịch sử commit

Sử dụng:

```bash
git log --graph --oneline --all
```

Kết quả:

```text
*   ab47d0a Merge feature-update and resolve conflict
|\
| * ee93ec2 Update README on feature branch
* | 7b4bd5f Update README on main branch
|/
* a8715c1 first commit
```

Lịch sử cho thấy `feature-update` và `main` phát triển riêng, sau đó được gộp lại bằng một Merge Commit.

## 4. Kết quả

Đã tạo và xử lý thành công Merge Conflict thủ công, đồng thời tạo Merge Commit có hai nhánh tổ tiên.
