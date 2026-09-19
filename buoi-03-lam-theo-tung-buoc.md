# Buổi 3: Kết nối Dữ liệu Đám mây (MCP) & Tự động hóa Google Sheets / Web App

## Nhịp buổi

| Phần | Nội dung chi tiết | Thời lượng dự kiến |
|:---:|---|:---:|
| **0** | **Giải mã MCP & Kết nối Claude với Google Drive:**<br>- MCP là gì? Ẩn dụ "cổng USB vạn năng" của AI.<br>- Kết nối Google Drive Connector trên Claude để đọc dữ liệu từ xa. | 25 phút |
| **1** | **Tư duy Kiến trúc: Google Sheets làm Database cho Web App:**<br>- Mô hình 2 file của Google Apps Script (GAS): `Code.gs` + `Index.html`.<br>- Quy trình "Deploy as Web App" để lấy link website chạy độc lập. | 15 phút |
| **2** | **THỰC HÀNH DEMO 1: Xây dựng Dashboard Analytics Tương tác (Read-Only):**<br>- Prompt chuyên gia phân tích dữ liệu Google Sheets.<br>- Lắp ráp 2 file `Code.gs` và `Index.html` $\rightarrow$ Triển khai Dashboard trực quan. | 45 phút |
| **3** | **THỰC HÀNH DEMO 2: Hệ thống Quản lý Đơn hàng B2B (Tiến hóa qua từng Prompt):**<br>- *Prompt 2.1:* Xây dựng Web App tiếp nhận đơn & đồng bộ 2 chiều vào Sheet.<br>- *Prompt 2.2 (Follow-up 1):* Bổ sung tính năng Xuất Phiếu giao hàng / Hóa đơn PDF.<br>- *Prompt 2.3 (Follow-up 2):* Tạo Menu tùy chỉnh `⚡ ĐƠN HÀNG` ngay trên Google Sheets (tự động gom số liệu & cộng dồn). | 50 phút |
| **4** | **Nghiệm thu Buổi 3, Chia sẻ Sản phẩm & Cầu nối sang Buổi 4** | 15 phút |

---

## PHẦN 0. GIẢI MÃ MCP & KẾT NỐI CLAUDE VỚI GOOGLE DRIVE

### 0.1. Điểm nghẽn từ Buổi 2: Dữ liệu tĩnh vs Dữ liệu sống
- Ở Buổi 2, chúng ta đã tự tay tạo ra những Web App / Artifacts rất đẹp.
- Nhưng nhược điểm lớn nhất là: **Dữ liệu vẫn là dữ liệu chết (tĩnh)**. Bạn phải gõ tay hoặc dán dữ liệu vào.
- Trong công việc thực tế của doanh nghiệp:
  - Bảng giá, danh sách tồn kho, báo cáo doanh số thay đổi từng giờ trên **Google Sheets**.
  - Hợp đồng, hồ sơ dự án nằm rải rác trên các thư mục của **Google Drive**.
  - Không ai có thời gian mỗi ngày đi tải từng file về máy rồi nạp lại vào khung chat AI.
- **Mục tiêu hôm nay:** Cấp quyền cho Claude "nhìn thẳng" vào đám mây Google Workspace để đọc dữ liệu sống và biến Google Sheets thành một cỗ máy tự động hóa hoàn chỉnh!

---

### 0.2. MCP (Model Context Protocol) là gì? Giải thích bằng ngôn ngữ đời thường

> [!NOTE]
> **Ẩn dụ "Cổng USB Type-C" của AI:**
> - Hãy tưởng tượng một chiếc máy tính xách tay xịn xò nhưng **không có bất kỳ cổng cắm nào** (không có USB, không có khe thẻ nhớ, không có cổng mạng). Chiếc máy đó rất thông minh nhưng hoàn toàn bị cô lập với thế giới bên ngoài.
> - **Claude** trước đây cũng như vậy: Mọi dữ liệu bạn muốn nó biết đều phải dùng tay copy-paste hoặc tải file đính kèm vào khung chat.
> - **MCP (Model Context Protocol)** chính là **"Cổng cắm USB vạn năng"** mà Anthropic tạo ra cho Claude. Nhờ chuẩn cắm này, Claude có thể cắm trực tiếp vào:
>   + Google Drive / Google Sheets / Gmail (để đọc tài liệu đám mây).
>   + Cơ sở dữ liệu SQL / CRM nội bộ công ty.
>   + Thư mục trên ổ cứng máy tính cá nhân.
> - Khi bạn bật tính năng **Google Drive Connector** trên Claude, về bản chất bạn đang "cắm một sợi cáp MCP" nối não bộ của Claude với kho tài liệu Google Drive của bạn!

