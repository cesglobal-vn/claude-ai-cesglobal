# Buổi 3: Kết nối Dữ liệu Đám mây (MCP) & Dashboard từ Google Sheets

## Nhịp buổi

| Phần | Nội dung chi tiết | Thời lượng dự kiến |
|:---:|---|:---:|
| **0** | **Giải mã MCP, Claude in Chrome & kết nối Google Drive, Gmail:**<br>- MCP là gì? Ẩn dụ "cổng USB vạn năng" của AI.<br>- Cài Claude in Chrome, kết nối Google Drive & Gmail trong app Claude.<br>- File chỉ dẫn toàn cục: dặn Claude quy tắc làm việc một lần.<br>- Claude in Chrome: liệt kê tab, đọc báo giúp.<br>- Gmail: phân loại hòm thư 7 ngày gần nhất. | 40 phút |
| **1** | **Ảnh chụp và dữ liệu sống:**<br>- 2 loại dashboard, 2 mục đích.<br>- Nhờ Claude sao chép file dữ liệu mẫu về Drive. | 10 phút |
| **2** | **DEMO 1: Báo cáo kinh doanh tháng bằng file HTML ("ảnh chụp"):**<br>- Đọc dữ liệu, tạo báo cáo tháng 3/2026, tinh chỉnh, thử nghiệm "ảnh chụp". | 45 phút |
| **3** | **DEMO 2: Web app quản lý bán hàng trên Apps Script (Claude in Chrome tự thao tác):**<br>- Kiểm tra Claude in Chrome, mở sheet, giao việc dựng web app thêm sửa xóa kèm dashboard, kiểm chứng đọc ghi vào Sheet. | 40 phút |
| **4** | **Nghiệm thu Buổi 3 & Cầu nối sang Buổi 4** | 15 phút |

---

## PHẦN 0. GIẢI MÃ MCP, CLAUDE IN CHROME & KẾT NỐI GOOGLE DRIVE, GMAIL

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

### 0.3. Chuẩn bị: cài Claude in Chrome và kết nối Google Drive, Gmail

<details>
<summary><b>Thao tác thực hành A: Cài tiện ích Claude in Chrome</b> (bấm để mở)</summary>

1. Mở Google Chrome, vào trang tiện ích [Claude in Chrome trên Chrome Web Store](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn).
2. Bấm **Thêm vào Chrome (Add to Chrome)**, rồi ghim biểu tượng Claude lên thanh công cụ của Chrome.
3. Đăng nhập tiện ích bằng **đúng tài khoản Claude** đang dùng trong app Claude trên máy.

*Tiện ích chạy trên Google Chrome và dành cho các gói trả phí của Claude.*
</details>

<details>
<summary><b>Thao tác thực hành B: Kết nối Google Drive và Gmail</b> (bấm để mở)</summary>

1. Trong app Claude, bấm dấu `+` cạnh ô nhập -> **Add connectors** (hoặc vào **Settings -> Connectors**).
2. Chọn **Google Drive** -> **Connect** -> chọn tài khoản Google làm việc -> **Cho phép (Allow)**. Làm tương tự với **Gmail**.
3. Trạng thái chuyển sang **Connected** là xong.
</details>

> [!WARNING]
> **Chọn đúng tài khoản Google:** connector đăng nhập tài khoản Google nào thì Claude đọc mail và tạo file trên tài khoản đó. Máy có nhiều tài khoản Google thì kiểm tra kỹ trước khi bấm Allow.

---

### 0.4. File chỉ dẫn toàn cục: dặn Claude quy tắc làm việc một lần cho mọi phiên

Giống ô Instructions của Projects ở Buổi 1, nhưng áp dụng cho **mọi phiên làm việc** của Claude trên máy. Làm 2 bước: hỏi trước, chưa sửa gì; xem xong mới thêm quy tắc.

<details>
<summary><b>Thao tác thực hành: Hỏi vị trí file, rồi thêm quy tắc làm việc</b> (bấm để mở)</summary>

**Prompt 0.4a - Hỏi vị trí file chỉ dẫn toàn cục:**

