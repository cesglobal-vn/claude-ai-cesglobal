# Buổi 2: Tạo công cụ làm việc tương tác bằng Claude Artifacts

## Nhịp buổi

| Phần | Nội dung | Thời lượng dự kiến |
|:---:|---|:---:|
| **0** | Từ văn bản tĩnh sang công cụ tương tác: Sản phẩm hôm nay bạn mang về là gì? | 15 phút |
| **1** | Bản chất của Claude Artifacts & Cơ chế hoạt động của "Cửa sổ thứ hai" | 25 phút |
| **2** | Kỹ thuật "Prompt-to-App" & 2 Case Study Xây dựng công cụ thực chiến | 70 phút |
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

## PHẦN 2. KỸ THUẬT "PROMPT-TO-APP" & 2 CASE STUDY THỰC CHIẾN

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

1. **Input (Đầu vào):** Quy định rõ người dùng tương tác bằng gì (ô nhập số, thanh trượt slider, menu thả xuống dropdown, hay nút chọn radio).
2. **Logic (Quy tắc tính toán):** Nêu rõ các bước tính, công thức chiết khấu, điều kiện if/else (Ví dụ: Nếu trên 50 người thì giảm 8%, nếu trả chậm thì cộng thêm 4%).
3. **Output (Đầu ra hiển thị):** Kết quả hiển thị gồm số tiền, bảng tóm tắt, màu cảnh báo trạng thái phê duyệt (Xanh/Vàng/Đỏ), và văn bản hoàn chỉnh.
4. **UX/UI (Trải nghiệm người dùng):** Yêu cầu giao diện hiện đại, sạch sẽ, chuẩn doanh nghiệp (corporate), thân thiện với cả máy tính và điện thoại di động, có nút "Sao chép một chạm" (Copy to clipboard).

---

### 2.2. Case Study 1: Bảng tính chiết khấu & Soạn Thư chào giá B2B Tương tác (NovaTech Deal Desk)

#### Vấn đề bài toán
Đội ngũ Sales B2B của công ty NovaTech thường xuyên phải tính giá cho khách hàng với nhiều biến số phức tạp:
- Chọn gói phần mềm (Starter, Professional, Enterprise).
- Chọn số lượng người dùng (tính thêm phí nếu vượt định mức gói).
- Đăng ký thêm dịch vụ đào tạo tại văn phòng (15 triệu/3 buổi).
- Áp dụng bậc chiết khấu doanh số theo quy chế công ty (0% - 12%).
- Ưu đãi thanh toán 100% (giảm 5%) hoặc phụ thu nếu trả 3 đợt (+4%).
- Hiển thị cảnh báo cấp thẩm quyền duyệt giá (Sales tự quyết / Cần Trưởng phòng / Bắt buộc CEO phê duyệt).
- Tự động xuất Thư chào giá hoàn chỉnh kèm số tài khoản ngân hàng để gửi khách ngay lập tức.

#### Thao tác tạo ứng dụng Báo giá tương tác

<details>
<summary><b>Thao tác thực hành: Tạo Bảng tính Báo giá tương tác bằng Artifacts</b> (bấm để mở)</summary>

**Bước 1: Mở Project hoặc mở một phiên Chat mới**
- Bạn có thể vào lại Project **"Trợ lý Báo giá & Thương mại B2B - NovaTech"** đã tạo ở Buổi 1 (đã có sẵn 3 file tài liệu trong Context).
- Hoặc mở trực tiếp một phiên chat mới trên Claude nếu muốn xây dựng ứng dụng độc lập.

**Bước 2: Copy và dán câu lệnh "Prompt-to-App" chuẩn vào ô chat**

