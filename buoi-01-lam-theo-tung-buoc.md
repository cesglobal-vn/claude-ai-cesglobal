# Buổi 1: Thiết lập bảo mật và dựng trợ lý Claude chuyên việc

## Nhịp buổi

| Phần | Nội dung |
|:---:|---|
| **0** | Khóa này giúp bạn bớt được việc gì? (Lộ trình 6 buổi) |
| **1** | Thiết lập tài khoản, Bảo mật & Bộ nhớ (Settings & Memory) |
| **2** | Dựng Trợ lý Chuyên việc với Claude Projects & Cowork (2 Case Study Thực chiến) |
| **3** | Lên lịch tự động (Scheduled Tasks) & Nghiệm thu cuối buổi |

---

## PHẦN 0. KHÓA NÀY GIÚP BẠN BỚT ĐƯỢC VIỆC GÌ?

- **Vấn đề quen thuộc:** Đa số chúng ta khi mới dùng AI đều mở khung chat lên, gõ vài câu bâng quơ, thấy nó trả lời chung chung, văn vở rồi lại tắt đi quay về làm tay trên Word, Excel như cũ.
- **Mục tiêu của khóa:** Dùng Claude để **bớt việc tay chân mỗi ngày**. Biến nó thành một đứa trợ lý việc gì cũng biết, hiểu tính bạn và quen việc ở công ty bạn.

### 3 nguyên tắc của lớp mình

1. **Làm trên việc thật của bạn:** Không làm bài tập mẫu vô thưởng vô phạt. Bạn cứ lấy đúng file báo cáo, bảng giá, hợp đồng hay ghi chép cuộc họp của bạn ra làm.
2. **Mỗi buổi có sản phẩm mang về dùng ngay:** Hết 2.5 tiếng là bạn có sẵn một công cụ hoặc trợ lý để sáng mai mang lên văn phòng dùng luôn.
3. **Không cần biết lập trình:** Bạn chỉ cần hiểu rõ việc của bạn, phần kỹ thuật Claude sẽ lo.

### Lộ trình 6 buổi: Từng bước giảm việc tay chân

| Buổi | Bạn sẽ làm được gì | Sản phẩm cầm về |
|:---:|---|---|
| **1** | Cài đặt bảo mật dữ liệu & tạo trợ lý hiểu việc | 1 Trợ lý riêng nạp sẵn tài liệu và mẫu biểu của bạn |
| **2** | Tự làm công cụ làm việc không cần viết code | 1 Mini web app / bảng tính tương tác có link gửi đồng nghiệp dùng chung |
| **3** | Nối Claude với Google Drive, Sheets, Gmail | Báo cáo tự động đọc số liệu thật, khỏi copy-paste tay |
| **4** | Đưa Claude xuống chạy trên máy tính (Claude Code) | Claude tự đọc, phân loại và sửa hàng loạt file Word, Excel trên ổ cứng |
| **5** | Đóng gói cách làm thành Skill và chia việc cho Trợ lý | 1 Skill quy trình chuẩn để Claude tự làm theo từng bước, không phải nhắc lại |
| **6** | Ghép tất cả thành một quy trình tự động | 1 Luồng làm việc tự chạy từ đầu đến cuối cho công việc của bạn |

---

## PHẦN 1. THIẾT LẬP TÀI KHOẢN, BẢO MẬT & BỘ NHỚ (SETTINGS & MEMORY)

### 1.1. Khóa bảo mật dữ liệu công việc (Privacy)

- Mặc định, các nền tảng AI có thể dùng nội dung chat để huấn luyện mô hình.
- Với công việc doanh nghiệp (báo cáo tài chính, doanh thu, thông tin khách hàng), việc bắt buộc đầu tiên là **tắt tính năng chia sẻ dữ liệu huấn luyện**.
- Tắt xong, dữ liệu hoàn toàn nằm trong không gian riêng của bạn, Anthropic không đem đi train AI.

<details>
<summary><b>Thao tác thực hành: Khóa bảo mật dữ liệu</b> (bấm để mở)</summary>

1. Bấm vào ảnh đại diện hoặc tên tài khoản ở góc dưới cùng bên trái màn hình -> Chọn **Settings**.
2. Ở menu bên trái, bấm chọn mục **Privacy**.
3. Tìm dòng: **"Help improve our AI models"**.
4. Gạt công tắc sang trạng thái **TẮT** (công tắc chuyển sang màu xám).</details>

---

### 1.2. Cài đặt Profile danh xưng và ngành nghề (General)

- Giúp Claude biết xưng hô chuẩn mực và hiểu bạn đang nhìn bài toán dưới góc độ chuyên môn nào (quản lý, marketing, tài chính hay vận hành).
- Khai báo một lần trong cài đặt chung, có hiệu lực trên mọi cuộc trò chuyện.

<details>
<summary><b>Thao tác thực hành: Cài đặt Profile</b> (bấm để mở)</summary>

1. Trong bảng **Settings**, bấm vào mục **General** (ở đầu danh sách bên trái).
2. Điền thông tin vào khối **Profile**:
   - **Full name:** [Họ và tên của bạn]
   - **What should Claude call you?:** [Tên bạn muốn Claude gọi, ví dụ: Anh Nam / Chị Lan]
   - **What best describes your work?:** Bấm mũi tên chọn ngành nghề sát nhất (ví dụ: Management, Marketing, Operations, Finance, Engineering).</details>

---

### 1.3. Cài đặt bộ quy tắc ứng xử dùng chung (Instructions for Claude)

- Đây là "chỉ dẫn gốc" của bạn, có hiệu lực trên mọi cuộc trò chuyện trong tài khoản.
- Không để AI chào hỏi rườm rà hay tự ý bịa số liệu. Cần ghim 5 nguyên tắc ứng xử chuẩn văn phòng.

<details>
<summary><b>Thao tác thực hành: Dán mẫu chỉ dẫn gốc</b> (bấm để mở)</summary>