```text
File chỉ dẫn toàn cục (global) của bạn nằm ở đâu trên máy tôi?
Nếu file đã có thì đọc cho tôi nội dung hiện tại. Nếu chưa có thì cho tôi biết bạn sẽ tạo file ở đâu.
Chưa sửa gì cả.
```

**Quan sát:** Claude cho biết đường dẫn file (thường là file `CLAUDE.md` trong thư mục `.claude` của tài khoản máy tính) và đọc nội dung nếu file đã có. Câu "Chưa sửa gì cả" giúp Claude chỉ xem, không tự ghi.

**Prompt 0.4b - Thêm quy tắc làm việc:**

```text
Thêm các quy tắc sau vào file chỉ dẫn toàn cục của bạn. Nếu file đã có nội dung thì giữ nguyên, chỉ thêm vào cuối:

Quy tắc làm việc với tôi
1. Luôn trả lời bằng tiếng Việt có dấu đầy đủ, rõ ý, chuyên nghiệp.
2. Yêu cầu chưa rõ hoặc thiếu dữ liệu thì hỏi lại, không tự đoán.
3. Chỉ sửa đúng phần tôi yêu cầu, không tự ý sửa thêm chỗ khác.
4. Trước khi xóa hoặc ghi đè file nào, phải hỏi tôi trước.
```

**Quan sát:** Claude thêm 4 quy tắc vào cuối file, giữ nguyên phần đã có. Từ phiên sau Claude tự tuân theo mà không cần dặn lại. Buổi 4 sẽ học tiếp file `CLAUDE.md` riêng cho từng thư mục dự án.
</details>

---

### 0.5. Claude in Chrome: cho Claude tự thao tác trên trình duyệt

<details>
<summary><b>Thao tác thực hành: Kiểm tra Claude in Chrome và nhờ đọc báo</b> (bấm để mở)</summary>

**Prompt 0.5a - Kiểm tra Claude in Chrome:**

```text
Bạn có dùng được Claude in chrome trên máy tôi không? Nếu có thì hãy liệt kê ra các tab đang mở
```

**Quan sát:** Claude kết nối với tiện ích và liệt kê các tab đang mở trong Chrome. Nếu Claude báo chưa kết nối được: kiểm tra Chrome đang mở, tiện ích đã cài và đăng nhập đúng tài khoản Claude.

**Prompt 0.5b - Đọc báo giúp tôi:**

```text
mở cho tôi trang báo lao động và cho tôi tiêu đề và nội dung 3 bài viết mới nhất về chủ đề kinh doanh đi
```

**Quan sát:** Claude tự mở tab mới, vào báo Lao động, tìm chuyên mục kinh doanh, đọc và tóm tắt 3 bài mới nhất. Lần đầu vào một trang mới, tiện ích có thể hỏi xin phép: bấm cho phép.
</details>

---

### 0.6. Gmail: kiểm tra kết nối và phân loại hòm thư công việc

<details>
<summary><b>Thao tác thực hành: Kiểm tra kết nối và phân loại hòm thư</b> (bấm để mở)</summary>

**Prompt 0.6a - Kiểm tra kết nối Gmail và Drive:**

```text
bạn có kết nối được với gmail và drive của tôi không?
```

**Quan sát:** Claude xác nhận đã kết nối và cho biết đang dùng tài khoản Google nào. Nếu sai tài khoản, đổi lại trong Settings -> Connectors trước khi làm tiếp.

**Prompt 0.6b - Phân loại hòm thư 7 ngày gần nhất:**

```text
Hãy quét các email tôi nhận được trong 7 ngày gần nhất trong hòm thư Gmail và thực hiện:

1. Phân loại email thành 3 nhóm rõ ràng:
   - [KHẨN CẤP / CẦN XỬ LÝ NGAY]: Email từ cấp trên, đối tác quan trọng, hoặc có thời hạn gấp.
   - [CẦN THEO DÕI]: Email cập nhật tiến độ, thông báo nội bộ, không cần phản hồi ngay.
   - [TIN TỨC / BỎ QUA]: Email quảng cáo, bản tin tiếp thị, thư tự động từ hệ thống.

2. Với các email thuộc nhóm [KHẨN CẤP / CẦN XỬ LÝ NGAY]:
   - Tóm tắt 1 câu ngắn gọn nội dung người gửi yêu cầu.
   - Đề xuất 1 việc cụ thể tôi cần làm hôm nay.
```

