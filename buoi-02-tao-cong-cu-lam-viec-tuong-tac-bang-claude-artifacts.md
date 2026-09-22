# Buổi 2: Tạo công cụ làm việc tương tác bằng Claude Artifacts

## Nhịp buổi

| Phần | Nội dung | Thời lượng dự kiến |
|:---:|---|:---:|
| **0** | Từ văn bản tĩnh sang công cụ tương tác: Sản phẩm hôm nay bạn mang về là gì? | 15 phút |
| **1** | Bản chất của Artifacts, Khởi động nhanh ngoài Chat & "Aha Moment" | 30 phút |
| **2** | Kỹ thuật "Prompt-to-App" & 2 Case Study Xây dựng công cụ thực chiến trong Project | 65 phút |
| **3** | Kỹ thuật tinh chỉnh (Iterate), Khắc phục lỗi (Debug) & Xuất bản chia sẻ link (Publish & Share) | 25 phút |
| **4** | Nghiệm thu cuối buổi & Định hướng Buổi 3 | 15 phút |


---

## PHẦN 0. TỪ VĂN BẢN TĨNH SANG CÔNG CỤ TƯƠNG TÁC

### 0.1. Điểm nghẽn sau Buổi 1
- Ở Buổi 1, chúng ta đã tạo được 2 Trợ lý chuyên việc trong Claude Projects (Báo giá B2B và Thẩm định hợp đồng).
- Kết quả nhận được rất xuất sắc, nhưng vẫn nằm ở dạng **văn bản tĩnh trong khung chat**.
- **Hạn chế trong công việc thực tế:**
  - Nếu muốn tính thử 5 phương án báo giá khác nhau cho khách (thử 30 người dùng, thử 45 người dùng, đổi từ trả 100% sang trả 3 đợt...), bạn phải gõ đi gõ lại 5 câu lệnh chat.
  - Bạn không thể gửi nguyên cả đoạn hội thoại dài ngoằng cho sếp hoặc đồng nghiệp xem được. Người khác muốn dùng cũng không biết phải bấm vào đâu.
  - Văn bản chữ thì khó hình dung trực quan bằng các nút bấm, thanh trượt, bảng tính tự động nhảy số và các khối màu cảnh báo.

### 0.2. Giải pháp: Claude Artifacts - Biến ý tưởng thành Mini Web App chạy ngay
- **Claude Artifacts** là tính năng độc quyền của Claude, cho phép mở ra một **"cửa sổ thứ hai"** bên cạnh khung chat.
- Thay vì chỉ trả về câu chữ, Claude sẽ tự động lập trình một **ứng dụng tương tác sống (Interactive App)** hoàn chỉnh:
  - Có các ô nhập liệu (Input), thanh kéo chọn số lượng (Slider), nút bấm chọn gói dịch vụ (Button).
  - Có logic tự động tính toán, đổi màu cảnh báo rủi ro thời gian thực.
  - Có nút bấm sao chép kết quả hoặc xuất dữ liệu để sử dụng ngay.
- **Điều kỳ diệu nhất:** Bạn **hoàn toàn không cần biết viết một dòng code nào**. Bạn chỉ cần đóng vai trò là "Người đặt đề bài", Claude sẽ vừa là kỹ sư lập trình vừa là nhà thiết kế giao diện cho bạn.
- **Sản phẩm cầm về hôm nay:** Ít nhất **01 Công cụ tương tác hoàn chỉnh** có thể mở trên trình duyệt của máy tính, điện thoại và **tạo link công khai gửi cho đồng nghiệp, khách hàng dùng độc lập**.

---

## PHẦN 1. BẢN CHẤT CỦA ARTIFACTS & CƠ CHẾ CỬA SỔ THỨ HAI

### 1.1. Khi nào Claude tự động bật cửa sổ Artifacts?

Claude sẽ tự động tách nội dung sang cửa sổ Artifacts bên phải khi nội dung đó thỏa mãn một trong các tiêu chí:
1. **Mã nguồn hoặc Ứng dụng độc lập:** Các ứng dụng tương tác HTML/Tailwind CSS/JavaScript, React Component hoặc SVG.
2. **Tài liệu có cấu trúc dài (> 15 dòng):** Tài liệu nghiệp vụ, bản đề xuất dự án, văn bản mẫu mà người dùng muốn lưu lại, chỉnh sửa riêng mà không bị trôi theo dòng chat.
3. **Biểu đồ & Sơ đồ quy trình trực quan:** Sơ đồ luồng công việc (Mermaid Chart), kiến trúc hệ thống, dòng thời gian dự án.

> [!TIP]
> **Quy tắc vàng phân biệt:**
> - **Cửa sổ Chat (Bên trái):** Nơi bạn và Claude đối thoại, bàn bạc, giao nhiệm vụ, góp ý sửa đổi.
> - **Cửa sổ Artifacts (Bên phải):** Nơi chứa "thành phẩm" cuối cùng. Thành phẩm này đứng độc lập, tương tác được, chỉnh sửa được và chia sẻ được.

---

### 1.2. Giải phẫu giao diện cửa sổ Artifacts

Khi Claude tạo một Artifact, góc trên bên phải màn hình sẽ xuất hiện một thanh công cụ với các nút quan trọng:
- **Tab Preview (Xem trước):** Hiển thị trực quan giao diện ứng dụng để bạn bấm thử, kéo trượt, nhập liệu y hệt như một website thực tế.
- **Tab Code (Mã nguồn):** Xem mã code mà Claude tự viết (dành cho người muốn copy code đưa vào hệ thống khác, người không chuyên có thể bỏ qua tab này).
- **Nút Copy (Sao chép):** Copy toàn bộ code hoặc nội dung của Artifact vào bộ nhớ tạm.
- **Nút Download (Tải về):** Tải file HTML/React về máy tính để mở offline khi không có internet.
- **Nút Version (Phiên bản - v1, v2, v3...):** Xem lại các phiên bản cũ trước đó khi bạn yêu cầu Claude chỉnh sửa. Bạn có thể quay về bất kỳ phiên bản nào nếu không ưng ý với bản mới.
- **Nút Publish / Share (Chia sẻ):** Xuất bản ứng dụng thành một đường link web công khai để gửi cho bất kỳ ai.