```markdown
Hãy đóng vai trò là một Chuyên gia Lập trình Web Frontend và Chuyên gia Tối ưu Vận hành B2B. 
Dựa vào các tài liệu nội bộ của NovaTech (hoặc các quy tắc nghiệp vụ tôi cung cấp dưới đây), hãy xây dựng một ỨNG DỤNG WEB TƯƠNG TÁC ĐỘC LẬP (Interactive Single-Page Web App) bằng HTML, Tailwind CSS và JavaScript hiện đại, chạy trực tiếp trong cửa sổ Artifact.

Ứng dụng mang tên: "BẢNG TÍNH BÁO GIÁ & PHÊ DUYỆT DEAL B2B - NOVATECH"

CÁC YÊU CẦU CHI TIẾT VỀ CHỨC NĂNG & GIAO DIỆN:

1. KHỐI ĐẦU VÀO (INPUT CONTROLS):
- Tên khách hàng & Doanh nghiệp: Ô nhập văn bản.
- Lựa chọn Gói giải pháp phần mềm (Radio Card hoặc Dropdown đẹp mắt):
  + Gói Starter: 18.000.000 đ/năm (Tối đa 15 người dùng).
  + Gói Professional: 36.000.000 đ/năm (Tối đa 50 người dùng).
  + Gói Enterprise: 72.000.000 đ/năm (Không giới hạn người dùng, mặc định 100).
- Số lượng người dùng thực tế: Thanh trượt (Slider) kết hợp ô nhập số trực tiếp (từ 5 đến 200 người). Tự động gợi ý gói phù hợp nếu số người dùng vượt trần của gói được chọn.
- Dịch vụ cộng thêm: Checkbox tùy chọn "Đào tạo trực tiếp tại văn phòng khách hàng (+15.000.000 đ/gói 3 buổi)".
- Hình thức thanh toán: Chọn 1 trong 2:
  + "Thanh toán 100% khi ký kết" (Được chiết khấu thanh toán sớm: giảm thêm 5% trên giá sau chiết khấu doanh số).
  + "Thanh toán chia làm 3 đợt theo tiến độ" (Phụ thu chi phí dòng tiền: cộng thêm 4% trên giá niêm yết).
- Đề xuất giảm giá thêm từ Sales: Thanh trượt từ 0% đến 15% (bước nhảy 1%).

2. KHỐI LOGIC TÍNH TOÁN & CẢNH BÁO THẨM QUYỀN (DYNAMIC LOGIC):
- Chiết khấu theo bậc doanh số hợp đồng:
  + Dưới 30 triệu: 0%
  + Từ 30 triệu đến dưới 60 triệu: 5%
  + Từ 60 triệu đến dưới 100 triệu: 8%
  + Từ 100 triệu trở lên: 12%
- Tính tổng chiết khấu, phụ thu thanh toán và tính thuế VAT 10%.
- CẢNH BÁO THẨM QUYỀN DUYỆT DEAL (Thẻ trạng thái đổi màu động):
  + Nếu tổng mức giảm giá <= 5%: Badge màu xanh lá "[Thẩm quyền: Chuyên viên Sales tự quyết]".
  + Nếu tổng mức giảm giá > 5% và <= 8%: Badge màu vàng cam "[Cảnh báo: Cần Trưởng phòng Kinh doanh duyệt]".
  + Nếu tổng mức giảm giá > 8%: Badge màu đỏ nhấp nháy "[CẢNH BÁO ĐỎ: VƯỢT THẨM QUYỀN - Bắt buộc có chữ ký phê duyệt của Tổng Giám đốc CEO]".

3. KHỐI XUẤT BẢN THƯ CHÀO GIÁ (OUTPUT & PREVIEW):
- Một bảng tóm tắt chi phí rõ ràng: Giá gốc niêm yết -> Mức giảm giá/Chiết khấu -> Phụ thu (nếu có) -> Giá trước thuế -> Thuế VAT 10% -> TỔNG CỘNG THANH TOÁN (Số to, in đậm, nổi bật).
- Khung "Xem trước Thư chào giá chuẩn gửi khách": Điền tự động toàn bộ tên khách, ngày tháng, bảng chiết tính và số tài khoản ngân hàng của NovaTech (Vietcombank: 0071001234567 - CN TP.HCM).
- Nút bấm: "Sao chép toàn bộ Thư chào giá" (Click to copy text kèm hiệu ứng thông báo "Đã sao chép thành công!").

4. THIẾT KẾ UX/UI:
- Giao diện hiện đại, sạch sẽ, bố cục 2 cột (Cột trái: Điều khiển nhập liệu; Cột phải: Bảng tính tiền & Xem trước thư).
- Phông chữ tiếng Việt chuẩn đẹp, màu sắc nhận diện công nghệ chuyên nghiệp (Xanh Navy, Trắng, Xám sang trọng).
- Tương thích tốt trên màn hình máy tính và điện thoại.

Hãy xuất toàn bộ mã nguồn trong một Artifact duy nhất để tôi sử dụng ngay!
```