**Trải nghiệm kết quả:** Claude tự quét hòm thư 7 ngày qua và trả về bảng phân loại kèm việc cần làm hôm nay, giúp nắm nhanh các đầu việc quan trọng mà không cần mở từng email.
</details>

---

## PHẦN 1. ẢNH CHỤP VÀ DỮ LIỆU SỐNG: 2 CÁCH LÀM DASHBOARD TỪ GOOGLE SHEETS

### 1.1. Hai loại dashboard, hai mục đích khác nhau

Khi Claude đã "nhìn thẳng" được vào Google Sheets qua connector, có 2 cách biến bảng số liệu thành dashboard. Hiểu đúng sự khác nhau sẽ biết chọn cách nào cho từng việc:

| Tiêu chí | Demo 1 - File HTML: "ảnh chụp" | Demo 2 - Web app Apps Script: "dữ liệu sống" |
|---|---|---|
| **Lấy số liệu** | Đọc Sheet **1 lần** lúc tạo, rồi "chép" số vào trong file | Đọc thẳng Sheet **mỗi lần mở** trang web |
| **Sửa Sheet** | File **không đổi**. Muốn số mới phải nhờ Claude làm lại | Web app **tự đổi theo**; thêm, sửa, xóa trên web là **ghi thẳng vào Sheet** |
| **Hợp cho** | Báo cáo **chốt kỳ** (tháng, quý), gửi sếp, gửi khách, in PDF | **Quản lý hằng ngày** danh mục, đơn hàng, khách hàng, kèm dashboard thống kê |

> [!NOTE]
> **Ví von dễ nhớ:**
> - File HTML giống **tấm ảnh chụp** cửa hàng lúc 9 giờ sáng: đẹp, gửi đi được, nhưng 10 giờ có khách mới thì ảnh vẫn là cảnh lúc 9 giờ.
> - Web app Apps Script giống **màn hình camera kiêm quầy thu ngân**: mở lên là thấy cửa hàng ngay lúc này, và nhập đơn được luôn tại chỗ.

---

### 1.2. Chuẩn bị dữ liệu: nhờ Claude sao chép file mẫu về Drive

Không cần tự tải file lên Drive: dán link file mẫu của lớp và nhờ Claude tạo bản sao qua connector Google Drive. Thay `....` bằng tên của anh chị.

<details>
<summary><b>Thao tác thực hành: Sao chép file dữ liệu mẫu về Drive</b> (bấm để mở)</summary>

**Prompt 1.0 - Sao chép file dữ liệu mẫu về Drive:**

```text
https://docs.google.com/spreadsheets/d/11q_TGO8mDPIvKzUFXk3QwYq-3HWoHqg8GtKYDkeAHts/edit?usp=sharing
bạn hãy tạo bản sao sheet này về drive của tôi nhé. Đặt tên là .... - Thực hành buổi 3
```

**Quan sát:** Claude tạo bản sao trong Google Drive (của tài khoản đang kết nối) và gửi lại link file mới. Dùng link này cho chỗ `{Dán link gg sheets}` ở các câu lệnh phía sau. Nếu dùng số liệu thật của công ty thì tự tải file lên Drive và lấy link tương tự.

*File mẫu có sheet `DonHang` gồm 50 đơn hàng tháng 2 và tháng 3/2026 (mã đơn, khách hàng, gói giải pháp, thành tiền, ngày hẹn bàn giao, trạng thái), cùng các sheet danh mục gói dịch vụ và danh bạ khách hàng.*
</details>

---

## PHẦN 2. DEMO 1: BÁO CÁO KINH DOANH THÁNG BẰNG FILE HTML ("ẢNH CHỤP")

### 2.1. Bước 1: Cho Claude đọc và làm quen dữ liệu

**Bài toán:** cuối tháng, sếp cần một bản báo cáo kinh doanh tháng 3 đẹp, rõ ràng để đọc và lưu lại. Trước khi làm báo cáo, cho Claude đọc dữ liệu để chắc nó hiểu đúng bảng số liệu. Gõ tiếp trong cùng phiên vừa sao chép file (chữ "file Google Sheets trên" là file vừa tạo ở Prompt 1.0).

