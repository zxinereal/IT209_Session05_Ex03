# Bài 3 – Xử lý xung đột phức tạp trong Rebase

## Báo cáo xử lý rebase từng chặng

1. Khởi tạo `config.json` trên `main`, sau đó tạo nhánh `feature-api`.
2. Trên `feature-api`, tạo lần lượt hai commit: `feat: change port` (port `9000`) và `feat: enable debug` (debug `true`).
3. Trên `main`, tạo hai commit: `update port on main` (port `8081`) và `add env config` (thêm `env: production`).
4. Chạy `git rebase main` khi đang ở `feature-api`.
5. Conflict thứ nhất xuất hiện khi áp dụng `feat: change port`. Sau khi đọc các nhãn conflict, chọn port `9000` của tính năng, đồng thời giữ `debug: false` và `env: production` của `main`; chạy `git add config.json` rồi tiếp tục rebase.
6. Conflict thứ hai xuất hiện khi áp dụng `feat: enable debug`. Giữ port `9000`, đổi debug thành `true`, và giữ `env: production`; sau đó `git add config.json` và tiếp tục rebase.
7. Rebase hoàn tất, không tạo merge commit. Lịch sử của `feature-api` thẳng hàng ngay sau hai commit mới nhất của `main`.

## Kết quả cấu hình

```json
{
  "port": 9000,
  "debug": true,
  "env": "production"
}
```

Lệnh kiểm tra: `git status` và `git log --graph --oneline --all`.
