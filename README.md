# LAB 5 – Component Vue 3

## Cách chạy

```bash
npm install
npm run dev
```

Mở địa chỉ Local mà Vite hiển thị (thường là `http://localhost:5173/`).

## Nội dung

- **Bài 1:** `Bai1.vue` là BookCard, nhận props `id`, `title`, `author`, `price`, `category` và hiển thị bằng Bootstrap.
- **Bài 2:** `Bai2.vue` là form thêm sách. Nút “Thêm sách” emit sự kiện `add-book`. `App.vue` lắng nghe và render danh sách bằng `Bai1.vue`.
- **Bài 3:** `Bai3.vue` là card dùng slot để nhận nội dung tùy chỉnh.
- **Bài 4:** `Bai4.vue` provide chủ đề `dark-theme` / `light-theme`, đưa theme ra scoped slot, và component con inject chủ đề đó.

Chọn từng bài bằng các nút phía trên trang.