**Bước 3: Trải nghiệm ứng dụng tại Tab Preview**
1. Quan sát cửa sổ bên phải mở ra, Claude sẽ render giao diện ứng dụng.
2. Thử kéo thanh trượt số người dùng từ 15 lên 45 người.
3. Thử đổi phương thức từ "Thanh toán 100%" sang "Chia 3 đợt" $\rightarrow$ Xem số tiền phụ thu tự động nhảy.
4. Thử kéo thanh giảm giá thêm lên 10% $\rightarrow$ Xem thẻ cảnh báo thẩm quyền lập tức đổi sang màu đỏ kèm thông báo *"VƯỢT THẨM QUYỀN - Bắt buộc CEO duyệt"*.
5. Bấm nút **"Sao chép toàn bộ Thư chào giá"** và dán thử vào Zalo / Word xem nội dung có chuẩn xác không.
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

**Bước 1: Tiếp tục trong ô chat hoặc mở phiên chat mới**

**Bước 2: Copy và dán câu lệnh "Prompt-to-App" cho Case Study Pháp lý**

```markdown
Hãy đóng vai trò là một Chuyên gia Công nghệ Pháp lý (LegalTech Specialist) và Nhà thiết kế UI/UX cấp cao.
Hãy tạo một ỨNG DỤNG WEB TƯƠNG TÁC ĐỘC LẬP (Interactive Single-Page Web App) trong cửa sổ Artifact bằng HTML, Tailwind CSS và JavaScript.

Ứng dụng mang tên: "BẢNG ĐIỀU KHIỂN RÀ SOÁT HỢP ĐỒNG & CHẤM ĐIỂM RỦI RO PHÁP LÝ (NOVATECH LEGAL SCANNER)"

CÁC TÍNH NĂNG VÀ BỐ CỤC BẮT BUỘC:

1. KHỐI TỔNG QUAN & ĐO ĐỘ RỦI RO (RISK METRICS BAR):
- Đồng hồ đo mức độ rủi ro tổng thể (Risk Gauge / Scorecard): Hiển thị điểm số từ 0 - 100 và cấp độ an toàn (Xanh: An toàn | Vàng: Cần đàm phán | Đỏ: Nguy cơ pháp lý cao).
- Thống kê nhanh số lượng điều khoản: Tổng số điều khoản quét, Số điều khoản nghiêm trọng (Đỏ), Số điều khoản trung bình (Vàng), Số điều khoản an toàn (Xanh).

2. KHỐI BỘ LỌC & DANH SÁCH RÀ SOÁT CÁC ĐIỀU KHOẢN TRỌNG YẾU:
- Nạp sẵn sẵn 4 điều khoản rủi ro kinh điển trong hợp đồng công nghệ (dữ liệu mẫu thực tế):
  + Điều khoản 1 (Phạt vi phạm 20%): Vi phạm Điều 301 Luật Thương mại Việt Nam (mức trần tối đa 8%). Mức rủi ro: CỰC KỲ NGHIÊM TRỌNG.
  + Điều khoản 2 (Quyền sở hữu trí tuệ & Dữ liệu nguồn): Đối tác đòi nắm quyền sở hữu toàn bộ mã nguồn nền tảng. Mức rủi ro: CỰC KỲ NGHIÊM TRỌNG.
  + Điều khoản 3 (Đơn phương chấm dứt không bồi thường): Đối tác có quyền cắt hợp đồng chỉ báo trước 7 ngày mà không trả chi phí đã thực hiện. Mức rủi ro: TRUNG BÌNH.
  + Điều khoản 4 (Cơ quan tài phán & Địa điểm tranh chấp): Chỉ định tòa án tại nước ngoài thay vì VIAC tại Việt Nam. Mức rủi ro: TRUNG BÌNH.
- Mỗi điều khoản được thiết kế dạng thẻ tương tác (Card) có thể bấm mở rộng (Accordion) xem chi tiết:
  + Nguyên văn điều khoản đối tác đề xuất (tô đỏ các cụm từ gài bẫy).
  + Căn cứ pháp lý & Lý do bất lợi cho công ty.
  + Câu chữ đề xuất viết lại (Redline) chuẩn chỉ, thiện chí hợp tác.
  + Nút bấm "Sao chép câu chữ Redline" để đi đàm phán.

3. KHỐI NHẬP LIỆU THỰC TẾ (LIVE AUDIT INPUT):
- Ô nhập liệu cho phép người dùng dán thêm một điều khoản mới bất kỳ.
- Nút "Chấm điểm điều khoản mới": Sau khi bấm, mô phỏng quá trình quét và tự động phân tích hiển thị kết quả trực quan ngay bên dưới.

4. NÚT XUẤT BÁO CÁO NHANH:
- Nút "Sao chép toàn bộ Bảng đối chiếu rủi ro sang văn bản" (định dạng sẵn bảng Markdown/Text đẹp để gửi sếp hoặc đính kèm email).

5. THIẾT KẾ & TRẢI NGHIỆM:
- Phong cách giao diện chuẩn văn phòng luật hiện đại (Corporate Legal Tech): Gam màu Xanh Đen (Slate/Indigo), Trắng, cảnh báo màu Đỏ Rượu/Vàng Hổ Phách.
- Giao diện trực quan, rõ ràng, không rối mắt, có thanh tìm kiếm nhanh các điều khoản theo từ khóa.

Hãy tạo ứng dụng hoàn chỉnh trong một Artifact độc lập!
```

