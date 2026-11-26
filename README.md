# NGOC HIEN · Kỷ Niệm 1000 Ngày Bên Nhau 🌸

> **Live Demo:** https://frontend-design-rose.vercel.app

Một trang trưng bày ảnh tĩnh mang phong cách **Balletcore / Pearlescent Rose**, được thiết kế dành riêng cho **Ngoc Hien** nhân dịp **Kỷ niệm 1000 ngày bên nhau**. Dự án xây dựng hoàn toàn bằng HTML tĩnh, CSS hiện đại (3D Transforms, Clip-Path, Parallax) và Vanilla JavaScript — không cần build tool, tối ưu mượt mà trên cả điện thoại và máy tính.

---

## Tính năng nổi bật

- **Hero Mosaic 4 cột so le (4:5 Portrait):** 20 khung ảnh tỉ lệ `4:5` xếp nhịp so le lấy cảm hứng từ bố cục editorial, tự động cân đối đẹp mắt trên màn hình điện thoại lẫn desktop.
- **Hiệu ứng mở vòng tròn không viền (`clip-path: circle`):** Khi cuộn trang hoặc kéo thanh điều khiển, 4 cột ảnh lướt parallax nhẹ và mở vòng tròn hiện tên **NGOC HIEN** ở trung tâm.
- **Thư viện Cánh Bướm (13 ảnh):** Bố cục đối xứng hai cánh trái/phải ôm lấy khung chân dung trung tâm `#01`, tích hợp hiệu ứng spotlight khi rê chuột.
- **Vòng xoay 3D tương tác (11 ảnh):** Vòng tròn 3D góc nhìn nghiêng từ trên xuống, hiển thị đầy đủ cả dải ảnh trước & sau, có phản chiếu mờ dưới chân ảnh, hỗ trợ **vuốt/kéo ngang trên điện thoại**, tạm dừng, đổi chiều và chỉnh tốc độ.
- **Lightbox phóng to toàn màn hình:** Chạm/bấm vào bất kỳ bức ảnh nào trong thư viện hoặc vòng xoay 3D để xem ảnh lớn kèm chú thích (hỗ trợ phím `Esc` hoặc chạm ngoài khung để đóng).
- **Hiệu ứng hoa anh đào rơi & ánh sao chuột:** Hoa anh đào rơi nhẹ nhàng bằng GPU `translate3d`, ánh sao lấp lánh theo con trỏ chuột trên máy tính.

---

## Tối ưu hiệu năng cho thiết bị di động

- Chuyển toàn bộ animation hoa anh đào rơi từ `top` sang `transform: translate3d(...)` (compositor-only, không gây reflow/repaint).
- Thay `filter: blur(120px)` nặng GPU bằng `radial-gradient` thuần và chỉ bật `backdrop-filter` trên thiết bị desktop (`pointer: fine`).
- Cuộn Hero dùng `requestAnimationFrame` + đọc `window.scrollY` không gọi `getBoundingClientRect()` trong scroll handler.
- Dùng `IntersectionObserver` để tự động tạm dừng vòng lặp `requestAnimationFrame` của Vòng xoay 3D khi không nằm trong vùng nhìn thấy.
- Tắt hiệu ứng particle theo chuột trên thiết bị cảm ứng (`pointer: coarse`) và dùng `content-visibility: auto` cho các phần bên dưới.

---

## Cấu trúc thư mục

```text
Frontend-design/
├── index.html          # Toàn bộ giao diện, CSS Balletcore & logic tương tác
├── hero-slot-8.jpg     # Ảnh chân dung dùng trong Hero Mosaic
├── .gitignore          # Loại trừ các ảnh gốc chưa dùng khi commit
└── README.md           # Tài liệu giới thiệu dự án
```

---

## Chạy cục bộ (Local)

Bạn có thể mở trực tiếp `index.html` trên trình duyệt, hoặc chạy máy chủ tĩnh bằng Python:

```bash
python -m http.server 5500 --bind 127.0.0.1
```

Sau đó truy cập `http://127.0.0.1:5500`.

---

## Công nghệ sử dụng

- **HTML5 & Vanilla JavaScript**
- **Tailwind CSS (CDN)** + Custom CSS 3D / Clip-Path / Animations
- **Google Fonts:** `Cormorant Garamond` & `Plus Jakarta Sans`
- **Hosting:** Vercel (`https://frontend-design-rose.vercel.app`)

---

*Made with love by **THANHPHAT** — Kỷ niệm 1000 ngày bên nhau.*