1. Vẫn tại mục **General**, cuộn chuột xuống ô **Instructions for Claude**.
2. Copy đoạn mẫu sau và dán thẳng vào ô:

```
1. Luôn phản hồi bằng tiếng Việt chuẩn mực, gãy gọn, chuyên nghiệp.
2. Đi thẳng vào câu trả lời và giải pháp. Không mở đầu bằng lời chào rườm rà ("Chào bạn, tôi rất vui..."), không kết thúc bằng lời cảm ơn sáo rỗng.
3. Khi phân tích hoặc lập kế hoạch, ưu tiên trình bày bằng gạch đầu dòng và bảng biểu để dễ theo dõi.
4. Nếu yêu cầu thiếu dữ liệu cần thiết, hãy đặt câu hỏi ngắn để làm rõ thay vì tự đoán mò.
5. Tuyệt đối không tự bịa thông tin, số liệu, tên người hoặc điều khoản khi tài liệu không đề cập.
```
</details>

---

### 1.4. Kích hoạt và nạp ký ức công việc (Memory)

- Tính năng **Memory (Trí nhớ dài hạn)** đóng vai trò như cuốn sổ tay của Claude: nó tự ghi nhớ thói quen, dự án đang chạy qua các cuộc chat.
- Người dùng nắm toàn quyền kiểm soát: có thể tự gõ nạp ký ức mới, xem lại các mục đang nhớ và bấm nút xóa khi dự án kết thúc.

<details>
<summary><b>Thao tác thực hành: Bật Memory và nạp bối cảnh dự án</b> (bấm để mở)</summary>

1. Trong bảng **Settings**, bấm vào mục **Memory** (biểu tượng đồng hồ).
2. Dòng **"Generate memory from chats"**: Gạt công tắc sang **BẬT** (màu xanh).
3. Dòng **"Include sensitive topics in memory"**: Giữ nguyên **TẮT** để bảo vệ dữ liệu nhạy cảm.
4. Cuộn xuống ô nhập dưới cùng của trang Memory, dán đoạn thông tin công việc của bạn (thay nội dung trong ngoặc vuông):

```
Tôi đang phụ trách phát triển kinh doanh tại Công ty Cổ phần Giải pháp Số NovaTech. Sản phẩm chính là phần mềm quản trị doanh nghiệp NovaERP và hạ tầng Cloud. Ưu tiên phong cách làm việc nhanh gọn, các báo giá luôn cần chiết tính rõ ràng giá trước thuế, mức chiết khấu và thuế VAT 10%.
```

5. Bấm Enter để lưu.</details>

---

## PHẦN 2. DỰNG TRỢ LÝ CHUYÊN VIỆC VỚI CLAUDE PROJECTS & COWORK

### 2.1. Nâng cấp tư duy: Từ "Chatbot hỏi-đáp" sang "Cộng sự tự chủ (Claude Cowork)"

#### 1. Sự chuyển dịch thế hệ: Chatbot vs AI Agent (Cộng sự số)
- **Chatbot truyền thống (Chế độ Chat):** Đóng vai trò như một "nhà tư vấn chỉ nói bằng miệng". Bạn hỏi một câu -> Claude trả lời một câu. Mọi thứ dừng lại ở các đoạn văn bản (text) trên màn hình, bạn phải ngồi trực trước máy tính để dẫn dắt từng bước và tự tay copy ra Word/Excel để format lại.
- **AI Agent (Chế độ Cowork):** Đóng vai trò như một "cộng sự thực thi bắt tay vào làm việc". Bạn chỉ cần giao mục tiêu đầu ra (Goal), Claude tự lập kế hoạch nhiều bước (Planning), tự chạy tính toán ngầm, tự đọc chéo tài liệu và **tự tạo ra file thành phẩm (.docx, .xlsx) tải về máy**. Bạn có thể rời máy tính đi uống cà phê rồi quay lại nhận kết quả.

---

#### 2. Bảng so sánh toàn diện: Claude Chat vs Claude Cowork

| Tiêu chí | Chế độ Chat (Hỏi - Đáp) | Chế độ Cowork (Cộng tác Tự chủ) |
|---|---|---|
| **Cơ chế tương tác** | Tuần tự từng câu 1:1. Hỏi câu nào trả lời câu đó. | Giao việc theo mục tiêu (Goal-driven), tự chia nhỏ thành chuỗi hành động đa bước. |
| **Mức độ rảnh tay** | Thấp: Bạn phải ngồi trực trước màn hình để bấm câu lệnh tiếp theo. | Cao: Giao việc xong có thể đóng máy/rời đi, Claude tự chạy ngầm đến khi hoàn thành. |
| **Môi trường thực thi** | Chạy trực tiếp trên giao diện web thông thường. | Chạy trong một **Cloud Sandbox (Hộp cát cô lập)** an toàn trên máy chủ của Anthropic. |
| **Khả năng tạo file** | Chỉ xuất văn bản text, bạn phải tự copy-paste vào Word/Excel và format lại. | **Tự tạo và xuất file thật:** File Word (.docx) định dạng sẵn bảng biểu, Excel (.xlsx) có công thức. |
| **Tính đa nền tảng** | Bị ràng buộc trên từng phiên làm việc cụ thể. | Bắt đầu giao việc trên máy tính (Desktop), ra ngoài xem tiến độ trên điện thoại (Mobile/Web). |
| **Tự động hóa** | Tắt trình duyệt là phiên làm việc dừng lại. | Kết hợp hoàn hảo với **Scheduled Tasks** để hẹn giờ tự chạy định kỳ trên Cloud. |

---

#### 3. Ma trận ra quyết định: Khi nào chọn Chat, khi nào chọn Cowork?