<details>
<summary><b>Thao tác thực hành: Đọc và làm quen dữ liệu (Prompt 1.1)</b> (bấm để mở)</summary>

```text
Hãy đọc file Google Sheets trên

Cho tôi biết:
- File có những sheet nào, mỗi sheet chứa thông tin gì.
- Dữ liệu đơn hàng trải từ tháng nào đến tháng nào, mỗi tháng có bao nhiêu đơn.
- 3 con số đáng chú ý nhất mà một người quản lý nên biết.
```

**Quan sát:** Claude đọc file qua connector Google Drive và tóm tắt cấu trúc, ví dụ sheet `DonHang` có 16 đơn tháng 2 và 34 đơn tháng 3/2026. Nếu Claude hiểu sai cột nào, sửa ngay ở bước này trước khi làm báo cáo.
</details>

---

### 2.2. Bước 2: Tạo báo cáo tháng dạng file HTML

<details>
<summary><b>Thao tác thực hành: Dashboard báo cáo tháng 3/2026 (Prompt 1.2)</b> (bấm để mở)</summary>

```text
Dựa vào thông tin của sheets trên, hãy làm cho tôi 1 dashboard báo cáo kinh doanh THÁNG 3/2026 dạng file HTML, lưu vào thư mục Download với tên bao-cao-thang-03-2026.html:
- Thẻ số liệu: tổng doanh thu, số đơn, giá trị trung bình mỗi đơn, số khách hàng.
- Biểu đồ doanh thu theo gói giải pháp và biểu đồ số đơn theo trạng thái.
- Bảng top 5 khách hàng có giá trị đơn lớn nhất trong tháng.
- So sánh với tháng 2/2026: tăng hay giảm bao nhiêu %.
- Ghi rõ dòng "Số liệu chốt ngày ..." ở đầu báo cáo.
- Giao diện hiện đại, dễ đọc.
có thể tự đề xuất sao cho đầy đủ trên dashboard
```

**Kiểm tra:**
1. File `bao-cao-thang-03-2026.html` xuất hiện trong thư mục **Download**, bấm đúp để mở bằng trình duyệt.
2. Đối chiếu 1-2 con số với Google Sheets (ví dụ tổng số đơn tháng 3) để chắc Claude tính đúng.
</details>

---

### 2.3. Bước 3: Tinh chỉnh cho đúng ý người đọc

Báo cáo cho sếp cần nhận định, không chỉ có số. Gõ tiếp trong cùng phiên:

<details>
<summary><b>Thao tác thực hành: Thêm nhận định, nút in PDF, đổi tone màu (Prompt 1.3, 1.4)</b> (bấm để mở)</summary>

**Prompt 1.3 - Thêm nhận định và nút in PDF:**

```text
Báo cáo ổn rồi. Hãy bổ sung:
- 3 nhận định ngắn về tình hình kinh doanh tháng 3 đặt ngay đầu báo cáo (điểm tốt, điểm cần lo, việc nên làm tiếp).
- Một nút "In / Lưu PDF" để tôi gửi báo cáo cho sếp, khi in chỉ in nội dung báo cáo.
```

**Prompt 1.4 (tùy chọn) - Đổi tone màu theo logo công ty:**

```text
Đổi tone màu của báo cáo theo màu chủ đạo của logo công ty tôi (tôi gửi kèm file logo), và chèn logo vào góc trên báo cáo.
```
</details>

---

### 2.4. Bước 4: Thử nghiệm "ảnh chụp"

<details>
<summary><b>Thao tác thực hành: Sửa Sheet và cập nhật lại báo cáo (Prompt 1.5)</b> (bấm để mở)</summary>

1. Mở Google Sheets, sửa cột **Thành tiền (VNĐ)** của một đơn tháng 3 (ví dụ tăng thêm 100.000.000).
2. Mở lại file `bao-cao-thang-03-2026.html`: tổng doanh thu **vẫn là số cũ**. Đó chính là "ảnh chụp".
3. Muốn số mới thì phải nhờ Claude làm lại:

```text
Tôi vừa sửa số liệu trong Google Sheets. Hãy đọc lại file và cập nhật báo cáo tháng 3 với số liệu mới nhất, giữ nguyên giao diện.
```
</details>