---

### 0.3. Thao tác thực hành: Kết nối Google Drive Connector trên Claude

<details>
<summary><b>Thao tác thực hành: Bật kết nối Google Drive trên Web</b> (bấm để mở)</summary>

1. Mở trang chủ Claude ([claude.ai](https://claude.ai)).
2. Bấm vào ảnh đại diện hoặc tên tài khoản ở góc dưới cùng bên trái màn hình $\rightarrow$ Chọn **Settings**.
3. Ở menu bên trái, tìm mục **Integrations** (hoặc **Connectors / Connected Accounts**).
4. Tìm dòng **Google Drive** $\rightarrow$ Bấm nút **Connect** (hoặc **Add**).
5. Một cửa sổ đăng nhập Google hiện ra: Chọn tài khoản Google làm việc của bạn $\rightarrow$ Bấm **Cho phép (Allow)** cấp quyền đọc tài liệu.
6. Khi trạng thái chuyển sang màu xanh **Connected**, quay lại khung chat.
7. **Thử nghiệm ngay:**
   - Trong ô chat mới, bấm biểu tượng dấu cộng `+` $\rightarrow$ Chọn **Add from Google Drive**.
   - Tìm một file tài liệu bất kỳ trên Drive của bạn $\rightarrow$ Bấm chọn $\rightarrow$ Gõ lệnh: *"Tóm tắt 3 ý chính của tài liệu này cho tôi"*.
   - Quan sát Claude tự động đọc trực tiếp từ Drive mà bạn không cần tải file về máy!
</details>

---

## PHẦN 1. TƯ DUY KIẾN TRÚC: GOOGLE SHEETS LÀM DATABASE CHO WEB APP

### 1.1. Tại sao dân văn phòng không cần học lập trình Database phức tạp?
- Thông thường để lập trình một trang web quản lý đơn hàng hay bảng điều khiển kinh doanh, dân lập trình phải thuê máy chủ (Server), mua tên miền (Domain), và cài đặt cơ sở dữ liệu phức tạp (MySQL, MongoDB...).
- Nhưng với dân văn phòng, **Google Sheets chính là một Cơ sở dữ liệu (Database) hoàn hảo nhất**:
  - Giao diện dạng bảng quen thuộc, ai cũng biết nhìn và chỉnh sửa.
  - Tự động lưu trữ đám mây, chia sẻ nhiều người dùng cùng lúc.
  - Hoàn toàn miễn phí và bảo mật theo tài khoản Google.

---

### 1.2. Giải phẫu cỗ máy Google Apps Script (GAS) Web App
Google Apps Script cho phép bạn dựng một ứng dụng web chạy thẳng trên nền tảng Google bằng đúng **2 file duy nhất**:

```
┌────────────────────────────────────────────────────────────────────────┐
│                   MÔ HÌNH GOOGLE APPS SCRIPT WEB APP                   │
│                                                                        │
│   1. File "Code.gs" (Phía Server - Máy chủ Google):                    │
│      - Đóng vai trò cầu nối: Đọc số liệu từ Sheet, tính toán,          │
│        chuẩn hóa ngày tháng/số tiền, và ghi dữ liệu mới vào Sheet.     │
│                                                                        │
│   2. File "Index.html" (Phía Client - Giao diện Web):                  │
│      - Chứa giao diện người dùng: Các nút bấm, form nhập liệu,         │
│        bảng hiển thị, biểu đồ trực quan (Chart.js / Tailwind CSS).     │
└────────────────────────────────────────────────────────────────────────┘
```

> [!IMPORTANT]
> **Quy trình "Deploy as Web App" (Triển khai ứng dụng):**
> 1. Trong Google Sheets, bấm menu: **Extensions (Tiện ích mở rộng) $\rightarrow$ Apps Script**.
> 2. Dán mã vào `Code.gs` và tạo file `Index.html`.
> 3. Bấm nút **Deploy (Triển khai) $\rightarrow$ New deployment (Triển khai mới)**.
> 4. Chọn loại: **Web app**.
> 5. Cấu hình quyền:
>    - *Execute as:* **Me** (Chạy dưới quyền của bạn).
>    - *Who has access:* **Anyone** (Bất kỳ ai có link đều truy cập được - rất tiện gửi đồng nghiệp).
> 6. Bấm **Deploy** $\rightarrow$ Google cấp cho bạn một đường link web (`https://script.google.com/macros/s/.../exec`). Mở link đó lên là thành một website sống!

---

### 1.3. Phân biệt 2 cấp độ dữ liệu: Bảng thống kê đơn vs Database đa bảng
Để chuẩn bị cho 2 bài thực hành lớn hôm nay, chúng ta cần phân biệt rõ 2 mô hình dữ liệu tương ứng với 2 file Excel mẫu khác nhau:

| Tiêu chí so sánh | DEMO 1: Dashboard Analytics | DEMO 2: Web App Quản lý Đơn hàng |
|---|---|---|
| **Bản chất** | Báo cáo phân tích tĩnh / chỉ đọc (Read-only Analytics) | Hệ thống phần mềm mini tương tác 2 chiều (CRUD Web App) |
| **Cấu trúc file** | **01 Sheet phẳng duy nhất** (`DoanhSo_NovaTech_2026`) | **04 Sheet quan hệ đa bảng** mô phỏng Database thực thụ |
| **File mẫu đi kèm** | `Demo 1 - Du lieu Dashboard Doanh so NovaTech.xlsx` | `Demo 2 - Co so Du lieu He thong Don hang B2B NovaTech.xlsx` |
| **Các bảng dữ liệu** | Gom chung toàn bộ dữ liệu lịch sử vào một bảng để vẽ biểu đồ | 1. `DonHang`: Ghi nhận đơn phát sinh từ Web.<br>2. `DanhMuc_GoiDichVu`: Bảng giá & tính năng để Web tự nạp dropdown.<br>3. `KhachHang_B2B`: Danh bạ MST, địa chỉ để in hóa đơn/PDF.<br>4. `TongHop_DoanhThu`: Nhận số liệu cộng dồn từ Apps Script. |

---

## PHẦN 2. THỰC HÀNH DEMO 1: XÂY DỰNG DASHBOARD ANALYTICS BẰNG GOOGLE APPS SCRIPT

### 2.1. Bài toán thực tế
Bạn có một bảng dữ liệu theo dõi doanh số bán hàng của công ty NovaTech trên Google Sheets (gồm các cột: *Mã đơn, Ngày đặt, Khách hàng, Gói phần mềm, Số tiền, Trạng thái thanh toán, Nhân viên phụ trách*).
- Bạn không muốn sếp hay đối tác phải mở bảng tính chi chít hàng trăm dòng số liệu khô khan.
- Bạn muốn biến nó thành một **Dashboard phân tích trực quan có biểu đồ cột, biểu đồ tròn, bộ lọc theo tháng** chạy độc lập trên trình duyệt web.

---

### 2.2. Câu lệnh Prompt chuẩn cho Demo 1

<details>
<summary><b>Thao tác thực hành: Chạy Prompt tạo Dashboard Analytics</b> (bấm để mở)</summary>

**Bước 1: Mở ô Chat hoặc Project trên Claude**
Copy và dán nguyên văn câu lệnh chuyên gia dưới đây:

```markdown
Hãy đóng vai một Chuyên gia Lập trình Tự động hóa Doanh nghiệp và Chuyên gia Xây dựng Dashboard bằng Google Apps Script (GAS Web App).

1. NHIỆM VỤ:
- Phân tích bảng dữ liệu bán hàng của Google Sheets (gồm các trường: Mã đơn, Ngày đặt hàng, Khách hàng, Gói giải pháp, Doanh thu NET, Hình thức thanh toán, Trạng thái, Sales phụ trách).
- Đề xuất các chỉ số KPI và loại biểu đồ phù hợp nhất:
  + Thẻ số liệu tổng quan: Tổng doanh thu, Tổng đơn hàng, Doanh thu trung bình/đơn, Tỷ lệ đơn thành công.
  + Biểu đồ cột: Xu hướng doanh thu theo tháng.
  + Biểu đồ tròn/donut: Cơ cấu doanh thu theo Gói giải pháp (Starter, Professional, Enterprise).
  + Bảng top 5 khách hàng đóng góp doanh thu lớn nhất.
  + Bộ lọc tương tác: Lọc xem theo Tháng và theo Nhân viên Sales.

2. YÊU CẦU KỸ THUẬT:
- Tách code hoàn chỉnh thành đúng 2 file:
  + File 1: "Code.gs" (Chứa hàm doGet phục vụ trang web và hàm getDataFromSheet đọc dữ liệu từ Google Sheets, chuẩn hóa toàn bộ ngày tháng, số tiền ở phía server).
  + File 2: "Index.html" (Chứa toàn bộ giao diện HTML, Tailwind CSS qua CDN, và thư viện Chart.js để vẽ biểu đồ responsive hiện đại).
- Code phải sạch, có chú thích chi tiết, xử lý tốt khi Sheet có dữ liệu rỗng.

3. KẾT QUẢ CẦN CÓ:
- Giải thích ngắn gọn về các biểu đồ và chỉ số KPI được chọn.
- Cung cấp toàn bộ mã nguồn của cả 2 file Code.gs và Index.html để tôi copy dán dùng ngay.
- Hướng dẫn các bước thao tác step-by-step từ lúc mở Google Sheets đến khi bấm Deploy lấy đường link Web App thành công cho người không chuyên kỹ thuật.
```

**Bước 2: Triển khai mã nguồn vào Google Sheets**
1. Mở một bảng tính Google Sheets mới (hoặc đặt tên là `NovaTech_Sales_Dashboard_2026`).
2. Nhập dữ liệu: Bạn vào **Tệp (File) $\rightarrow$ Nhập (Import) $\rightarrow$ Tải lên (Upload)** file mẫu `demo-files/buoi-03/Demo 1 - Du lieu Dashboard Doanh so NovaTech.xlsx` (gồm 20 dòng doanh số chuẩn của NovaTech), hoặc dán dữ liệu doanh số thực tế của bạn.
3. Bấm menu: **Extensions (Tiện ích mở rộng) $\rightarrow$ Apps Script**.
4. **Tại file `Code.gs`:** Xóa sạch mã mặc định, dán toàn bộ code `Code.gs` mà Claude vừa tạo vào.
5. **Tạo file `Index.html`:**
   - Ở cột bên trái của Apps Script, cạnh chữ *Files*, bấm dấu `+` $\rightarrow$ Chọn **HTML**.
   - Đặt tên file là `Index` (hệ thống tự thêm đuôi `.html`).
   - Xóa sạch mã cũ, dán toàn bộ code `Index.html` của Claude vào.
6. Bấm biểu tượng đĩa mềm **Save (Lưu)** cả 2 file.

**Bước 3: Bấm Deploy để lấy đường link Web App**
1. Ở góc trên bên phải màn hình Apps Script, bấm nút màu xanh **Deploy (Triển khai)** $\rightarrow$ Chọn **New deployment (Triển khai mới)**.
2. Bấm vào biểu tượng bánh răng bên cạnh chữ *Select type* $\rightarrow$ Chọn **Web app**.
3. Điền mô tả: `NovaTech Dashboard v1`.
4. Mục *Who has access*: Chọn **Anyone** (Bất kỳ ai).
5. Bấm **Deploy** $\rightarrow$ Bấm **Authorize access (Ủy quyền truy cập)** $\rightarrow$ Chọn tài khoản Google của bạn $\rightarrow$ Bấm **Advanced (Nâng cao)** $\rightarrow$ Bấm **Go to Untitled project (unsafe)** $\rightarrow$ Bấm **Allow (Cho phép)**.
*(Đây là bước xác thực bảo mật thông thường của Google khi chạy script do chính bạn tạo).*
6. Google sẽ cung cấp đường link **Web app URL**. Bấm **Copy** và mở link đó trên tab mới.

**Bước 4: Trải nghiệm Dashboard sống**
- Màn hình hiện lên một trang Dashboard lung linh với các thẻ KPI doanh số, biểu đồ cột doanh thu theo thời gian và biểu đồ tròn cơ cấu gói cước.
- Thử quay lại file Google Sheets, sửa một số tiền doanh thu bất kỳ $\rightarrow$ Quay lại tab Dashboard bấm F5/Tải lại trang $\rightarrow$ Thấy biểu đồ tự động cập nhật số liệu mới ngay lập tức!
</details>

---

## PHẦN 3. THỰC HÀNH DEMO 2: HỆ THỐNG QUẢN LÝ ĐƠN HÀNG B2B (TIẾN HÓA QUA TỪNG PROMPT)

> [!TIP]
> **Phương pháp phát triển lặp từng bước (Iterative Development):**
> Khi làm việc với AI để xây dựng phần mềm hoặc quy trình tự động hóa, **tuyệt đối không nên quăng một câu lệnh khổng lồ** đòi hỏi làm tất cả mọi thứ cùng một lúc.
> Hãy đi theo quy trình 3 bước chuyên nghiệp:
> - **Bước 1:** Dựng phần lõi cơ bản (Core Web App kết nối Database đa bảng) cho chạy mượt mà trước.
> - **Bước 2:** Bổ sung tính năng nghiệp vụ (Xuất hóa đơn / phiếu giao hàng PDF tra cứu từ bảng đối tác).
> - **Bước 3:** Tạo menu tự động hóa cao cấp trên chính Google Sheets (`⚡ QUẢN LÝ ĐƠN HÀNG` gom số liệu và phân hạng khách hàng).

---

### 3.0. Chuẩn bị Cơ sở Dữ liệu Đa bảng (Multi-sheet Database)
Khác với Demo 1 chỉ có 1 sheet doanh số phẳng, Demo 2 là **một ứng dụng quản trị hoàn chỉnh**, vì vậy chúng ta sẽ sử dụng một file Google Sheets riêng biệt đóng vai trò là một Cơ sở dữ liệu quan hệ (Mini Relational DB):

1. Mở Google Drive $\rightarrow$ Tạo một file Google Sheets mới (đặt tên là `NovaTech_Order_System_2026`).
2. Vào **Tệp (File) $\rightarrow$ Nhập (Import) $\rightarrow$ Tải lên (Upload)** file mẫu:
   `demo-files/buoi-03/Demo 2 - Co so Du lieu He thong Don hang B2B NovaTech.xlsx`.
3. Kiểm tra file đã có đủ **4 Sheet quan hệ**:
   - 📑 **Sheet `DonHang` (Bảng giao dịch):** Lưu trữ toàn bộ lịch sử đơn hàng và là nơi Web App sẽ ghi dòng đơn mới vào.
   - 📑 **Sheet `DanhMuc_GoiDichVu` (Bảng danh mục):** Bảng giá niêm yết và thông số tính năng của 4 gói giải pháp số.
   - 📑 **Sheet `KhachHang_B2B` (Bảng khách hàng):** Danh bạ đối tác gồm Mã KH, Tên công ty, MST, Người đại diện, Hotline, Địa chỉ.
   - 📑 **Sheet `TongHop_DoanhThu` (Bảng tổng hợp):** Bảng đích sẵn sàng nhận dữ liệu tự động cộng dồn từ script.
4. Bấm menu: **Extensions (Tiện ích mở rộng) $\rightarrow$ Apps Script** để sẵn sàng lập trình cùng Claude!

---

### 3.1. Bước 1: Dựng Web App tiếp nhận đơn hàng kết nối đa bảng (Prompt 2.1)

#### Bài toán
Nhân viên kinh doanh hoặc đối tác khi đi thị trường cần một trang web trên điện thoại/laptop để tạo đơn hàng mới. Trang web phải tự động lấy danh mục gói cước và danh bạ khách hàng từ Google Sheets để người dùng chọn, khi bấm "Gửi đơn" thì tự động sinh mã đơn và lưu vào sheet `DonHang`.

<details>
<summary><b>Thao tác thực hành: Chạy Prompt 2.1 dựng Web App Đơn hàng</b> (bấm để mở)</summary>

**Copy và dán câu lệnh sau vào Claude:**

```markdown
Tiếp tục đóng vai chuyên gia Google Apps Script. Bây giờ tôi muốn xây dựng một "HỆ THỐNG TIẾP NHẬN & QUẢN LÝ ĐƠN HÀNG B2B" hoạt động như một ứng dụng Web thực thụ kết nối trực tiếp với file Google Sheets (hiện có các sheet: "DonHang", "DanhMuc_GoiDichVu", "KhachHang_B2B").

Hãy viết mã nguồn gồm 2 file (Code.gs và Index.html) để triển khai thành Web App:

1. XỬ LÝ SERVER (Code.gs):
- Hàm doGet(): Phục vụ giao diện trang Web App.
- Hàm getInitialData(): Đọc dữ liệu từ sheet "DanhMuc_GoiDichVu" (Tên gói, Đơn giá niêm yết) và sheet "KhachHang_B2B" (Tên công ty) để nạp sẵn cho form phía giao diện client.
- Hàm saveOrder(orderData):
  + Tự động sinh Mã đơn hàng tiếp theo (ví dụ: DH-008, DH-009...).
  + Ghi nhận thời gian tạo đơn thực tế (YYYY-MM-DD HH:mm).
  + Chèn một dòng mới vào sheet "DonHang" với trạng thái ban đầu là "Chờ duyệt".
  + Trả về kết quả thành công kèm Mã đơn vừa tạo.
- Hàm getRecentOrders(): Lấy danh sách các đơn hàng gần nhất từ sheet "DonHang" để gửi lên giao diện web.

2. GIAO DIỆN WEB (Index.html):
- Thiết kế giao diện hiện đại bằng Tailwind CSS, responsive mượt mà trên cả máy tính và điện thoại.
- Form tạo đơn hàng B2B gồm:
  + Chọn Khách hàng (Dropdown động nạp từ sheet KhachHang_B2B, có ô nhập khách mới nếu chưa có).
  + Chọn Gói giải pháp (Dropdown động nạp từ sheet DanhMuc_GoiDichVu - tự động hiển thị đơn giá tham chiếu).
  + Số lượng người dùng (ô nhập số).
  + Phương thức thanh toán (Radio: Thanh toán 100% hoặc Chia 3 đợt).
  + Ngày hẹn bàn giao (ô chọn lịch).
  + Ghi chú đơn hàng (ô nhập văn bản).
- Khung "Tạm tính giá trị hợp đồng" tự động tính tiền khi người dùng chọn gói và số lượng.
- Nút bấm nổi bật: "GỬI ĐƠN HÀNG MỚI" (có hiệu ứng loading / disable nút khi đang gửi).
- Bảng danh sách các đơn hàng gần nhất đã đặt (hiển thị ngay bên dưới form để kiểm tra tức thì).

Hãy cung cấp toàn bộ code sạch của 2 file Code.gs và Index.html, có chú thích rõ ràng để tôi dán vào Apps Script dùng ngay nhé!
```

**Thao tác kiểm tra sau khi cập nhật mã:**
1. Trong cửa sổ Apps Script của file `NovaTech_Order_System_2026`:
   - Dán mã vào `Code.gs`.
   - Tạo file `Index.html` và dán mã giao diện vào $\rightarrow$ Bấm **Save (Lưu)**.
2. Bấm **Deploy $\rightarrow$ New deployment $\rightarrow$ Chọn Web app $\rightarrow$ Who has access: Anyone $\rightarrow$ Deploy $\rightarrow$ Ủy quyền truy cập**.
3. Mở link Web App:
   - Thấy dropdown Khách hàng và Gói dịch vụ tự động load tên công ty và tên gói từ file Sheets!
   - Thử gửi một đơn hàng: *"Công ty TNHH Cơ khí Hồng Hà - Gói NovaPro Cloud - 45 user"* $\rightarrow$ Bấm **Gửi đơn hàng mới**.
4. Mở tab Google Sheets: Bảng `DonHang` vừa tự động xuất hiện dòng đơn mới với mã `DH-008` chuẩn xác!
</details>

---

### 3.2. Bước 2: Nâng cấp tính năng Xuất Phiếu giao hàng / Thỏa thuận dịch vụ PDF (Prompt 2.2 - Follow-up 1)

#### Bài toán
Sau khi đơn hàng được ghi nhận, nhân viên kinh doanh cần in ngay Phiếu tiếp nhận đơn hàng hoặc tải file PDF để gửi Zalo cho khách hàng. Phiếu này cần tự động tra cứu Mã số thuế, Địa chỉ, Người đại diện từ sheet `KhachHang_B2B`.

<details>
<summary><b>Thao tác thực hành: Chạy Prompt 2.2 bổ sung Xuất PDF</b> (bấm để mở)</summary>

**Gõ tiếp ngay câu lệnh follow-up này vào phiên chat:**

```markdown
Web App đơn hàng hoạt động rất tuyệt vời! Bây giờ hãy nâng cấp thêm tính năng sau:

Ở mỗi dòng đơn hàng trong danh sách đơn hàng đã đặt, hãy thêm một cột "Thao tác" với nút bấm:
- Nút "Xuất Phiếu Giao Hàng (PDF/In)" (icon máy in).
- Khi người dùng bấm vào nút này của đơn hàng nào, hãy mở ra một popup Modal hiển thị mẫu "PHIẾU TIẾP NHẬN ĐƠN HÀNG & THỎA THUẬN DỊCH VỤ" chuẩn khổ A4 dọc gồm:
  + Header thương hiệu NovaTech (MST: 0109887766, Hotline: 1900 6868, Địa chỉ: Tòa nhà TechPark, Cầu Giấy, Hà Nội).
  + Toàn bộ thông tin đơn hàng lấy từ sheet "DonHang" (Mã đơn, Gói dịch vụ, Ngày hẹn bàn giao, Giá trị).
  + Tự động tra cứu và hiển thị thông tin pháp lý của đối tác từ sheet "KhachHang_B2B" (Tên công ty, Mã số thuế, Người đại diện ký, Địa chỉ trụ sở).
  + Bảng chiết tính thanh toán và thông tin tài khoản chuyển khoản ngân hàng Vietcombank.
  + Hai khung chữ ký xác nhận của Đại diện NovaTech và Đại diện Khách hàng.
  + Nút "In / Lưu file PDF" kích hoạt lệnh in trình duyệt chuẩn CSS @media print (chỉ in đúng tờ phiếu A4, ẩn toàn bộ form web và các nút bấm xung quanh).

Hãy cập nhật code cho Index.html (và Code.gs nếu cần hàm tra cứu thông tin khách hàng) để tôi cập nhật nhé!
```

**Thao tác kiểm tra:**
1. Cập nhật mã vào `Index.html` (và `Code.gs` nếu có) $\rightarrow$ Bấm **Save**.
2. Bấm **Deploy $\rightarrow$ Manage deployments $\rightarrow$ Bút chì (Edit) $\rightarrow$ Version: New version $\rightarrow$ Deploy**.
3. Mở link Web App $\rightarrow$ Trong bảng đơn hàng, bấm nút icon máy in ở một đơn hàng bất kỳ.
4. Popup Phiếu A4 hiện lên với đầy đủ tên công ty, MST, địa chỉ và thông tin đơn hàng $\rightarrow$ Bấm nút "In / Lưu PDF" để xem bản in đẹp chuẩn doanh nghiệp!
</details>

---

### 3.3. Bước 3: Thêm Menu tùy chỉnh `⚡ QUẢN LÝ ĐƠN HÀNG` ngay trên Google Sheets (Prompt 2.3 - Follow-up 2)

#### Bài toán (Kế thừa bài toán bóc tách & tổng hợp thực chiến của kỹ sư)
Người quản lý hoặc kế toán không cần mở Web App mà làm việc trực tiếp trên file Google Sheets. Họ muốn trên thanh công cụ của Google Sheets xuất hiện riêng menu **`⚡ QUẢN LÝ ĐƠN HÀNG`** để tự động hóa:
1. **Tự động gom nhóm khách hàng & cộng dồn doanh số:** Quét toàn bộ sheet `DonHang`, những khách hàng đặt nhiều đơn sẽ được gộp lại thành 1 dòng duy nhất, cộng dồn tổng giá trị tích lũy, đếm số lượng đơn, tra cứu MST từ sheet `KhachHang_B2B`, tự động phân hạng khách hàng (*VIP Diamond*, *Gold*, *Standard*), và xuất sang sheet `TongHop_DoanhThu`.
2. **Dọn dẹp bảng tính / Chuẩn hóa dữ liệu.**

<details>
<summary><b>Thao tác thực hành: Chạy Prompt 2.3 tạo Menu tự động hóa trên Sheets</b> (bấm để mở)</summary>

**Gõ tiếp câu lệnh follow-up cuối cùng này vào Claude:**

```markdown
Bây giờ, hãy bổ sung thêm tính năng TỰ ĐỘNG HÓA TRỰC TIẾP TRÊN GOOGLE SHEETS bằng Google Apps Script:

Hãy thêm vào file Code.gs hàm onOpen() để khi bất kỳ ai mở file Google Sheets này lên, trên thanh công cụ (cạnh menu Help) sẽ xuất hiện một menu tùy chỉnh riêng mang tên:
"⚡ QUẢN LÝ ĐƠN HÀNG" với 2 chức năng tự động:

1. Dòng lệnh 1: "📊 Tổng hợp & Phân hạng Khách hàng"
- Khi bấm vào:
  + Quét toàn bộ dữ liệu ở sheet "DonHang".
  + Gom nhóm (Group by) theo Tên khách hàng: Những khách hàng có nhiều đơn hàng (như Dệt may Nam Định, BĐS An Phú...) sẽ được gộp lại thành 1 dòng duy nhất, tự động tính tổng số đơn và CỘNG DỒN TỔNG GIÁ TRỊ TÍCH LŨY.
  + Tra cứu Mã số thuế tương ứng từ sheet "KhachHang_B2B".
  + Tự động phân hạng khách hàng dựa trên tổng doanh số tích lũy:
    * Doanh thu >= 100.000.000 VNĐ: Hạng "💎 VIP Diamond"
    * Doanh thu từ 40.000.000 đến dưới 100.000.000 VNĐ: Hạng "🥇 Gold"
    * Doanh thu dưới 40.000.000 VNĐ: Hạng "🥈 Standard"
  + Tự động ghi kết quả vào sheet "TongHop_DoanhThu" (xóa dữ liệu cũ, kẻ bảng viền đẹp mắt, tô màu header xanh lục đậm chữ trắng, định dạng số tiền VNĐ chuẩn).
  + Hiện thông báo Toast góc dưới màn hình: "Đã tổng hợp thành công X khách hàng!".

2. Dòng lệnh 2: "🧹 Dọn dẹp dòng trống"
- Tự động quét và xóa các dòng trống vô tình tạo ra trong quá trình thao tác bảng tính.

Hãy bổ sung đoạn mã này vào file Code.gs và hướng dẫn tôi kích hoạt chạy thử trên Google Sheets!
```

**Thao tác kiểm tra trên Google Sheets:**
1. Dán đoạn mã mới bổ sung vào cuối file `Code.gs` $\rightarrow$ Bấm **Save**.
2. Quay lại tab bảng tính Google Sheets $\rightarrow$ Bấm **F5 (Tải lại trang)**.
3. Nhìn lên thanh menu trên cùng (cạnh chữ *Help / Trợ giúp*): Xuất hiện menu mới toanh **`⚡ QUẢN LÝ ĐƠN HÀNG`**!
4. Bấm vào menu **`⚡ QUẢN LÝ ĐƠN HÀNG` $\rightarrow$ Chọn "📊 Tổng hợp & Phân hạng Khách hàng"**.
5. Mở sheet `TongHop_DoanhThu`: Toàn bộ các khách hàng đã được gom gọn, doanh số được cộng dồn chính xác 100%, phân hạng VIP lấp lánh chỉ trong 2 giây!
</details>

---

## PHẦN 4. NGHIỆM THU BUỔI 3, CHIA SẺ & BƯỚC NGOẶT SANG BUỔI 4

### 4.1. Nghiệm thu Buổi 3: Danh mục kiểm tra thành phẩm

Hãy tự kiểm tra lại các sản phẩm số bạn đã tạo ra trước khi kết thúc buổi học:

#### Về hiểu biết bản chất:
- [ ] Hiểu rõ **MCP (Model Context Protocol)** là gì qua ẩn dụ "cổng USB Type-C của AI".
- [ ] Nắm được cơ chế dùng **Google Sheets làm Cơ sở dữ liệu (Database)** để nuôi sống Web App.
- [ ] Hiểu cấu trúc 2 file của Apps Script: `Code.gs` (Server xử lý dữ liệu) và `Index.html` (Client hiển thị giao diện).

#### Về sản phẩm số cầm về dùng ngay:
- [ ] **Sản phẩm 1:** 01 Dashboard Analytics phân tích dữ liệu Google Sheets trực quan bằng biểu đồ động, có đường link web công khai chia sẻ được.
- [ ] **Sản phẩm 2:** 01 Hệ thống Web App Quản lý Đơn hàng (có form gửi đơn tự động lưu vào Google Sheets + chức năng xuất Phiếu giao hàng PDF).
- [ ] **Sản phẩm 3:** 01 Menu tùy chỉnh `⚡ QUẢN LÝ ĐƠN HÀNG` hoạt động trực tiếp trên Google Sheets giúp tự động lọc trùng và cộng dồn số liệu chỉ bằng 1 cú click chuột!

---

### 4.2. Chia sẻ thành quả tại lớp
- Học viên copy đường link Web App vừa Deploy của mình và dán vào nhóm Zalo lớp để đồng nghiệp và giảng viên cùng mở thử trên điện thoại, bấm gửi thử đơn hàng xem dữ liệu có nhảy về Google Sheets không!

---

### 4.3. Cầu nối sang Buổi 4: Cho Claude xuống làm việc trên máy tính (Claude Desktop)

- **Thành tựu hôm nay:** Bạn đã làm chủ hoàn toàn dữ liệu đám mây (Google Drive, Google Sheets) và biết biến Claude thành một lập trình viên tự động hóa bảng tính mà không cần biết viết code.
- **Bài toán mới nảy sinh cho Buổi 4:**
  - *"Nếu công ty bạn có hàng trăm file Word, hợp đồng scan nặng hàng trăm MB nằm ngay trong thư mục ổ đĩa máy tính (ổ C, ổ D), không thể tải hết lên Google Drive được thì sao?"*
  - *"Làm sao để Claude tự động mở từng file trên máy tính của bạn, trích xuất dữ liệu, sửa lỗi chính tả hàng loạt và đổi tên file tự động?"*
- 👉 **Hẹn gặp lại ở Buổi 4: Đưa Claude xuống máy tính với ứng dụng CLAUDE DESKTOP (Chế độ Cowork & Code)!**