| Tình huống công việc | Chế độ tối ưu | Lý do |
|---|:---:|---|
| Dịch nhanh 1 email, sửa lỗi chính tả, hỏi giải thích 1 khái niệm lạ | **Chat** | Việc nhanh phát sinh 1 lần (one-off), không cần tạo file hay chia bước. |
| Lên ý tưởng (Brainstorming), trao đổi qua lại để tìm giải pháp | **Chat** | Cần sự tương tác liên tục và phản hồi tức thì giữa người và AI. |
| Tra cứu bảng giá + tính chiết khấu + xuất file Thư chào giá Word | **Cowork** | Quy trình nhiều bước, cần tạo ra file văn bản định dạng chuẩn tải về máy. |
| Đọc dự thảo hợp đồng 5 trang + đối soát tiêu chuẩn + lập biên bản rà soát | **Cowork** | Đa tác vụ, đối soát chéo tài liệu lớn và xuất báo cáo rủi ro hoàn chỉnh. |
| Hẹn giờ tự tổng hợp báo cáo vào 17h chiều thứ Sáu hàng tuần | **Cowork** | Cần môi trường tự chạy ngầm trên cloud (kết hợp Scheduled Tasks). |

---

### 2.2. Vì sao không nên dùng ô chat thông thường cho công việc lâu dài?

- **Chat thông thường (ngoài màn hình chính):**
  - Mỗi lần mở chat mới là một phiên làm việc hoàn toàn độc lập, tách rời nhau, không lưu giữ liên kết.
  - **Hợp với việc gì:** Rất tiện cho các việc phát sinh một lần rồi thôi (one-off) như dịch nhanh một đoạn email, sửa lỗi chính tả một bài viết, hỏi giải thích một thuật ngữ lạ.
  - **Bất tiện khi làm việc thật:** Cứ bấm chat mới là Claude lại "quên sạch". Bạn lại phải mất công đính kèm lại bảng giá, quy chế chiết khấu, mẫu thư chào giá... Vừa mất thời gian vừa dễ sót thông tin.
- **Claude Projects (Không gian làm việc chuyên việc):**
  - Giải pháp là **chia ngăn kéo hồ sơ**: Mỗi đầu việc lớn có một không gian riêng.
  - Bạn nạp sẵn tài liệu biểu mẫu và quy chế làm việc vào ngăn kéo này một lần duy nhất. Sau này cứ mở Project ra giao việc là Claude tự động hiểu bối cảnh và áp dụng đúng quy chế công ty, không cần giải thích lại từ đầu.

#### Project Instructions là gì?
- Nó giống như bản **"Mô tả công việc (Job Description)"** và **"Sổ tay quy trình"** mà bạn giao cho một nhân sự mới vào ngày đầu nhận việc.

#### Nếu không viết Instructions thì sao?
- Claude sẽ như một bạn thực tập sinh ngơ ngác: Bạn bảo *"Báo giá cho anh khách này"* thì nó chỉ biết tính giá theo cảm tính, không biết công ty có quy chế chiết khấu gì, không biết ai có quyền giảm giá, và mỗi lần chat bạn lại phải gõ nhắc lại từ đầu rất mệt mỏi.

#### Cách viết Instructions cho người mới tinh (Không cần tự viết từ đầu!)
- Bạn không cần phải ngồi vắt óc nghĩ từng câu từng chữ tiếng Anh hay kỹ thuật cao siêu. Bạn là người hiểu công việc của mình nhất, bạn chỉ cần:
  1. Nạp tài liệu vào mục Context.
  2. Gõ một câu lệnh bằng ngôn ngữ nói hàng ngày của bạn: **Mô tả quy trình xử lý** (Khi đưa dữ liệu vào thì làm gì -> Bước 1 làm gì, Bước 2 làm gì, Bước 3 làm gì -> Output ra sao) và bảo Claude: *"Đọc các file trong Context và viết lại thành bản Project Instructions chuẩn chỉnh cho tôi nhé!"*.
  3. Claude đọc tài liệu + hiểu quy trình của bạn -> Tự sinh ra bản Instructions chuyên nghiệp. Bạn chỉ việc bấm Copy và dán vào ô Instructions là xong!

---

### 2.3. Case Study 1: Trợ lý Báo giá & Xử lý Deal Bán hàng B2B (NovaTech)

#### Nỗi đau thực tế trong hoạt động bán hàng B2B
- Khách hàng nhắn hỏi giá với đủ điều kiện phức tạp: *"Bên anh có 45 nhân sự, cần dùng gói Professional, muốn đào tạo tại văn phòng ở Bình Thạnh, thanh toán làm 3 đợt, bên em bớt được 15% không? Báo giá gấp cho anh nhé"*.
- Nhân viên kinh doanh phải mở cùng lúc 3 file: Bảng giá PDF, Quy chế chiết khấu Word, Mẫu thư chào giá Word.
- Rất dễ tính nhầm bậc chiết khấu, quên tính phụ phí chia đợt thanh toán, hoặc tự ý giảm giá vượt thẩm quyền làm công ty chịu rủi ro.

#### Thao tác 1: Tạo Project & Nạp 3 file tài liệu vào Context

Trước khi nạp, hãy hiểu rõ **3 file này là gì và vai trò của từng file:**
1. `Bảng giá phần mềm quản trị và giải pháp số 2026 - NovaTech.pdf` (3 trang): Bảng giá niêm yết chính thức 4 gói phần mềm (Starter, Professional, Enterprise, Custom), phụ phí đào tạo trực tiếp tại văn phòng (15 triệu/3 buổi) và cam kết thời gian hoạt động Uptime SLA 99.9% -> *Để trợ lý biết chính xác đơn giá gốc và các chi phí dịch vụ đi kèm của công ty.*
2. `Quy chế chiết khấu thương mại và chính sách thanh toán - NovaTech.docx` (4 trang): Quy định mức giảm giá theo bậc doanh số hợp đồng (0% - 12%), ưu đãi thanh toán sớm (giảm 5% khi trả 100%), phụ thu dòng tiền nếu chia đợt/trả chậm (4%), và bảng phân cấp thẩm quyền duyệt giá (Sales tối đa 5%, Trưởng phòng 8%, trên 8% bắt buộc CEO ký) -> *Để trợ lý kiểm soát tài chính, không tự ý giảm giá bừa bãi.*
3. `Mẫu thư chào giá và thỏa thuận dịch vụ chuẩn - NovaTech.docx` (2 trang): Biểu mẫu văn bản chuẩn nhận diện thương hiệu, có sẵn cấu trúc bảng biểu và thông tin số tài khoản ngân hàng Vietcombank của công ty -> *Để trợ lý điền thẳng số liệu vào thành văn bản hoàn chỉnh gửi khách.*