**Bước 3: Trải nghiệm và thử nghiệm công cụ**
1. Bấm mở rộng từng thẻ điều khoản để xem cách ứng dụng làm nổi bật câu chữ gài bẫy và phần đề xuất viết lại.
2. Bấm thử nút "Sao chép câu chữ Redline" của Điều khoản 1 (Mức phạt 20%) xem nội dung đã dẫn chiếu chính xác Điều 301 Luật Thương mại chưa.
3. Thử dán một đoạn điều khoản thực tế từ công việc của bạn vào ô nhập liệu để kiểm tra tính hữu dụng.
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

Chọn **1 trong 2 đề bài** sau để tự tay làm công cụ cho công việc của chính bạn:

- **Đề bài A (Khối Bán hàng / Marketing / Chăm sóc khách hàng):**
  - Xây dựng một **"Bảng tính ROI & Báo giá dịch vụ tự động"** hoặc **"Bộ công cụ chấm điểm Lead tiềm năng (Lead Scoring Calculator)"** cho công ty bạn.
  - Yêu cầu: Có ít nhất 3 tham số đầu vào, có logic phân loại màu sắc (Nóng / Ấm / Lạnh), có bảng tóm tắt đề xuất hành động tiếp theo.

- **Đề bài B (Khối Nhân sự / Vận hành / Quản lý nội bộ):**
  - Xây dựng một **"Bảng tính lương Net sang Gross & Chi phí doanh nghiệp"** hoặc **"Checklist tiếp nhận nhân sự mới (Interactive Onboarding Tracker)"** có các checkbox tích chọn hoàn thành nhiệm vụ theo ngày/tuần và thanh tiến độ hoàn thành (Progress Bar % tự nhảy).

---

### 4.2. Nghiệm thu buổi 2: Danh mục kiểm tra thành phẩm

Hãy tự kiểm tra lại sản phẩm của bạn trước khi đóng máy:

#### Về kỹ năng thao tác:
- [ ] Phân biệt rõ sự khác nhau giữa nội dung trong khung Chat và nội dung trong cửa sổ Artifacts.
- [ ] Nắm vững công thức 4 thành tố **Prompt-to-App (I - L - O - U)** để đặc tả công cụ cho AI.
- [ ] Biết cách xem trước tại tab **Preview**, chuyển qua tab **Code** và sử dụng lịch sử phiên bản (**Versions**).
- [ ] Biết cách dùng ngôn ngữ nói thông thường để yêu cầu Claude tinh chỉnh giao diện hoặc bổ sung tính năng mà không cần biết lập trình.
- [ ] Nắm được cách xử lý khi gặp lỗi trắng màn hình hoặc nút bấm không ăn.
- [ ] Xuất bản thành công ít nhất **01 đường link Public Artifact** và gửi mở thử nghiệm trên điện thoại hoặc tab ẩn danh.

#### Về sản phẩm số mang về:
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
