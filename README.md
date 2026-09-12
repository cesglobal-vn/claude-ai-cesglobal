# Làm chủ Claude AI cho công việc thật - Tài liệu khóa học

Kho tài liệu chính thức cho khóa đào tạo **"Làm chủ Claude AI cho công việc thật"** của **CES Global**: giáo án từng bước, workbook tương tác cho học viên, khung chương trình và bộ file demo dùng để thực hành.

> Khóa 6 buổi x 2.5 giờ (15 giờ thực chiến). Dành cho dân văn phòng, quản lý, freelancer, chủ SME - **không yêu cầu nền tảng lập trình**.

---

## Nội dung khóa học (6 buổi)

| Buổi | Chủ đề | Môi trường | Sản phẩm mang về |
|:---:|---|:---:|---|
| 1 | Làm quen & thiết lập trợ lý Claude cá nhân hóa | Web | 1 Trợ lý Claude nạp sẵn tài liệu, văn phong, SOP của bạn |
| 2 | Tạo công cụ làm việc tương tác bằng Artifacts | Web | 1 Web App / bảng tính tương tác có link chia sẻ |
| 3 | Kết nối Claude với dữ liệu thật (Connectors) | Web | 1 Báo cáo tự động đọc từ Google Drive / Sheets / Gmail |
| 4 | Cho Claude làm việc trên máy tính (Claude Code) | Local | Claude Code hoàn chỉnh + xử lý file hàng loạt |
| 5 | Đóng gói Skill & tạo Agent chuyên vai | Local | 1 Skill quy trình chuẩn + 1 Agent chuyên trách |
| 6 | Xây dựng quy trình tự động hóa hoàn chỉnh | End-to-End | 1 Luồng làm việc tự động khép kín (CLAUDE.md + Agent + Data) |

Chi tiết đầy đủ: xem [`docs/khung-chuong-trinh-6-buoi.md`](docs/khung-chuong-trinh-6-buoi.md).

---

## Cấu trúc thư mục

```
claude-ai/
├── buoi-01-lam-theo-tung-buoc.md   # Giáo án buổi 01 (bản gốc, làm theo từng bước)
├── workbook.html                   # Workbook tương tác buổi 01 (mở bằng trình duyệt)
├── docs/
│   ├── khung-chuong-trinh-6-buoi.md # Khung chương trình đầy đủ 6 buổi
│   └── course-outline-source.md     # Bản outline nguồn (tham chiếu khi soạn bài)
├── demo-files/
│   └── buoi-01/                     # File demo để thực hành (hợp đồng, bảng giá... của công ty giả định NovaTech)
└── scripts/
    └── logo_b64.txt                 # Logo CES (base64) dùng khi dựng lại workbook
```

---

## Hướng dẫn sử dụng

### Dành cho học viên

1. **Mở workbook:** Tải file [`workbook.html`](workbook.html) về máy rồi mở bằng trình duyệt (Chrome, Edge, Safari...). Đây là bản workbook tương tác của buổi 01, đọc và làm theo trực tiếp, không cần cài đặt gì thêm.
2. **Lấy file thực hành:** Dùng các file trong [`demo-files/buoi-01/`](demo-files/buoi-01) làm dữ liệu thực hành cho các bài tập trong buổi (hợp đồng, bảng giá, quy chế chiết khấu... của công ty giả định NovaTech).
3. **Nguyên tắc học:** Ưu tiên làm trên **tài liệu và dữ liệu công việc thật của chính bạn**. File demo chỉ để tập khi bạn chưa có sẵn dữ liệu.

### Dành cho giảng viên / trợ giảng

- Dùng [`buoi-01-lam-theo-tung-buoc.md`](buoi-01-lam-theo-tung-buoc.md) làm **giáo án bám giảng**: nội dung chia theo Phần, mỗi thao tác có bước đánh số và khối thực hành (thẻ `<details>` bấm để mở).
- Dùng [`docs/khung-chuong-trinh-6-buoi.md`](docs/khung-chuong-trinh-6-buoi.md) để nắm mạch năng lực xuyên suốt 6 buổi và sản phẩm đầu ra từng buổi.
- File demo trong `demo-files/buoi-01/` dùng để phát cho học viên chưa mang dữ liệu thật.

---

## Yêu cầu

- **Tài khoản Claude** (claude.ai) - buổi 1-3 làm trên web.
- **Trình duyệt hiện đại** để mở `workbook.html`.
- Buổi 4-6 cần cài **Claude Code** trên máy (có trợ giảng hướng dẫn 1-1 tại lớp).

---

## Ghi chú kỹ thuật

- `workbook.html` là file HTML tự chứa (standalone), chỉ tải font từ Google Fonts khi có mạng; không mạng vẫn đọc được với font dự phòng.
- Các script Python dùng để dựng lại `workbook.html` và sinh file demo là công cụ build cục bộ, **không đưa vào repo** (đã loại qua `.gitignore`). Bản tài liệu đã render sẵn (`workbook.html`, `demo-files/`) là thứ dùng trực tiếp.

---

## Bản quyền

(C) CES Global. Tài liệu phục vụ học viên khóa "Làm chủ Claude AI cho công việc thật". Vui lòng không phát tán ngoài phạm vi khóa học khi chưa được phép.
