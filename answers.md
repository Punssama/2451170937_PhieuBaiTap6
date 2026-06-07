# BÀI LÀM — PBT 06

## TRACK A — BOOTSTRAP 5

## PHẦN A — ĐỌC HIỂU

### Câu A1 — Grid System

| Kích thước | < 768px              | 768px - 991px | ≥ 992px      |
| ---------- | -------------------- | ------------- | ------------ |
| Số cột     | 1 cột                | 2 cột         | 4 cột        |
| Box layout | Mỗi box chiếm 1 hàng | 2 box / hàng  | 4 box / hàng |

**Giải thích:**

- Mặc định `col-12` nên trên mobile mỗi box chiếm 12/12 = 100%.
- Từ `md` trở lên, `col-md-6` làm mỗi box chiếm 6/12 = 50%
- Từ `lg` trở lên, `col-lg-3` làm mỗi box chiếm 3/12 = 25%

**Câu hỏi thêm:**

- `col-md-6` nghĩa là từ breakpoint `md` (≥ 768px) trở lên, cột chiếm 6/12 chiều rộng row.
- Không cần viết `col-sm-12` vì `col-12` đã là trạng thái mặc định cho mobile-first.

---

### Câu A2 — Utilities & Components

1. `d-none d-md-block`

- `d-none`: ẩn phần tử ở mọi kích thước.
- `d-md-block`: từ `md` trở lên thì hiển thị dạng block.
- Kết luận: ẩn trên mobile, hiện từ tablet/desktop trở lên.

2. 5 spacing utilities

- `mt-3` → margin-top mức 3.
- `mb-4` → margin-bottom mức 4.
- `ms-2` → margin-left theo hướng start mức 2.
- `px-4` → padding trái/phải mức 4.
- `py-3` → padding trên/dưới mức 3.

3. `.container`, `.container-fluid`, `.container-md`

- `.container` → có max-width theo breakpoint.
- `.container-fluid` → rộng 100% toàn màn hình.
- `.container-md` → fluid dưới `md`, từ `md` trở lên mới có max-width kiểu container.

---

## PHẦN B — THỰC HÀNH

### Bài B1 — Landing Page Bootstrap

- File: [bootstrap_landing.html](bootstrap_landing.html)

**Đã làm đúng yêu cầu chính:**

- Navbar `navbar navbar-expand-lg` có logo, menu, search, cart.
- Hero dùng `carousel` 3 slide với overlay text.
- Product grid dùng `row-cols-1 row-cols-md-2 row-cols-lg-4`.
- Card dùng `card`, `card-img-top`, `card-body`, `card-title`, `card-text`.
- Badge sale dùng `badge bg-danger position-absolute`.
- Modal `Xem nhanh` hoạt động bằng Bootstrap modal.
- Footer chia 4 cột.

### Bài B2 — Dashboard Layout

- File: [bootstrap_dashboard.html](bootstrap_dashboard.html)

**Đã làm đúng yêu cầu chính:**

- Sidebar cố định trái bằng `position-fixed`.
- Topbar có breadcrumb và dropdown user.
- 4 stat cards với màu `bg-primary/success/warning/danger`.
- Table dùng `table table-striped table-hover`.
- Form tìm kiếm + filter dùng `input-group`.
- Accordion FAQ và alert success đều có.

---

## PHẦN C — PHÂN TÍCH

### Câu C1 — Tùy biến Bootstrap

1. Đổi màu `$primary` sang `#E63946`

- Dùng Bootstrap source SCSS và Sass compiler.
- Tạo file custom, ví dụ `custom.scss`.
- Gán biến trước khi import Bootstrap:

```scss
$primary: #e63946;
@import "bootstrap/scss/bootstrap";
```

- Chạy compile bằng `sass` hoặc công cụ build của dự án.

2. Vì sao không override trực tiếp `.btn-primary`

- Override trực tiếp chỉ đổi 1 class, không đổi toàn hệ thống.
- Nhiều component khác cũng dùng `$primary`, sẽ bị lệch theme.
- Dùng Sass variables giúp đồng bộ, dễ bảo trì, đúng chuẩn Bootstrap.

---

### Câu C2 — So sánh

**Ví dụ CSS thuần ngắn gọn:**

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 24px;
}

.product-card {
  border: 1px solid #ddd;
  border-radius: 12px;
  overflow: hidden;
}

@media (min-width: 768px) {
  .product-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 992px) {
  .product-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
```

**So sánh với Bootstrap:**

- Số dòng CSS: CSS thuần phải viết nhiều hơn; Bootstrap giảm đáng kể số dòng style riêng.
- Thời gian phát triển: Bootstrap nhanh hơn cho layout phổ biến.
- Khả năng tùy biến: CSS thuần linh hoạt hơn nếu cần thiết kế rất riêng.
- Nên dùng Bootstrap: dashboard, landing page, prototype nhanh, dự án cần ra mắt sớm.
- Không nên dùng Bootstrap: giao diện custom quá cao, cần tối ưu bundle chặt, hoặc design system riêng.

---

## Ghi chú screenshots

- Chụp 3 breakpoint cho [bootstrap_landing.html](bootstrap_landing.html): mobile, tablet, desktop.
- Chụp dashboard ở trạng thái đầy đủ và responsive.