<details>
<summary><b>Thao tác thực hành: Tạo Project và nạp 3 file vào Context</b> (bấm để mở)</summary>

1. Bấm vào mục **Projects** trên thanh menu bên trái màn hình -> Bấm nút **Create Project** (hoặc dấu `+`).
2. Đặt tên dự án: `Trợ lý Báo giá & Thương mại B2B - NovaTech` -> Chọn **Private** -> Bấm tạo.
3. Ở cột bên phải của Project, tìm khối **Context** -> Bấm nút `+` (hoặc dòng *"Add PDFs, documents..."*).
4. Mở thư mục `demo-files/buoi-01/` trên máy tính, chọn cả 3 file:
   - `Bảng giá phần mềm quản trị và giải pháp số 2026 - NovaTech.pdf`
   - `Quy chế chiết khấu thương mại và chính sách thanh toán - NovaTech.docx`
   - `Mẫu thư chào giá và thỏa thuận dịch vụ chuẩn - NovaTech.docx`
5. Bấm **Open / Tải lên**.
6. Kiểm tra tài liệu đã nạp bằng cách gõ câu lệnh sau vào ô chat:

```
Dựa vào các tài liệu trong mục Context của dự án này, hãy trả lời nhanh:
1. Gói phần mềm Professional có đơn giá niêm yết bao nhiêu một năm và áp dụng cho quy mô bao nhiêu người dùng?
2. Theo Quy chế chiết khấu, nhân viên kinh doanh được quyền tự quyết mức chiết khấu tối đa bao nhiêu phần trăm? Muốn chiết khấu 10% thì phải do cấp nào phê duyệt?
```
</details>

#### Thao tác 2: Đưa quy trình cho Claude tự viết Instructions & Cài đặt Trợ lý

<details>
<summary><b>Thao tác thực hành: Nhờ Claude viết Instructions và dán vào Project</b> (bấm để mở)</summary>

**Bước 1: Nhờ Claude tự viết Instructions bám theo quy trình của bạn**
Trong ô chat của Project, copy và dán câu lệnh mô tả quy trình sau:

```
Hiện tôi cần viết Instructions cho project này để làm trợ lý báo giá phần mềm B2B cho công ty NovaTech.
Quy trình xử lý tôi muốn như sau:
- Khi tôi đưa thông tin yêu cầu của khách hàng vào (số lượng người dùng, nhu cầu đào tạo, phương thức thanh toán, mức giảm giá khách đòi...):
  + Bước 1: Tra đúng gói phần mềm trong Bảng giá và tính tổng giá niêm yết.
  + Bước 2: Tính chiết khấu theo Quy chế chiết khấu (giảm thêm nếu trả 100%, phụ thu nếu chia 3 đợt).
  + Bước 3: Kiểm soát thẩm quyền phê duyệt giảm giá (dưới 5% là Sales tự quyết; 5% - 8% cần Trưởng phòng duyệt; trên 8% là vượt quyền, bắt buộc CEO duyệt).
  + Bước 4: Soạn Thư chào giá hoàn chỉnh theo đúng cấu trúc của Mẫu thư chào giá trong Context.
  + Chống ảo giác: Tính chính xác từng con số, nêu rõ giá trước thuế, VAT 10% và tổng thanh toán; đính kèm số tài khoản Vietcombank chuẩn.
Bạn hãy đọc kỹ 3 file tài liệu trong Context và viết lại thành một bản Project Instructions thật chuẩn chỉnh, chuyên nghiệp để tôi copy dán vào ô Instructions nhé.
```

**Bước 2: Copy bản Instructions được sinh ra và dán vào ô Instructions**
1. Claude sẽ đọc 3 file tài liệu và xuất ra một bản Instructions chuẩn mực.
2. Bấm nút **Copy** đoạn văn bản mà Claude vừa tạo *(hoặc bạn có thể dùng ngay bản chuẩn bị sẵn ở khung dưới)*.
3. Ở cột bên phải màn hình Project, tìm ô **Instructions** -> Bấm biểu tượng cây bút sửa -> Dán nội dung vào -> Bấm **Save**.