> [!TIP]
> **Kết luận Demo 1:** File HTML rất hợp cho **báo cáo chốt kỳ**: số liệu đứng yên đúng như thời điểm chốt, gửi đi hay in ra đều được. Nhưng nếu cần theo dõi **từng ngày** thì mỗi lần phải nhờ làm lại. Đó là lý do có Demo 2.

---

## PHẦN 3. DEMO 2: WEB APP QUẢN LÝ BÁN HÀNG TRÊN APPS SCRIPT, CLAUDE IN CHROME TỰ THAO TÁC

**Bài toán:** chủ doanh nghiệp đang theo dõi doanh thu, đơn hàng, khách hàng trên một file Google Sheets nhiều sheet, thao tác trực tiếp trên bảng rất khó xem. Muốn có một trang web riêng để **thêm, sửa, xóa** danh mục, đơn hàng, khách hàng và có **dashboard thống kê nhanh**, dữ liệu vẫn lưu thẳng vào Google Sheets.

> [!NOTE]
> **Vì sao dùng Apps Script:**
> - **Google Apps Script** là công cụ có sẵn trong Google Sheets, cho phép dựng một trang web **đọc và ghi thẳng vào Sheet**: mở web là thấy số liệu mới nhất, nhập trên web là Sheet có dòng mới.
> - Anh chị không cần biết code: **Claude in Chrome** sẽ tự mở Apps Script, viết code, lưu và triển khai thành web app.

> [!WARNING]
> **Hai bước anh chị tự làm, không để Claude làm thay:**
> - **Cấp quyền (Authorize / Allow):** lần đầu chạy, Google hỏi cho phép script truy cập tài khoản. Claude sẽ dừng lại, anh chị tự đọc và tự bấm.
> - **Ai được mở web app:** đây là số liệu kinh doanh nội bộ, nên chọn chỉ mình mình hoặc trong công ty. Không chọn "Anyone" (ai có link cũng xem và sửa được).

### 3.1. Bước 1: Kiểm tra Claude in Chrome

<details>
<summary><b>Thao tác thực hành: Kiểm tra Claude in Chrome (Prompt 2.1)</b> (bấm để mở)</summary>

```text
Bạn có dùng được Claude in chrome trên máy tôi không?
```

**Quan sát:** Claude xác nhận đã kết nối được tiện ích Claude in Chrome. Nếu chưa được: kiểm tra Chrome đang mở, tiện ích đã cài và đăng nhập đúng tài khoản Claude (như mục 0.3).
</details>

---

### 3.2. Bước 2: Mở file Google Sheets xem thử

Thay `{Dán link gg sheets}` bằng link file Google Sheets tổng hợp doanh thu của anh chị.

<details>
<summary><b>Thao tác thực hành: Mở sheet xem thử (Prompt 2.2)</b> (bấm để mở)</summary>

```text
{Dán link gg sheets}
mở sheet này xem thử cho tôi nhé
```

**Quan sát:** Claude in Chrome mở file trong một tab mới của Chrome và tóm tắt các sheet, các cột dữ liệu đang có. Lần đầu vào trang Google Sheets, tiện ích có thể hỏi xin phép: bấm cho phép.
</details>

---

### 3.3. Bước 3: Giao việc dựng web app trên Apps Script

<details>
<summary><b>Thao tác thực hành: Dựng web app thêm sửa xóa và dashboard (Prompt 2.3)</b> (bấm để mở)</summary>

```text
Đây là file excel tổng hợp doanh thu của tôi, hiện tôi chỉ thao tác trên này thì hơi khó xem, tôi biết là có thể dùng AppsScript để làm web và kết nối với gg sheet để lưu luôn. Hãy dùng claude in chrome và tự thao tác với AppsScript rồi tự tạo code đưa lên cho tôi nhé.
Tôi muốn trên web tôi sẽ thêm sửa xóa được danh mục, đơn hàng, khách hàng luôn,... Có dashboard để xem nhanh thống kê luôn.
Có gì thắc mắc thì hỏi lại tôi cho chắc nhé
```