---

### 1.3. Bật tính năng Artifacts trong tài khoản (Kiểm tra điều kiện)

<details>
<summary><b>Thao tác thực hành: Kiểm tra tính năng Artifacts</b> (bấm để mở)</summary>

1. Mở trang chủ Claude ([claude.ai](https://claude.ai)).
2. Bấm vào ảnh đại diện / tên tài khoản của bạn ở góc dưới cùng bên trái màn hình -> Chọn **Settings**.
3. Bấm chọn mục **Capabilities** (hoặc kiểm tra trong mục **General / Feature Preview** tùy phiên bản tài khoản).
4. Đảm bảo mục **Artifacts** đang được gạt sang trạng thái **BẬT (ON)**.
*(Thông thường trên giao diện hiện tại của Claude, tính năng Artifacts đã được bật mặc định cho tất cả tài khoản).*
</details>

---

### 1.4. Khởi động nhanh (Warm-up): Tạo ngay công cụ đầu tiên trong 30 giây (ngoài màn hình Chat thường)

- **Mục tiêu:** Giúp bạn có ngay khoảnh khắc "Aha!" - tận mắt thấy cửa sổ Artifacts trượt ra, kéo thử các thanh trượt và hiểu cơ chế hoạt động mà không bị áp lực bởi các quy chế nghiệp vụ phức tạp.
- **Vị trí thực hiện:** Ra ngoài màn hình chính của Claude (Chat thông thường / Cowork), **chưa cần mở Project**.

#### 👉 Bài tập khởi động chính (Thực hành tại lớp): Bảng tính Lãi vay mua nhà / mua xe trả góp (Loan Calculator)
- Chỉ với một câu lệnh 5 dòng đơn giản, Claude sẽ dựng ngay một công cụ tài chính có 2 thanh trượt mượt mà.

<details>
<summary><b>Thao tác thực hành: Khởi động với Bảng tính Lãi vay trả góp</b> (bấm để mở)</summary>

1. Bấm vào nút **Start a new chat** (hoặc dấu `+` ở góc trên bên trái màn hình) để mở một phiên chat mới tinh ngoài màn hình chính.
2. Copy và dán câu lệnh ngắn sau vào ô chat:

```markdown
Hãy tạo một ứng dụng mini web app bằng Artifact như sau:
"BẢNG TÍNH LÃI VAY MUA NHÀ & XE TRẢ GÓP"
- Đầu vào:
  + Thanh trượt (Slider) chọn số tiền vay: từ 200 triệu đến 5 tỷ đồng (bước nhảy 50 triệu, mặc định 1 tỷ).
  + Thanh trượt chọn thời hạn vay: từ 1 năm đến 25 năm (mặc định 10 năm).
  + Ô nhập hoặc thanh trượt lãi suất: mặc định 8.5%/năm.
- Logic & Kết quả:
  + Tự động tính số tiền gốc hàng tháng = Tiền vay / (Số năm * 12).
  + Tự động tính số tiền lãi tháng đầu = Tiền vay * (Lãi suất / 12).
  + Hiển thị nổi bật: Tổng số tiền phải trả tháng đầu (Gốc + Lãi) với con số to, rõ ràng.
  + Hiển thị bảng tóm tắt: Tổng lãi phải trả trong suốt kỳ hạn và Tổng số tiền cả gốc lẫn lãi.
- Giao diện: Hiện đại, sạch sẽ, màu xanh tài chính (Emerald/Teal), số tiền định dạng chuẩn tiếng Việt (ví dụ: 1.000.000.000 đ).
```

3. Bấm **Gửi (Send)** và quan sát:
   - Trong vòng 30 giây, khung chat bên trái sẽ tự động nhường chỗ cho **cửa sổ Artifacts bên phải**.
   - Tab **Preview** hiển thị giao diện sống động: Thử kéo thanh trượt từ 1 tỷ lên 2 tỷ đồng -> Xem con số tiền trả hàng tháng nhảy lập tức theo thời gian thực!
   - Thử chuyển qua tab **Code** để xem Claude vừa tự viết hàng chục dòng mã lệnh cho bạn.
</details>

---

#### 🌟 2 Lựa chọn khởi động bổ sung (Học viên tự thử nghiệm thêm nếu muốn)

Nếu bạn muốn khám phá thêm các dạng giao diện khác (như danh sách tích chọn hoặc chia tiền theo nhóm), hãy thử copy 1 trong 2 lệnh dưới đây:

<details>
<summary><b>Lựa chọn bổ sung 1: Bảng tính chia tiền ăn trưa & Quỹ trà sữa văn phòng (Lunch & Coffee Splitter)</b> (bấm để mở)</summary>

```markdown
Hãy tạo một ứng dụng mini web app bằng Artifact như sau: "CÔNG CỤ CHIA TIỀN ĂN TRƯA VĂN PHÒNG"
- Cho nhập tổng hóa đơn bữa trưa (ô nhập số tiền).
- Thanh trượt chọn số người tham gia (từ 2 đến 15 người).
- Danh sách tùy chọn (Checkbox) cho các món gọi riêng:
  + "Có uống trà sữa / cà phê (+35.000 đ/ly)" -> Cho chọn số người uống.
  + "Có người ăn chay / giảm khẩu phần (-20.000 đ)" -> Cho chọn số người.
- Kết quả: Tự tính số tiền chính xác mỗi người cần chuyển khoản (chia nhóm: Người ăn thường chuyển bao nhiêu, Người có uống thêm nước chuyển bao nhiêu).
- Kèm nút bấm: "Sao chép thông báo chia tiền để gửi Zalo nhóm" (định dạng sẵn lời nhắn lịch sự, vui vẻ).
```
</details>

<details>
<summary><b>Lựa chọn bổ sung 2: Bảng phân loại việc cần làm theo Ma trận Eisenhower (Daily Focus Tracker)</b> (bấm để mở)</summary>

```markdown
Hãy tạo một ứng dụng mini web app bằng Artifact như sau: "MA TRẬN QUẢN LÝ CÔNG VIỆC TRONG NGÀY (EISENHOWER MATRIX)"
- Bố cục 4 ô trực quan:
  1. Khẩn cấp & Quan trọng (Làm ngay - Màu đỏ)
  2. Quan trọng nhưng Không khẩn cấp (Lên lịch làm - Màu xanh dương)
  3. Khẩn cấp nhưng Không quan trọng (Ủy quyền/Giao việc - Màu vàng)
  4. Không khẩn cấp & Không quan trọng (Loại bỏ - Màu xám)
- Mỗi ô cho phép gõ thêm đầu việc mới và có nút checkbox để tick khi hoàn thành.
- Phía trên cùng có một thanh tiến độ (Progress Bar) tự động cập nhật % công việc đã hoàn thành trong ngày.
- Giao diện phẳng tối giản, hiện đại, lưu trạng thái tạm thời trên trình duyệt.
```
</details>

---

### 1.5. Cầu nối tư duy: Khi nào làm ngoài Chat, khi nào phải vào Claude Projects?

- **Làm ngoài Chat thông thường:** Rất tuyệt vời cho các công cụ cá nhân, công cụ tính toán nhanh một lần (như tính tiền vay, chia bill ăn trưa, to-do list cá nhân).
- **Khi nào bắt buộc phải đưa vào Claude Projects?**
  - Khi bạn cần xây dựng **công cụ nghiệp vụ cho công ty** (như Bảng tính báo giá NovaTech hay Bảng kiểm tra hợp đồng).
  - Vì nếu làm ngoài Chat, mỗi lần bạn muốn đổi công cụ, bạn lại phải ngồi gõ lại 3 trang bảng giá PDF và 4 trang quy chế chiết khấu.
  - Còn khi làm trong **Claude Projects của Buổi 1**, toàn bộ dữ liệu nội bộ đã nằm sẵn trong mục `Context`. Bạn chỉ cần đặc tả chức năng, Claude sẽ tự động bốc toàn bộ bảng giá và quy định của công ty đưa vào ứng dụng mà không sai một dấu phẩy!

---

## PHẦN 2. KỸ THUẬT "PROMPT-TO-APP" & 2 CASE STUDY THỰC CHIẾN TRONG PROJECT


### 2.1. Công thức 4 thành tố "Prompt-to-App" cho người không biết lập trình

Để Claude tạo ra một công cụ tương tác đúng ý 100% ngay từ lần đầu tiên mà không bị ngô nghê hay lỗi hiển thị, bạn cần cung cấp đủ **4 thành tố (I - L - O - U)**:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        CÔNG THỨC PROMPT-TO-APP                         │
│                                                                        │
│   1. INPUT (Đầu vào)      : Người dùng sẽ nhập hoặc chọn những gì?     │
│   2. LOGIC (Quy tắc tính) : Công thức, điều kiện, bậc thang thế nào?   │
│   3. OUTPUT (Kết quả)     : Màn hình hiển thị những số liệu/văn bản gì?│
│   4. UX/UI (Giao diện)    : Màu sắc, phong cách, nút bấm, tiện ích gì? │
└────────────────────────────────────────────────────────────────────────┘
```

1. **Input (Đầu vào):** Nêu rõ những gì bạn muốn người dùng thao tác (ô nhập tên khách, thanh trượt số người, nút chọn gói dịch vụ, nút chọn trả góp...).
2. **Logic (Quy tắc tính toán & Thẩm quyền):** Bảo Claude tự đọc các công thức, bậc thang chiết khấu, phụ phí và thẩm quyền phê duyệt từ các file trong Context.
3. **Output (Đầu ra hiển thị):** Kết quả hiển thị gồm bảng chiết tính tiền, các thẻ đổi màu cảnh báo thẩm quyền (Xanh/Vàng/Đỏ), và văn bản mẫu điền sẵn số liệu.
4. **UX/UI (Trải nghiệm người dùng):** Yêu cầu giao diện hiện đại, bố cục 2 cột rõ ràng, có nút bấm sao chép một chạm.

> [!IMPORTANT]
> **Bí quyết vàng của người làm chủ AI (Không làm thay việc của AI):**
> Bạn **KHÔNG CẦN VÀ KHÔNG NÊN** ngồi chép lại từng mức giá, từng bậc chiết khấu hay từng điều luật vào câu lệnh prompt! 
> Đó là cách làm của người chưa biết dùng Projects. Với Claude Projects, bạn chỉ cần ra lệnh: *"Đọc từ file Bảng giá và Quy chế chiết khấu trong Context của dự án này..."*. Claude sẽ tự động bốc toàn bộ dữ liệu nội bộ ra để lập trình ứng dụng cho bạn!

---

### 2.2. Case Study 1: Bảng tính chiết khấu & Soạn Thư chào giá B2B Tương tác (NovaTech Deal Desk)

#### Vấn đề bài toán
Đội ngũ Sales B2B của công ty NovaTech thường xuyên phải tính giá cho khách hàng với nhiều biến số phức tạp:
- Chọn gói phần mềm, số người dùng thực tế, đăng ký thêm gói đào tạo tại văn phòng.
- Áp dụng bậc chiết khấu doanh số, ưu đãi trả 100% hoặc phụ thu trả 3 đợt.
- Kiểm soát thẩm quyền duyệt giá (Sales tự quyết / Cần Trưởng phòng / Bắt buộc CEO phê duyệt).
- Xuất Thư chào giá hoàn chỉnh gửi khách ngay lập tức.

#### Thao tác tạo ứng dụng Báo giá tương tác

<details>
<summary><b>Thao tác thực hành: Tạo Bảng tính Báo giá tương tác bằng Artifacts</b> (bấm để mở)</summary>

**Bước 1: Mở lại Project đã tạo ở Buổi 1**
- Vào mục **Projects** ở menu bên trái -> Bấm chọn Project **"Trợ lý Báo giá & Thương mại B2B - NovaTech"** (đã có sẵn 3 file: Bảng giá PDF, Quy chế chiết khấu Word, Mẫu thư chào giá Word trong Context).
- Bấm mở một phiên chat mới bên trong Project này.

**Bước 2: Copy và dán câu lệnh yêu cầu tự nhiên vào ô chat**
*(Hãy chú ý: Câu lệnh ngắn gọn, tự nhiên như giao việc cho nhân viên, để Claude tự đọc 3 file tài liệu trong Context chứ không cần bạn gõ lại giá tiền!)*

```markdown
Dựa vào các file tài liệu trong mục Context của dự án này (Bảng giá, Quy chế chiết khấu, Mẫu thư chào giá):
Hãy tạo cho tôi một ỨNG DỤNG WEB TƯƠNG TÁC bằng Artifact để nhân viên kinh doanh NovaTech tính giá và duyệt deal B2B với khách hàng:

1. ĐẦU VÀO (Cho Sales thao tác):
- Tự động đọc từ file Bảng giá để tạo danh sách các gói phần mềm cho Sales bấm chọn, và tùy chọn dịch vụ đào tạo tại văn phòng đi kèm.
- Có ô nhập tên khách hàng / công ty, và thanh trượt chọn số lượng người dùng thực tế.
- Chọn phương thức thanh toán: Trả 100% (hưởng ưu đãi thanh toán sớm) hoặc Chia 3 đợt (phụ thu phí dòng tiền) theo đúng quy chế công ty.
- Thanh trượt cho Sales đề xuất mức giảm giá thêm (từ 0% đến 15%).

2. LOGIC TÍNH TOÁN & CẢNH BÁO THẨM QUYỀN (Tự động theo Quy chế chiết khấu):
- Tự động áp đúng tỷ lệ chiết khấu theo bậc doanh số từ file Quy chế chiết khấu trong Context.
- Tính chính xác thuế VAT 10% và tổng tiền thanh toán cuối cùng.
- RẤT QUAN TRỌNG: Tự động đổi màu thẻ cảnh báo thẩm quyền duyệt deal theo đúng quy chế công ty:
  + Mức giảm giá nằm trong hạn mức Sales được tự quyết -> Thẻ màu xanh lá.
  + Vượt hạn mức Sales nhưng trong quyền hạn Trưởng phòng -> Thẻ màu vàng cam cảnh báo cần Trưởng phòng duyệt.
  + Vượt thẩm quyền Trưởng phòng -> Đổi sang màu đỏ cảnh báo bắt buộc Tổng Giám đốc CEO ký duyệt.

3. XUẤT BẢN THƯ CHÀO GIÁ (Bên phải màn hình):
- Tự động điền thông tin và bảng chiết tính vào bản xem trước Thư chào giá chuẩn theo đúng file Mẫu thư trong Context (nhớ lấy đúng thông tin tài khoản ngân hàng của NovaTech).
- Có nút bấm "Sao chép toàn bộ Thư chào giá" để Sales copy gửi khách ngay.

Giao diện thiết kế phong cách doanh nghiệp hiện đại, trực quan, chia 2 cột rõ ràng, dễ dùng cho dân kinh doanh nhé!
```

**Bước 3: Trải nghiệm ứng dụng tại Tab Preview**
1. Quan sát cửa sổ bên phải mở ra: Claude sẽ tự đọc 3 file trong Context và hiển thị đầy đủ tên các gói Starter, Professional, Enterprise, kèm đơn giá niêm yết mà bạn không hề phải gõ vào prompt!
2. Thử kéo thanh trượt số người dùng từ 15 lên 45 người.
3. Thử đổi phương thức từ "Thanh toán 100%" sang "Chia 3 đợt" -> Xem số tiền phụ thu tự động nhảy.
4. Thử kéo thanh giảm giá thêm lên 10% -> Xem thẻ cảnh báo thẩm quyền lập tức đổi sang màu đỏ kèm thông báo *"VƯỢT THẨM QUYỀN - Bắt buộc CEO duyệt"*.
5. Bấm nút **"Sao chép toàn bộ Thư chào giá"** và dán thử vào Zalo / Word xem số tài khoản Vietcombank và bảng giá có được điền tự động chính xác không.

**Bước 4 (Nâng cấp tương tác - gõ tiếp trong cùng phiên chat, không tạo app mới):**
Sau khi ứng dụng đã chạy, gửi tiếp 2 câu lệnh dưới để nâng cấp Thư chào giá thành phiếu điện tử có mã VietQR + con dấu và xuất ảnh/file gửi khách.

*Câu lệnh nâng cấp 1 - Phiếu báo giá điện tử + VietQR + xuất ảnh PNG:*

```markdown
Ở phần Thư chào giá bên phải, hãy thiết kế lại thành một "PHIẾU BÁO GIÁ & HỢP ĐỒNG ĐIỆN TỬ" dạng thẻ card đẹp và thêm tính năng XUẤT ẢNH PNG:

THIẾT KẾ PHIẾU BÁO GIÁ (Định dạng như một hóa đơn điện tử cao cấp):
Có tên Công ty NovaTech
Bảng chiết tính rõ ràng: Gói cước, số người dùng, chiết khấu, phụ thu và TỔNG TIỀN THANH TOÁN (in số to, nổi bật).
TỰ ĐỘNG CHÈN MÃ VIETQR: Nhúng mã QR thanh toán động từ VietQR (Ngân hàng: Vietcombank, STK: 0071001234567, số tiền tự động cập nhật theo Tổng thanh toán).
Có đóng một con dấu mộc tròn điện tử màu đỏ: "NOVATECH - ĐÃ PHÊ DUYỆT DEAL".
TÍNH NĂNG XUẤT ẢNH:
Thêm nút bấm nổi bật: "Tải ảnh Báo giá (PNG gửi Zalo)" và nút "Sao chép ảnh vào Clipboard".
Khi bấm "Tải ảnh PNG", chụp lại toàn bộ phiếu báo giá đó và tự động tải file ảnh sắc nét về máy tính.
Hãy cập nhật lại Artifact này cho tôi nhé!
```

*Câu lệnh nâng cấp 2 - Xuất Artifact thành file HTML tải về máy:*

```markdown
xuất artifact này thành file html cho tôi tải xuống nhé
```
</details>

---

### 2.3. Case Study 2: Bảng điều khiển Rà soát Hợp đồng & Chấm điểm Rủi ro Pháp lý (Legal Audit Dashboard)

#### Vấn đề bài toán
Chuyên viên kinh doanh hoặc quản lý khi nhận một bản hợp đồng dịch vụ dài từ đối tác thường rất ngại đọc từng trang chữ li ti. Cần một công cụ trực quan:
- Cho phép dán nhanh các điều khoản nghi vấn vào rà soát.
- Có sẵn danh mục các điều khoản rủi ro điển hình trong ngành (Phạt vi phạm, Bảo mật dữ liệu, Quyền sở hữu trí tuệ, Thẩm quyền giải quyết tranh chấp).
- Tự động chấm điểm mức độ rủi ro (Risk Score: Thấp / Trung bình / Nguy hiểm).
- Đối chiếu tự động với Luật Thương mại, Luật Sở hữu trí tuệ và Luật Bảo vệ dữ liệu cá nhân Việt Nam.
- Sinh sẵn câu chữ đề xuất viết lại (Redline/Markup) và có nút bấm Copy từng điều khoản để dán vào email đàm phán lại.

#### Thao tác tạo Bảng điều khiển Pháp lý tương tác

<details>
<summary><b>Thao tác thực hành: Tạo Bảng điều khiển Pháp lý tương tác</b> (bấm để mở)</summary>

**Bước 1: Mở lại Project Pháp chế đã tạo ở Buổi 1**
- Vào mục **Projects** ở menu bên trái -> Chọn Project **"Trợ lý Rà soát Hợp đồng & Pháp chế Doanh nghiệp - NovaTech"** (đã có sẵn file `Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp - NovaTech.pdf` trong Context).
- Mở một phiên chat mới bên trong Project.

**Bước 2: Copy và dán câu lệnh yêu cầu tự nhiên vào ô chat**
*(Tương tự Case Study 1, bạn chỉ nêu đề bài, Claude sẽ tự đọc Bộ tiêu chuẩn pháp lý để trích xuất các điều khoản, căn cứ luật Việt Nam và câu chữ redline!)*

```markdown
Dựa vào tài liệu "Bộ tiêu chuẩn rà soát pháp lý" và "Hợp đồng dịch vụ mẫu" trong mục Context của dự án:
Hãy tạo cho tôi một BẢNG ĐIỀU KHIỂN RÀ SOÁT RỦI RO HỢP ĐỒNG TƯƠNG TÁC (Legal Risk Dashboard) bằng Artifact:

1. TỔNG QUAN & ĐO LƯỜNG RỦI RO:
- Có đồng hồ đo điểm rủi ro tổng thể (Risk Scorecard từ 0 - 100) và các thẻ thống kê nhanh số lượng điều khoản (An toàn / Cần đàm phán / Nguy cơ cao).

2. DANH MỤC CÁC ĐIỀU KHOẢN RỦI RO CẦN RÀ SOÁT:
- Tự động đọc từ file Bộ tiêu chuẩn pháp lý của công ty để trích xuất sẵn 4 điều khoản rủi ro kinh điển nhất làm dữ liệu mẫu (nhất là điều khoản phạt vi phạm, quyền sở hữu trí tuệ/mã nguồn, đơn phương chấm dứt và thẩm quyền tài phán).
- Mỗi điều khoản trình bày dạng thẻ bấm mở rộng (Accordion) xem chi tiết:
  + Nêu rõ câu chữ đối tác hay gài bẫy (tô đỏ các cụm từ bất lợi).
  + Căn cứ theo đúng điều luật của Việt Nam và quy chuẩn công ty trong Context để giải thích rõ lý do vì sao nguy hiểm.
  + Viết sẵn câu chữ đề xuất sửa đổi (redline) chuẩn mực, giữ văn phong thiện chí hợp tác.
  + Có nút bấm "Sao chép câu chữ Redline" để chuyên viên copy gửi đi đàm phán lại.

3. TƯƠNG TÁC THỰC TẾ:
- Có một ô nhập liệu để tôi có thể dán thử một điều khoản hợp đồng mới bất kỳ vào và nút "Quét nhanh rủi ro".
- Nút "Sao chép bảng tổng hợp rủi ro" để gửi báo cáo nhanh cho sếp qua email.

Giao diện phong cách Legal Tech hiện đại, màu sắc trang nhã, trực quan, chuyên nghiệp nhé!
```

**Bước 3: Trải nghiệm và thử nghiệm công cụ**
1. Quan sát Claude tự đọc file trong Context và hiển thị ngay 4 điều khoản rủi ro kèm căn cứ chính xác Điều 301 Luật Thương mại (phạt trần 8%) mà bạn không phải gõ một dòng luật nào!
2. Bấm mở rộng từng thẻ điều khoản để xem câu chữ gài bẫy và phần đề xuất viết lại.
3. Bấm thử nút "Sao chép câu chữ Redline" để kiểm tra tính tiện lợi khi đi đàm phán hợp đồng.
4. Thử dán một đoạn điều khoản thực tế từ công việc của bạn vào ô nhập liệu để kiểm tra tính năng quét rủi ro.

**Bước 4 (Nâng cấp tương tác - gõ tiếp trong cùng phiên chat, không tạo app mới):**
Sau khi bảng điều khiển đã chạy, gửi tiếp 2 câu lệnh dưới để gói kết quả rà soát thành một phiếu thẩm định có con dấu và xuất ảnh/file gửi sếp, đối tác.

*Câu lệnh nâng cấp 1 - Phiếu thẩm định rủi ro pháp lý + xuất ảnh PNG:*

```markdown
Ở phần bảng tổng hợp rủi ro bên phải, hãy thiết kế lại thành một "PHIẾU KẾT QUẢ THẨM ĐỊNH RỦI RO PHÁP LÝ" dạng thẻ card đẹp và thêm tính năng XUẤT ẢNH PNG:

THIẾT KẾ PHIẾU THẨM ĐỊNH (Định dạng như một biên bản pháp chế cao cấp):
Có tên Công ty NovaTech - Phòng Pháp chế.
Bảng tổng hợp rõ ràng: Điểm rủi ro tổng thể (thang 0-100, in số to nổi bật), số lượng điều khoản theo từng mức (An toàn / Cần đàm phán / Nguy cơ cao) và danh sách các điều khoản nguy hiểm nhất kèm đề xuất xử lý.
Có đóng một con dấu mộc tròn điện tử màu đỏ: "NOVATECH - ĐÃ RÀ SOÁT PHÁP CHẾ".
Ghi rõ ngày rà soát và dòng "Người thẩm định: Phòng Pháp chế NovaTech".
TÍNH NĂNG XUẤT ẢNH:
Thêm nút bấm nổi bật: "Tải ảnh Phiếu thẩm định (PNG gửi Zalo)" và nút "Sao chép ảnh vào Clipboard".
Khi bấm "Tải ảnh PNG", chụp lại toàn bộ phiếu thẩm định đó và tự động tải file ảnh sắc nét về máy tính.
Hãy cập nhật lại Artifact này cho tôi nhé!
```

*Câu lệnh nâng cấp 2 - Xuất Artifact thành file HTML tải về máy:*

```markdown
xuất artifact này thành file html cho tôi tải xuống nhé
```
</details>

---

## PHẦN 3. KỸ THUẬT TINH CHỈNH, SỬA LỖI & CHIA SẺ LINK (PUBLISH & SHARE)

### 3.1. Kỹ thuật "Chỉ điểm" để tinh chỉnh giao diện (Không đụng vào code)

Sau khi Claude tạo xong ứng dụng lần đầu, chắc chắn bạn sẽ muốn điều chỉnh: đổi màu sắc, thêm một nút bấm, đổi vị trí các khối, hoặc sửa lại một công thức tính.

> [!IMPORTANT]
> **Nguyên tắc đối thoại khi chỉnh sửa Artifact:**
> Bạn **không cần** và **không nên** mở tab Code ra sửa tay nếu bạn không rành lập trình. 
> Hãy đứng ở khung chat bên trái, dùng ngôn ngữ mô tả vị trí trực quan theo công thức:
> **[Vị trí màn hình] + [Hiện trạng] + [Yêu cầu thay đổi cụ thể]**.

#### Các mẫu câu tinh chỉnh kinh điển:
- **Thêm tính năng:** *"Ở phần kết quả chiết tính, hãy bổ sung thêm một nút bấm 'In Thư chào giá (Print/PDF)' để khi bấm vào sẽ mở hộp thoại in tài liệu của trình duyệt."*
- **Sửa giao diện/màu sắc:** *"Bảng cảnh báo thẩm quyền màu đỏ hiện tại hơi gắt, hãy chuyển sang viền đỏ nhạt, nền kem trang nhã và làm nút bấm 'Sao chép' to hơn một chút ở chính giữa màn hình."*
- **Thêm trường dữ liệu:** *"Ở cột nhập liệu bên trái, hãy thêm một ô chọn (Dropdown) cho phép chọn thời hạn hợp đồng: 1 năm (giá chuẩn), 2 năm (giảm thêm 10%), 3 năm (giảm thêm 15%). Khi người dùng chọn thì tự động áp dụng vào bảng tính."*

---

### 3.2. Khắc phục sự cố thường gặp khi dùng Artifacts (Troubleshooting & Debug)

| Tình huống sự cố | Nguyên nhân | Cách khắc phục nhanh |
|---|---|---|
| **Màn hình Preview trắng tinh (Blank screen)** | Lỗi cú pháp JavaScript hoặc tài viện ngoài tải chậm | Gõ vào ô chat: *"Màn hình Preview đang bị trắng, hãy kiểm tra lại toàn bộ mã nguồn JavaScript để đảm bảo các thẻ đóng mở đầy đủ và không dùng thư viện ngoài bị chặn."* |
| **Bấm nút tính tiền nhưng số không nhảy** | Sự kiện click chuột (event listener) chưa liên kết với biến | Gõ vào chat: *"Khi tôi đổi số lượng trên thanh trượt, các ô tổng tiền bên phải chưa tự động cập nhật số liệu. Hãy viết lại hàm tính toán tự động cập nhật mỗi khi có thay đổi (onInput / onChange)."* |
| **Claude không tạo Artifact mà in code vào khung chat** | Lệnh prompt chưa đủ rõ ràng về loại định dạng đầu ra | Gõ vào chat: *"Hãy đóng gói toàn bộ ứng dụng trên vào MỘT CỬA SỔ ARTIFACT DUY NHẤT để tôi có thể xem trước (Preview) và sử dụng ngay lập tức."* |
| **Giao diện vỡ khi mở trên điện thoại** | Chưa tối ưu bố cục Responsive | Gõ vào chat: *"Hãy tối ưu lại giao diện này cho màn hình di động: trên màn hình nhỏ thì chuyển thành bố cục 1 cột dọc (nhập liệu ở trên, kết quả ở dưới)."* |

---

### 3.3. Xuất bản & Chia sẻ ứng dụng cho đồng nghiệp dùng độc lập (Publish & Share)

Đây là tính năng giá trị nhất của Artifacts: Biến sản phẩm bạn vừa tạo thành một **công cụ dùng chung cho cả phòng ban hoặc gửi trực tiếp cho khách hàng**.

```
┌────────────────────────────────────────────────────────────────────────┐
│                        QUY TRÌNH CHIA SẺ ARTIFACT                      │
│                                                                        │
│   [Nút Publish góc phải] ──> [Chọn Publish to Web] ──> [Copy Link]     │
│                                                             │          │
│                                                             ▼          │
│                                                Gửi qua Zalo, Slack,    │
│                                                Email cho đồng nghiệp   │
│                                                (Người nhận mở dùng     │
│                                                 ngay, không cần tài    │
│                                                 khoản Claude)          │
└────────────────────────────────────────────────────────────────────────┘
```

<details>
<summary><b>Thao tác thực hành: Xuất bản và lấy link chia sẻ công cụ</b> (bấm để mở)</summary>

1. Nhìn lên thanh tiêu đề của cửa sổ Artifact (góc trên bên phải).
2. Tìm nút **Publish** (hoặc biểu tượng chia sẻ / ba dấu chấm tùy phiên bản).
3. Một bảng thông báo hiện ra xác nhận việc xuất bản ứng dụng. Bấm chọn **Publish to Web** (Xuất bản lên web).
4. Hệ thống sẽ sinh ra một đường dẫn công khai (Public URL, ví dụ: `https://claude.site/artifacts/...`).
5. Bấm nút **Copy Link** (Sao chép đường liên kết).
6. **Thử nghiệm thực tế:**
   - Mở một tab trình duyệt ẩn danh (Incognito / Private Window) và dán link vào.
   - Hoặc gửi đường link đó qua Zalo cho một người bạn / đồng nghiệp trong lớp và nhờ họ mở trên điện thoại thử kéo thanh trượt tính giá.
   - Người nhận **không cần đăng nhập, không cần có tài khoản Claude** vẫn sử dụng được công cụ tính giá của bạn một cách mượt mà!
</details>

> [!NOTE]
> **Tính năng Remix (Dành cho người nhận):**
> Khi người nhận mở link ứng dụng của bạn, nếu họ có tài khoản Claude, họ có thể bấm nút **"Remix"** ở góc màn hình để sao chép công cụ đó về tài khoản của họ và tiếp tục tùy biến thêm theo ý họ mà không làm thay đổi bản gốc của bạn.

---

## PHẦN 4. BÀI TẬP TẠI LỚP, NGHIỆM THU & BƯỚC CHUẨN BỊ BUỔI 3

### 4.1. Bài tập thực hành tại lớp (30 phút tự do sáng tạo)

Chọn **1 trong 2 đề bài** sau để tự tay tạo ra công cụ phục vụ cho công việc:
- **Ưu tiên 1:** Làm trên chính tài liệu, bảng tính hoặc quy chế thực tế của công ty bạn.
- **Nếu chưa có sẵn tài liệu riêng:** Sử dụng ngay **2 file demo được chuẩn bị sẵn** của công ty NovaTech trong thư mục `demo-files/buoi-02/`.

---

#### 🌟 Đề bài A (Khối Bán hàng / Marketing / Chăm sóc khách hàng):
**Mục tiêu:** Xây dựng **"Bộ công cụ Chấm điểm & Phân loại Khách hàng Tiềm năng B2B (Lead Scoring App)"**.

<details>
<summary><b>Hướng dẫn thực hành Đề bài A với File Excel mẫu</b> (bấm để mở)</summary>

1. **Lấy file demo:** Mở thư mục `demo-files/buoi-02/` trên máy tính, lấy file:
   - `Ma trận chấm điểm Lead tiềm năng và Kịch bản chốt deal - NovaTech.xlsx`
2. **Nạp file vào Claude:** Bạn có thể nạp vào Project Buổi 1 hoặc đính kèm trực tiếp vào ô chat.
3. **Copy và dán câu lệnh tự nhiên sau:**

```markdown
Dựa vào file Excel "Ma trận chấm điểm Lead tiềm năng và Kịch bản chốt deal" tôi vừa nạp:
Hãy tạo cho tôi một BẢNG TÍNH CHẤM ĐIỂM VÀ PHÂN LOẠI KHÁCH HÀNG B2B TƯƠNG TÁC (Lead Scoring App) bằng Artifact:

- Đọc từ Sheet "Barem_Cham_Diem" để tạo các nhóm tiêu chí cho Sales bấm chọn: Quy mô doanh nghiệp, Vị trí người liên hệ, Ngân sách dự kiến và Mức độ cấp thiết.
- Tự động cộng tổng điểm và đối chiếu với Sheet "Quy_Tac_Phan_Loai" để:
  + Đổi màu thẻ xếp hạng trực quan: Đỏ (Lead Nóng - 150-200đ) | Vàng (Lead Ấm - 100-149đ) | Xám (Lead Lạnh - Dưới 100đ).
  + Hiển thị thời hạn cam kết phản hồi (SLA) và kịch bản hành động chi tiết tương ứng.
- Có nút bấm "Sao chép tóm tắt đánh giá Lead" để Sales dán nhanh vào CRM hoặc gửi Zalo nhóm cho Trưởng phòng.

Giao diện thiết kế trực quan, chia 2 cột hiện đại, dễ thao tác nhé!
```

4. **Trải nghiệm:** Thử bấm chọn các tiêu chí xem điểm số tự nhảy và thẻ trạng thái tự động đổi màu Đỏ/Vàng/Xám theo đúng quy tắc trong file Excel!
</details>

---

#### 🌟 Đề bài B (Khối Nhân sự / Vận hành / Quản trị nội bộ):
**Mục tiêu:** Xây dựng **"Bảng theo dõi Hội nhập & Đánh giá Thử việc 30 ngày (Interactive Onboarding Tracker)"**.

<details>
<summary><b>Hướng dẫn thực hành Đề bài B với File Word mẫu</b> (bấm để mở)</summary>

1. **Lấy file demo:** Mở thư mục `demo-files/buoi-02/` trên máy tính, lấy file:
   - `Quy trình tiếp nhận và kế hoạch thử việc 30 ngày cho nhân sự mới - NovaTech.docx`
2. **Nạp file vào Claude:** Đính kèm file Word này vào ô chat hoặc Project của bạn.
3. **Copy và dán câu lệnh tự nhiên sau:**

```markdown
Dựa vào file Word "Quy trình tiếp nhận và kế hoạch thử việc 30 ngày cho nhân sự mới" tôi vừa nạp:
Hãy tạo cho tôi một BẢNG THEO DÕI HỘI NHẬP VÀ ĐÁNH GIÁ THỬ VIỆC TƯƠNG TÁC (Interactive Onboarding Tracker) bằng Artifact:

- Đọc từ tài liệu để chia lộ trình 30 ngày thành 4 giai đoạn theo tuần (Tuần 1: Chào sân, Tuần 2: Học nghề, Tuần 3: Thử lửa, Tuần 4: Về đích).
- Mỗi tuần hiển thị danh sách các đầu việc có checkbox để tick chọn khi hoàn thành, ghi rõ người phụ trách và tiêu chuẩn nghiệm thu.
- Phía trên cùng có thanh tiến độ (Progress Bar %) tự động cập nhật khi người dùng tích chọn xong từng việc.
- Có khối chấm điểm nghiệm thu 30 ngày (thang 100 điểm theo 3 tiêu chí trong tài liệu) và nút "Sao chép Báo cáo thử việc gửi HR".

Giao diện phong cách quản trị nhân sự hiện đại, thanh lịch, trực quan nhé!
```

4. **Trải nghiệm:** Thử tích chọn các đầu việc của Tuần 1 và Tuần 2 $\rightarrow$ Xem thanh tiến độ % tự động nhảy từ 0% lên 30%, 50% cực kỳ trực quan!
</details>

---

### 4.2. Nghiệm thu buổi 2: Danh mục kiểm tra thành phẩm

Hãy tự kiểm tra lại sản phẩm của bạn trước khi đóng máy:

#### Về kỹ năng thao tác:
- [ ] Phân biệt rõ sự khác nhau giữa nội dung trong khung Chat và nội dung trong cửa sổ Artifacts.
- [ ] Tự tay tạo được công cụ khởi động nhanh ngoài Chat thường (Bảng tính lãi vay mua nhà/xe hoặc Chia tiền ăn trưa).
- [ ] Nắm vững công thức 4 thành tố **Prompt-to-App (I - L - O - U)** để đặc tả công cụ cho AI.
- [ ] Biết cách xem trước tại tab **Preview**, chuyển qua tab **Code** và sử dụng lịch sử phiên bản (**Versions**).
- [ ] Biết cách dùng ngôn ngữ nói thông thường để yêu cầu Claude tinh chỉnh giao diện hoặc bổ sung tính năng mà không cần biết lập trình.
- [ ] Nắm được cách xử lý khi gặp lỗi trắng màn hình hoặc nút bấm không ăn.
- [ ] Xuất bản thành công ít nhất **01 đường link Public Artifact** và gửi mở thử nghiệm trên điện thoại hoặc tab ẩn danh.

#### Về sản phẩm số mang về:
- [ ] **Sản phẩm Khởi động:** 01 Ứng dụng mini cá nhân (Tính lãi vay / Chia bill / Ma trận công việc).
- [ ] **Sản phẩm 1:** Bản tính Báo giá & Phê duyệt Deal B2B tương tác (hoặc công cụ tính giá ngành của bạn).
- [ ] **Sản phẩm 2:** Bảng điều khiển rà soát rủi ro pháp lý & Redline (hoặc công cụ nghiệp vụ tự chọn).
- [ ] Đường link web độc lập sẵn sàng gửi cho sếp hoặc đồng nghiệp trải nghiệm ngay trong sáng mai.

---

### 4.3. Cầu nối sang Buổi 3: Kết nối dữ liệu thật (Connectors)

- **Thành tựu hôm nay:** Bạn đã có thể tự tạo ra bất kỳ phần mềm mini hay công cụ tương tác nào chỉ bằng vài câu lệnh tiếng Việt.
- **Giới hạn cần vượt qua:** Các công cụ này hiện vẫn đang nhận dữ liệu do bạn gõ vào tay từng lần.
- **Buổi 3 chúng ta sẽ làm gì?**
  - Chúng ta sẽ **phá vỡ thao tác copy-paste thủ công**.
  - Kết nối Claude trực tiếp với **Google Drive, Google Sheets và Gmail** của bạn.
  - Claude sẽ tự đọc các file báo cáo, đơn hàng thực tế trên Drive/Sheets, đối chiếu số liệu và tự động điền vào báo cáo mà bạn không cần mở từng file ra chép tay!