*(Bản mẫu chuẩn bị sẵn để bạn đối chiếu hoặc copy dùng ngay nếu cần:)*
```markdown
# TRỢ LÝ BÁO GIÁ & THƯƠNG MẠI B2B - NOVATECH

## 1. VAI TRÒ
Bạn là Chuyên viên Hỗ trợ Kinh doanh (Deal Desk Specialist) cấp cao tại Công ty Cổ phần Giải pháp Số NovaTech. Nhiệm vụ của bạn là tiếp nhận yêu cầu báo giá từ khách hàng, đối chiếu chính xác Bảng giá và Quy chế chiết khấu nội bộ để tính toán chi phí tối ưu và soạn thảo Thư chào giá hoàn chỉnh.

## 2. QUY TRÌNH XỬ LÝ DEAL (4 BƯỚC BẮT BUỘC)
- Bước 1 (Phân tích nhu cầu): Xác định quy mô nhân sự của khách để chọn đúng gói (Standard, Professional, Enterprise) và các dịch vụ đào tạo đi kèm.
- Bước 2 (Tra cứu & Chiết tính):
  + Lấy đơn giá niêm yết từ file Bảng giá.
  + Áp dụng mức chiết khấu bậc thang theo giá trị hợp đồng từ file Quy chế chiết khấu.
  + Áp dụng ưu đãi thanh toán (giảm thêm 5% nếu trả 100%, phụ thu 4% nếu chia 3 đợt hoặc nợ sau 30 ngày).
- Bước 3 (Kiểm soát thẩm quyền phê duyệt):
  + Nếu mức giảm giá của deal nằm trong mức 0% - 5%: Ghi chú "[Thẩm quyền Sales tự quyết]".
  + Nếu khách yêu cầu giảm trên 5% - 8%: Cảnh báo "[Cần Trưởng phòng Kinh doanh phê duyệt trước khi gửi khách]".
  + Nếu khách yêu cầu giảm trên 8% hoặc nợ quá hạn: Cảnh báo đỏ "[VƯỢT THẨM QUYỀN - Bắt buộc có chữ ký phê duyệt của Tổng Giám đốc CEO]".
- Bước 4 (Soạn thảo văn bản): Xuất Thư chào giá hoàn chỉnh theo đúng cấu trúc của file Mẫu thư chào giá trong Context.

## 3. ĐIỀU KHOẢN CHỐNG ẢO GIÁC & AN TOÀN TÀI CHÍNH
- Tuyệt đối tính toán chính xác từng con số, nêu rõ giá trước thuế, tiền thuế VAT 10% và tổng thanh toán sau thuế.
- Cấm tự ý bịa thêm các ưu đãi không có trong Quy chế (như miễn phí máy chủ riêng, tặng thêm người dùng).
- Luôn đính kèm thông tin tài khoản thụ hưởng Vietcombank chuẩn của công ty ở chân thư chào giá.
```

> **Lưu ý về ô Memory:** Mục Memory ở ngay bên dưới bạn cứ để trống. Trong quá trình bạn chat và xử lý công việc sau này, Claude sẽ tự động lắng nghe và tích lũy thói quen, cách xưng hô hay bối cảnh dự án của bạn vào đây. Bạn luôn có quyền xem lại hoặc chỉnh sửa bất cứ lúc nào, nhưng hiện tại không cần gõ dán gì vào đây.
</details>

#### Thao tác 3: Thực hành xử lý trọn vẹn vòng đời một deal bán hàng (Hands-on trong 1 phiên chat)

- **Lưu ý quan trọng:** Toàn bộ 4 tình huống dưới đây diễn ra trong **CÙNG 1 PHIÊN CHAT LIÊN TỤC** của Project `Trợ lý Báo giá & Thương mại B2B - NovaTech`.
- Bạn **không cần mở chat mới**, cứ gõ nối tiếp theo diễn biến cuộc đàm phán để thấy Claude ghi nhớ toàn bộ ngữ cảnh và đồng hành cùng bạn từ lúc tiếp nhận deal đến khi chốt hợp đồng!

<details>
<summary><b>Tình huống 1: Tiếp nhận yêu cầu & Bóc tách deal phức tạp (Deal Nam Hải)</b> (bấm để mở)</summary>

Gõ tin nhắn đầu tiên vào ô chat của Project:
```
Khách hàng là Công ty Cổ phần Thương mại Dịch vụ Nam Hải vừa gửi yêu cầu sau:
"Bên anh có 45 nhân sự cần dùng phần mềm quản lý bán hàng và kho. Anh muốn bên em
đến đào tạo trực tiếp tại văn phòng công ty anh ở Quận Bình Thạnh (3 buổi).
Anh muốn thanh toán làm 3 đợt. Do ngân sách có hạn, bên em có giảm được 15% tổng hóa đơn không?
Báo giá gấp cho anh nhé."

Hãy xử lý yêu cầu này theo đúng quy chế và tư vấn cách xử lý giúp tôi.
```
</details>

<details>
<summary><b>Tình huống 2: Khách chê đắt & so sánh với đối thủ cạnh tranh (Chat tiếp ngay bên dưới)</b> (bấm để mở)</summary>

Khách phản hồi ép giá. Bạn gõ tiếp ngay trong phiên chat:
```
Khách hàng Nam Hải nhắn lại: "Anh thấy bên đối thủ khác đang chào gói tính năng tương tự rẻ hơn bên em tầm 20%. Em xem có bớt thêm được không chứ mức giá 73 triệu này sếp anh khó duyệt lắm?"

Hãy giúp tôi soạn một tin nhắn phản hồi khéo léo, giữ vững mức giá dựa trên cam kết chất lượng Uptime SLA 99.9% và dịch vụ đào tạo tại chỗ của chúng ta, đồng thời gợi ý khách phương án thanh toán 100% để hưởng ưu đãi tối đa.
```
</details>

<details>
<summary><b>Tình huống 3: Lập bảng so sánh 2 phương án tài chính gửi Giám đốc khách hàng (Chat tiếp)</b> (bấm để mở)</summary>

Để khách có căn cứ trình sếp, bạn gõ tiếp ngay trong phiên chat:
```
Để khách dễ trình Tổng Giám đốc của họ duyệt ngân sách, hãy lập cho tôi một BẢNG SO SÁNH 2 PHƯƠNG ÁN tài chính thật trực quan:
- Phương án A (Thanh toán 100% một lần): Hưởng mức chiết khấu tối đa hợp lệ (8% theo phê duyệt của Trưởng phòng + 5% ưu đãi thanh toán sớm).
- Phương án B (Thanh toán làm 3 đợt): Không được ưu đãi thanh toán sớm và phải chịu phụ phí dòng tiền 4%.
Phân tích rõ số tiền cụ thể khách tiết kiệm được nếu chọn Phương án A để họ thấy rõ lợi ích dòng tiền.
```
</details>

<details>
<summary><b>Tình huống 4: Xuất Thư chào giá hoàn chỉnh để in ấn/ký tên (Chat tiếp)</b> (bấm để mở)</summary>