**Quan sát:**
1. Claude **hỏi lại vài câu** cho chắc (ví dụ: sheet nào là danh mục, đơn hàng, khách hàng; dashboard cần chỉ số gì; ai được mở web app). Trả lời ngắn gọn như nói với đồng nghiệp.
2. Claude in Chrome tự mở **Tiện ích mở rộng -> Apps Script** từ file Sheets, viết code, lưu lại rồi vào **Triển khai -> Ứng dụng web**. Anh chị chỉ cần theo dõi trên Chrome.
3. Tới bước **cấp quyền**, Claude dừng lại: anh chị tự bấm cho phép.
4. Claude gửi **link web app**. Mở link: có trang dashboard thống kê và các trang quản lý danh mục, đơn hàng, khách hàng.
</details>

---

### 3.4. Bước 4: Kiểm chứng web app đọc ghi thẳng vào Google Sheets

1. Trên web app, **thêm một đơn hàng mới** rồi mở Google Sheets: sheet đơn hàng có thêm dòng mới.
2. **Sửa một con số trực tiếp trong Google Sheets**, quay lại web app bấm tải lại trang: dashboard đổi theo.
3. Thử sửa, xóa một khách hàng trên web và đối chiếu lại trong Sheet.
4. Muốn thêm tính năng (lọc theo tháng, xuất báo cáo...) thì nói tiếp với Claude, Claude in Chrome sẽ sửa code và triển khai lại.

> [!TIP]
> **Kết luận Demo 2:** Báo cáo gửi đi thì dùng **file HTML** (Demo 1): số liệu đứng yên đúng thời điểm chốt. Còn quản lý hằng ngày thì dùng **web app Apps Script** (Demo 2): vừa xem số liệu mới nhất, vừa thêm, sửa, xóa ngay trên web, mọi thứ lưu thẳng vào Google Sheets.

---

## PHẦN 4. NGHIỆM THU BUỔI 3 & CẦU NỐI SANG BUỔI 4

### 4.1. Nghiệm thu Buổi 3

#### Về hiểu biết bản chất:
- [ ] Hiểu MCP (Model Context Protocol) qua ẩn dụ "cổng USB Type-C của AI".
- [ ] Phân biệt dashboard "ảnh chụp" (file HTML) và "dữ liệu sống" (web app Apps Script đọc ghi thẳng vào Sheet), biết khi nào dùng cái nào.
- [ ] Biết tự bấm bước cấp quyền Apps Script, không để Claude bấm thay.
- [ ] Biết chọn đúng người được mở web app (chỉ mình mình hoặc trong công ty), không để "Anyone".

#### Về sản phẩm số mang về:
- [ ] Có file chỉ dẫn toàn cục với 4 quy tắc làm việc riêng của mình.
- [ ] Cài Claude in Chrome; Claude liệt kê được các tab đang mở và đọc được tin trên báo Lao động.
- [ ] Kết nối thành công Google Drive và Gmail; chạy được trợ lý phân loại hòm thư.
- [ ] **Sản phẩm 1:** 01 file báo cáo kinh doanh tháng dạng HTML, có nhận định và nút In / Lưu PDF.
- [ ] **Sản phẩm 2:** 01 web app Apps Script thêm, sửa, xóa danh mục, đơn hàng, khách hàng, có dashboard thống kê, dữ liệu lưu thẳng vào Google Sheets.
- [ ] Thêm thử 1 đơn hàng trên web app và thấy dòng mới xuất hiện trong Google Sheets.

---

### 4.2. Cầu nối sang Buổi 4: Cho Claude xuống làm việc trên máy tính

- **Thành tựu hôm nay:** Claude đọc thẳng dữ liệu trên Gmail, Google Drive, Google Sheets; anh chị có báo cáo tháng để gửi đi và web app quản lý bán hàng kết nối thẳng Google Sheets.
- **Bài toán mới:** nếu công ty có hàng trăm file Word, hợp đồng, bảng kê nằm trong ổ C, ổ D, không thể đưa hết lên Drive thì sao?
- **Buổi 4:** cho Claude làm việc trực tiếp với thư mục trên máy tính bằng **Claude Code Desktop**: tự mở từng file, đối chiếu số liệu, tạo file mới và sắp xếp thư mục ngăn nắp.
