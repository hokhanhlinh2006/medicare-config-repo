# Báo cáo: Bài 4 - Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## Tình huống
Đã vô tình commit nhầm file chứa thông tin bảo mật `credentials.txt` lên Git. Nhiệm vụ là gỡ bỏ file này khỏi Git cache, bỏ qua nó bằng `.gitignore`, và sửa lại thông điệp commit cuối cùng.

## Cách giải quyết

### Bước 1: Gỡ file ra khỏi cache theo dõi của Git
Lệnh sau được sử dụng để loại bỏ `credentials.txt` ra khỏi cache của Git mà không xóa file vật lý trên ổ cứng:
```bash
git rm --cached credentials.txt
```

### Bước 2: Bỏ qua file nhạy cảm bằng `.gitignore`
Tạo file `.gitignore` và thêm `credentials.txt` vào để Git ngừng theo dõi file này trong tương lai:
```bash
echo "credentials.txt" > .gitignore
git add .gitignore
```

### Bước 3: Sửa lịch sử commit (Amend)
Sử dụng tuỳ chọn `--amend` để gộp những thay đổi vừa rồi vào commit hiện tại và đổi nội dung thông điệp cho chuẩn xác:
```bash
git commit --amend -m "Cấu hình .gitignore bỏ qua file nhạy cảm credentials.txt"
```

## Kết quả kiểm tra

Dưới đây là kết quả của lệnh `git log -n 1` xác nhận commit gần nhất đã được thay đổi thành công:

```text
commit 00ec82767a516fcdf2ad3cdeff8ec89350d8fc16 (HEAD -> master)
Author: Ho Khanh Linh <hokhanhlinh2006@gmail.com>
Date:   Mon Oct 5 10:45:11 2026 +0700

    Cấu hình .gitignore bỏ qua file nhạy cảm credentials.txt
```

Bên cạnh đó, lệnh `git status` lúc này sẽ báo "working tree clean" (hoặc chỉ hiển thị các file không liên quan) do `credentials.txt` đã được Git hoàn toàn bỏ qua.