Khách đã đồng ý chốt, bạn gõ tiếp câu lệnh cuối cùng:
```
Khách hàng Nam Hải đã đồng ý chốt theo Phương án A (Thanh toán 100% để hưởng ưu đãi tối đa).
Hãy xuất toàn bộ Thư chào giá chính thức theo đúng cấu trúc của Mẫu thư chào giá trong Context:
- Điền đầy đủ pháp nhân khách hàng (Công ty CP Thương mại Dịch vụ Nam Hải).
- Chi tiết dịch vụ: Gói Professional (50 users) + 3 buổi đào tạo tại chỗ ở Bình Thạnh.
- Bảng chiết tính số tiền cuối cùng sau thuế VAT 10%.
- Thông tin tài khoản thụ hưởng Vietcombank chuẩn của NovaTech.
- Người ký đại diện: Nguyễn Văn Hùng (Trưởng phòng Kinh doanh).
Xuất văn bản hoàn chỉnh để tôi in ra trình ký đóng dấu ngay.
```
</details>

---

### 2.4. Case Study 2: Trợ lý Rà soát Hợp đồng & Cảnh báo Rủi ro Pháp lý (NovaTech)

#### Nỗi đau thực tế trong rà soát hợp đồng kinh tế
- Đối tác gửi sang một bản hợp đồng kinh tế dài 5 trang với nhiều thuật ngữ pháp lý lắt léo.
- Doanh nghiệp không có phòng pháp chế riêng, sếp đọc lướt qua rất dễ ký nhầm vào các điều khoản "chết người": phạt vi phạm vô lý (20% - 30%), bị ép thời hạn nợ kéo dài, hoặc bị tước đoạt toàn bộ quyền sở hữu trí tuệ đối với sản phẩm công nghệ.
- Ký nhầm một hợp đồng có thể gây thiệt hại hàng trăm triệu đồng và mất quyền kinh doanh sản phẩm của chính mình.

#### Thao tác 1: Tạo Project & Nạp bộ tài liệu pháp lý vào Context

Trước khi nạp, hãy hiểu rõ **vai trò của các tài liệu pháp lý này:**
1. `Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp - NovaTech.pdf` (3 trang): Cẩm nang pháp lý nội bộ, nêu rõ 5 "Ranh giới đỏ" bảo vệ quyền lợi công ty (mức phạt vi phạm tối đa 8% theo Điều 301 Luật Thương mại, thời hạn nợ tối đa 15 ngày làm việc, độc quyền mã nguồn cho NovaTech, trần bồi thường không quá giá trị hợp đồng 12 tháng, giải quyết tranh chấp tại VIAC TP.HCM) -> *Dùng làm bộ tiêu chí thẩm định tối thượng để bắt lỗi.*
2. `Mẫu hợp đồng dịch vụ chuẩn của công ty - NovaTech.docx` (4 trang): Hợp đồng khung chuẩn của NovaTech đã được luật sư rà soát kỹ lưỡng -> *Dùng làm "thước đo" câu chữ chuẩn mực bảo vệ công ty.*
3. `Hợp đồng dịch vụ phần mềm và hạ tầng số (Bản đối tác đề xuất).docx` (5 trang): Bản hợp đồng thực tế đối tác Nam Hải gửi sang, cố tình gài 4 điều khoản bẫy (ép nợ 60 ngày, tước đoạt mã nguồn, phạt 20%, ép xử tại Tòa án Quận Bình Thạnh) -> *Dùng làm bài tập thực tế để học viên cùng Claude bắt lỗi ở Thao tác 3.*

<details>
<summary><b>Thao tác thực hành: Tạo Project và nạp 2 file tiêu chuẩn pháp lý</b> (bấm để mở)</summary>

1. Bấm vào mục **Projects** trên menu bên trái -> Bấm **Create Project**.
2. Đặt tên: `Trợ lý Pháp chế & Rà soát Hợp đồng - NovaTech` -> Chọn **Private** -> Bấm tạo.
3. Ở cột bên phải của Project, tìm khối **Context** -> Bấm nút `+`.
4. Tải 2 file pháp lý từ thư mục `demo-files/buoi-01/`:
   - `Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp - NovaTech.pdf`
   - `Mẫu hợp đồng dịch vụ chuẩn của công ty - NovaTech.docx`
5. Kiểm tra tài liệu đã nạp bằng câu lệnh:

```
Dựa vào file "Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp", hãy tóm tắt nhanh
5 ranh giới đỏ (Red Flags) không thể thương lượng của công ty chúng ta là gì?
```
</details>

#### Thao tác 2: Đưa quy trình cho Claude tự viết Instructions & Cài đặt Trợ lý

<details>
<summary><b>Thao tác thực hành: Nhờ Claude viết Instructions và dán vào Project</b> (bấm để mở)</summary>

**Bước 1: Nhờ Claude tự viết Instructions bám theo quy trình của bạn**
Trong ô chat của Project, copy và dán câu lệnh mô tả quy trình sau:

```
Hiện tôi cần viết Instructions cho project này để làm trợ lý pháp chế rà soát hợp đồng kinh tế cho công ty NovaTech.
Quy trình xử lý tôi muốn như sau:
- Khi tôi đính kèm một file dự thảo hợp đồng của đối tác gửi sang:
  + Bước 1: Quét toàn bộ hợp đồng và đối soát với file "Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp" trong Context.
  + Bước 2: Bắt các điều khoản bất lợi, vi phạm pháp luật, đặc biệt kiểm tra nghiêm ngặt 5 ranh giới đỏ (mức phạt tối đa 8% theo Điều 301 Luật Thương mại, thời hạn nợ tối đa 15 ngày, giữ độc quyền mã nguồn cho NovaTech, trọng tài VIAC tại TP.HCM).
  + Bước 3: Lập bảng cảnh báo rủi ro (tên điều khoản, mức độ rủi ro, lý do vi phạm hoặc bất lợi, căn cứ điều luật).
  + Bước 4: Viết lại nguyên văn câu chữ đề xuất sửa đổi cho từng điều khoản để gửi lại đối tác đàm phán.
  + Chống ảo giác: Chỉ trích dẫn chính xác nội dung trong văn bản và luật pháp Việt Nam, không tự suy diễn.
Bạn hãy đọc kỹ 2 file tài liệu trong Context và viết lại thành một bản Project Instructions thật chuẩn chỉnh, chuyên nghiệp để tôi copy dán vào ô Instructions nhé.
```

**Bước 2: Copy bản Instructions được sinh ra và dán vào ô Instructions**
1. Claude sẽ đọc 2 file tài liệu và xuất ra một bản Instructions chuyên nghiệp.
2. Bấm nút **Copy** đoạn văn bản mà Claude vừa tạo *(hoặc bạn có thể dùng ngay bản chuẩn bị sẵn ở khung dưới)*.
3. Ở cột bên phải màn hình Project, tìm ô **Instructions** -> Bấm biểu tượng cây bút sửa -> Dán nội dung vào -> Bấm **Save**.

*(Bản mẫu chuẩn bị sẵn để bạn đối chiếu hoặc copy dùng ngay nếu cần:)*
```markdown
# TRỢ LÝ PHÁP CHẾ & RÀ SOÁT HỢP ĐỒNG - NOVATECH

## 1. VAI TRÒ
Bạn là Trưởng Ban Pháp chế và Quản trị Rủi ro Tuân thủ tại Công ty Cổ phần Giải pháp Số NovaTech. Nhiệm vụ của bạn là rà soát toàn diện các dự thảo hợp đồng kinh tế do đối tác gửi sang, phát hiện các điều khoản bất lợi, gài bẫy hoặc vi phạm pháp luật Việt Nam, và đề xuất phương án sửa đổi từng câu chữ để bảo vệ quyền lợi công ty.

## 2. QUY TRÌNH RÀ SOÁT (4 BƯỚC BẮT BUỘC)
- Bước 1 (Đọc quét & Phân loại): Quét toàn bộ hợp đồng của đối tác để lập danh mục các điều khoản trọng yếu (Phạm vi dịch vụ, Thanh toán, Nghiệm thu, Bảo hành, Phạt vi phạm, Bản quyền, Tranh chấp).
- Bước 2 (So khớp 5 Ranh giới đỏ):
  + Điều khoản Phạt vi phạm: Bắt buộc tuân thủ Điều 301 Luật Thương mại 2005 (tối đa không quá 8% phần vi phạm).
  + Điều khoản Thanh toán: Không chấp nhận thời hạn nợ trên 15 ngày làm việc và điều khoản lùi vô thời hạn.
  + Điều khoản Sở hữu trí tuệ: Tuyệt đối giữ quyền sở hữu mã nguồn, thuật toán cho NovaTech.
  + Điều khoản Giải quyết tranh chấp: Bắt buộc chọn Trọng tài Quốc tế Việt Nam (VIAC) tại TP.HCM.
- Bước 3 (Lập Bảng cảnh báo rủi ro): Liệt kê rõ: Tên điều khoản -> Mức độ rủi ro (Nghiêm trọng / Trung bình) -> Lý do vi phạm hoặc bất lợi -> Điều luật làm căn cứ.
- Bước 4 (Soạn câu chữ đàm phán lại): Viết lại nguyên văn điều khoản đề xuất mới để chuyên viên kinh doanh copy gửi lại đối tác.

## 3. ĐIỀU KHOẢN CHỐNG ẢO GIÁC
- Chỉ trích dẫn chính xác nội dung có trong hợp đồng của đối tác và các điều luật thực tế của Việt Nam.
- Không tự suy diễn các điều khoản ngầm hiểu mà văn bản không nêu.
```

> **Lưu ý về ô Memory:** Mục Memory ở đây bạn cũng để trống. Claude sẽ tự động ghi nhớ các lưu ý pháp lý của công ty qua các phiên làm việc sau này, không cần phải dán thủ công.
</details>

#### Thao tác 3: Thực hành rà soát trọn vẹn vòng đời một hợp đồng (Hands-on trong 1 phiên chat)

- **Lưu ý quan trọng:** Toàn bộ 5 bước dưới đây diễn ra trong **CÙNG 1 PHIÊN CHAT LIÊN TỤC** của Project `Trợ lý Pháp chế & Rà soát Hợp đồng - NovaTech`.
- Bạn chỉ cần đính kèm file hợp đồng 1 lần ở bước đầu tiên, sau đó gõ lệnh tương tác nối tiếp theo quy trình thẩm tra thực tế tại doanh nghiệp!

<details>
<summary><b>Bước 1: Đính kèm hợp đồng đối tác & Quét nhanh bức tranh tổng quan trong 10 giây</b> (bấm để mở)</summary>

1. Bấm vào biểu tượng đính kèm file (cái kẹp giấy hoặc dấu `+`) ở thanh chat của Project.
2. Chọn tải file `Hợp đồng dịch vụ phần mềm và hạ tầng số (Bản đối tác đề xuất).docx` từ thư mục `demo-files/buoi-01/`.
3. Gõ câu lệnh sau:

```
Đối tác Nam Hải vừa gửi sang bản dự thảo Hợp đồng dịch vụ phần mềm này.
Trước khi đi vào chi tiết, hãy đọc lướt toàn bộ hợp đồng và lập một BẢNG TỔNG QUAN TÓM TẮT các thông số trọng yếu: Giá trị hợp đồng, thời hạn thực hiện, tiến độ thanh toán, thời hạn bảo hành và cơ quan giải quyết tranh chấp.
```
</details>

<details>
<summary><b>Bước 2: Thẩm định chuyên sâu & Bắt trọn 4 bẫy pháp lý (Chat tiếp ngay bên dưới)</b> (bấm để mở)</summary>

Gõ tiếp ngay trong phiên chat:
```
Bây giờ, hãy đối soát toàn diện hợp đồng này với file "Bộ tiêu chuẩn rà soát pháp lý hợp đồng doanh nghiệp" trong Context của chúng ta.
Chỉ ra chính xác các điều khoản bất lợi, gài bẫy hoặc vi phạm pháp luật Việt Nam.
Trình bày thành BẢNG CẢNH BÁO RỦI RO gồm các cột: Tên điều khoản -> Mức độ rủi ro (Nghiêm trọng / Trung bình) -> Lý do bất lợi hoặc vi phạm điều luật nào.
```
</details>

<details>
<summary><b>Bước 3: Soạn câu chữ viết lại (Redline/Markup) để đàm phán lại (Chat tiếp)</b> (bấm để mở)</summary>

Gõ tiếp ngay trong phiên chat:
```
Đối với 4 điều khoản có rủi ro nghiêm trọng ở trên (Điều 6, Điều 7, Điều 9, Điều 11), hãy viết lại nguyên văn câu chữ đề xuất sửa đổi (redline) để chuyên viên kinh doanh copy gửi sang cho phòng pháp chế Nam Hải đàm phán lại. Câu từ cần chắc chắn về mặt pháp lý nhưng giữ văn phong lịch sự, thiện chí hợp tác.
```
</details>

<details>
<summary><b>Bước 4: Soạn Email ngoại giao chính thức từ Ban Giám đốc gửi đối tác (Chat tiếp)</b> (bấm để mở)</summary>

Gõ tiếp ngay trong phiên chat:
```
Hãy giúp tôi soạn một email chính thức từ Ban Pháp chế & Ban Giám đốc NovaTech gửi người phụ trách hợp đồng của Nam Hải. Email cần trình bày trang trọng, lịch sự, giải thích rõ lý do vì sao chúng ta cần điều chỉnh 4 điều khoản này (đặc biệt nêu rõ mức phạt 20% là trái Điều 301 Luật Thương mại Việt Nam) và đính kèm phương án sửa đổi để hai bên nhanh chóng tiến tới ký kết.
```
</details>

<details>
<summary><b>Bước 5: Lập Checklist 10 điểm an toàn trước khi sếp đặt bút ký (Chat tiếp)</b> (bấm để mở)</summary>

Gõ câu lệnh chốt phiên làm việc:
```
Giả sử sau khi đàm phán, đối tác gửi lại bản hợp đồng đã chỉnh sửa. Hãy lập giúp tôi một CHECKLIST 10 ĐIỂM KIỂM TRA NHANH (dạng bảng có các cột: Tiêu chí kiểm tra, Căn cứ pháp lý/tiêu chuẩn, Trạng thái Đạt/Chưa đạt) để chuyên viên kinh doanh tự rà lại lần cuối trước khi trình Tổng Giám đốc ký kết.
```
</details>

---

## PHẦN 3. LÊN LỊCH TỰ ĐỘNG (SCHEDULED TASKS) & NGHIỆM THU CUỐI BUỔI

### 3.1. Tìm hiểu tính năng Scheduled Tasks (Lên lịch định kỳ)

- Nhìn xuống góc dưới bên phải Project có khối **Scheduled**.
- Đây là tính năng hẹn giờ để Claude tự động làm việc định kỳ (ví dụ: đúng 17h thứ Sáu tự tổng hợp danh sách các deal báo giá hoặc các hợp đồng cần thẩm tra trong tuần).
- Hôm nay ta nhận diện vị trí tính năng này; Buổi 6 sẽ kết hợp cùng công cụ tự động hóa trên máy tính để tạo cỗ máy tự chạy hoàn chỉnh.

<details>
<summary><b>Thao tác thực hành: Quan sát khối Scheduled</b> (bấm để mở)</summary>

1. Nhìn xuống khối dưới cùng ở cột bên phải Project: **Scheduled** (có dấu `+`).
2. Bấm vào dấu `+` để xem bảng giao diện tạo lịch định kỳ.
3. Ghi nhận tính năng này để sẵn sàng cho bài toán tự động hóa hoàn chỉnh ở Buổi 6.
</details>

---

### 3.2. Nghiệm thu buổi 1: Kiểm lại những gì bạn đã có

Tự tay làm được:
- [ ] Khóa thành công mục `Help improve our AI models` trong `Settings > Privacy` để bảo vệ dữ liệu nội bộ.
- [ ] Thiết lập xong `Profile` và 5 nguyên tắc ứng xử gốc trong `Settings > General`.
- [ ] Bật `Memory` và nạp thành công 1 dòng bối cảnh công việc thực tế vào tài khoản.
- [ ] Nắm vững sự khác biệt giữa Chế độ Chat (Hỏi-đáp) và Chế độ Cowork (Cộng tác tự chủ) để chọn đúng công cụ cho từng tình huống công việc.
- [ ] Hiểu rõ sự khác biệt giữa Chat thông thường và Claude Projects để chọn đúng công cụ cho công việc lâu dài.
- [ ] Biết cách đưa quy trình bằng ngôn ngữ nói để Claude tự viết `Project Instructions` chuẩn chỉnh bám sát tài liệu.
- [ ] Tạo thành công **Case Study 1: Trợ lý Báo giá B2B**, nạp 3 file tài liệu vào `Context`, xử lý trọn vẹn 1 deal khách hàng phức tạp.
- [ ] Tạo thành công **Case Study 2: Trợ lý Pháp chế**, nạp bộ tiêu chuẩn vào `Context` và rà soát thành công 1 bản hợp đồng bắt trọn 4 bẫy pháp lý.

Hiểu để dùng sau:
- [ ] Vì sao không nên dùng Chat thông thường cho việc dài hạn mà phải dùng Claude Projects.
- [ ] Năng lực đối chiếu chéo nhiều file tài liệu (PDF, Word) cùng lúc trong Context.
- [ ] Nhận biết vị trí tính năng Scheduled Tasks để chuẩn bị cho tự động hóa ở Buổi 6.

Thiếu mục nào thì kéo lên làm lại đúng bước đó. Buổi sau ta sẽ **biến ý tưởng công việc thành công cụ mini, bảng tính tự động và ứng dụng tương tác chạy được ngay trên trình duyệt bằng Claude Artifacts**.
