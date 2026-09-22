# Buổi 4: Cho Claude Xuống Làm Việc Trên Máy Tính (Claude Code Desktop) & Chuẩn Hóa Không Gian Làm Việc

## Nhịp buổi

| Phần | Nội dung chi tiết | Thời lượng dự kiến |
|:---:|---|:---:|
| **0** | **Khởi động & Làm quen Giao diện Claude Code Desktop:**<br>- Tại sao cần đưa Claude xuống máy tính?<br>- Khám phá giao diện: Chọn folder dự án, xem cây thư mục, Built-in Browser, cơ chế xin quyền an toàn. | 20 phút |
| **1** | **Tương tác Từng bước với File & Khoảnh khắc "Àaaa...":**<br>- *Prompt 1.1:* Quét thư mục & nhận diện nội dung từng file.<br>- *Prompt 1.2:* Đọc sâu & đối chiếu số liệu chéo (Word vs Excel).<br>- *Prompt 1.3:* Tổng hợp thông tin & tạo Biên bản nghiệm thu mới.<br>- *Nhận diện nỗi đau:* File nằm lẫn lộn, tên tùy tiện, AI quên bối cảnh. | 45 phút |
| **2** | **Chuẩn hóa Cây Thư Mục Làm Việc & Tạo Thư Mục `.claude/`:**<br>- Quy tắc "5S" dữ liệu: `01_input`, `02_templates`, `03_output`.<br>- Khởi tạo thư mục ngầm `.claude/` (với `skills/` và `agents/`) làm bệ phóng cho Buổi 5.<br>- *Prompt 2:* Nhờ Claude tự động dọn dẹp và sắp xếp file ngăn nắp. | 25 phút |
| **3** | **"Bộ Não Ngữ Cảnh" `CLAUDE.md` - Đưa Nội Quy Công Ty Cho AI:**<br>- Bản chất: `CLAUDE.md` chính là ô Instructions trên máy tính.<br>- Tạo `CLAUDE.md` (Cách trực tiếp hoặc Claude phỏng vấn tự viết).<br>- Dán sơ đồ các phòng vào `CLAUDE.md` & kiểm tra phản xạ định vị.<br>- Thử nghiệm thực chiến với hồ sơ An Phú (AI tự làm đúng 100%). | 40 phút |
| **4** | **Nghiệm thu Buổi 4, Chia sẻ Thành phẩm & Cầu nối sang Buổi 5** | 20 phút |

---

## PHẦN 0. KHỞI ĐỘNG & LÀM QUEN GIAO DIỆN CLAUDE CODE DESKTOP

### 0.1. Điểm nghẽn từ bản Web: Tại sao dân văn phòng cần đưa Claude xuống máy tính?
- Ở 3 buổi trước, chúng ta đã khai thác rất nhiều sức mạnh của Claude trên nền tảng Web ([claude.ai](https://claude.ai)): từ tạo trợ lý tùy chỉnh, dựng Web App bằng Artifacts, cho đến kết nối Google Drive và Sheets.
- **Tuy nhiên, bản Web có những giới hạn lớn trong công việc hàng ngày:**
  - Bạn phải bấm tải từng file lên khung chat, bị giới hạn dung lượng và số lượng file.
  - Sau khi AI tạo ra tài liệu mới, bạn lại phải bấm tải file về máy rồi tự tay copy vào các thư mục lưu trữ.
  - Thực tế tại công ty: Bạn có hàng chục, hàng trăm file hợp đồng, bảng kê chi phí, hồ sơ khách hàng nằm rải rác trong ổ đĩa C, D. Bạn không thể ngồi tải từng file lên web được!
- **Claude Code Desktop giải quyết triệt để vấn đề này:**
  - Cho phép bạn chọn một thư mục bất kỳ trên máy tính để làm việc.
  - Claude có thể "bước vào" thư mục đó, tự đọc toàn bộ các file (Word, Excel, PDF, Text), tự đối chiếu số liệu và tự tạo ra file mới lưu thẳng vào ổ cứng của bạn.

---

### 0.2. Khám phá 5 khu vực chính trên giao diện Claude Code Desktop

```
┌────────────────────────────────────────────────────────────────────────┐
│                   GIAO DIỆN CLAUDE CODE DESKTOP                        │
├─────────────────┬──────────────────────────────────────────────────────┤
│ 1. FILE TREE    │ 3. KHUNG HỘI THOẠI & THỰC THI (Chat Area)            │
│ (Cây thư mục)   │ - Nơi bạn gõ câu lệnh bằng tiếng Việt tự nhiên       │
│                 │ - Claude hiển thị các bước suy nghĩ và thao tác      │
│ 📁 01_input/     │                                                      │
│ 📁 02_templates/ │ 4. BUILT-IN BROWSER (Trình duyệt tích hợp)           │
│ 📁 03_output/    │ - Mở xem trước các file HTML, Dashboard hoặc link    │
│ 📁 .claude/      │   tài liệu ngay trong app mà không cần mở Chrome     │
│ 📄 CLAUDE.md    ├──────────────────────────────────────────────────────┤
│                 │ 5. HỘP THOẠI XIN QUYỀN (Safety / Permission Gate)    │
│ 2. XEM FILE     │ - Nút "Allow / Approve" trước khi đọc, sửa, tạo file │
│ (File Preview)  │ - Đảm bảo dữ liệu an toàn, không bị xóa nhầm        │
└─────────────────┴──────────────────────────────────────────────────────┘
```

1. **Không gian chọn thư mục (Open Project Folder):** Nút mở thư mục dự án bạn muốn Claude cùng làm việc.
2. **Cây thư mục (File Explorer) & Khung xem file:** Duyệt nhanh toàn bộ file và thư mục con, bấm vào file nào là xem được nội dung file đó ngay lập tức.
3. **Khung hội thoại chính (Chat & Execution Area):** Nơi bạn trò chuyện và giao việc cho Claude bằng ngôn ngữ giao tiếp văn phòng bình thường.
4. **Trình duyệt tích hợp (Built-in Browser):** Điểm đặc biệt của Claude Desktop — có sẵn một trình duyệt bên trong để bạn xem trước các sản phẩm giao diện web, dashboard (như sản phẩm Buổi 2 & 3) hoặc kiểm tra tài liệu trực tuyến mà không phải nhảy tab.
5. **Cơ chế an toàn & xin quyền (Safety / Permission Gate):** Claude không bao giờ tự ý sửa hoặc xóa file bừa bãi. Trước khi thực hiện hành động can thiệp vào ổ cứng, Claude luôn hiển thị thông báo hỏi ý kiến: *"Bạn có cho phép đọc/sửa file này không?"* $\rightarrow$ Bạn bấm chấp thuận thì AI mới thực thi.

---

### 0.3. Thao tác thực hành: Mở thư mục dự án trên Claude Code Desktop

<details>
<summary><b>Thao tác thực hành: Chọn thư mục làm việc</b> (bấm để mở)</summary>

1. Mở ứng dụng **Claude** trên máy tính của bạn.
2. Bấm nút **Open Folder** (hoặc vào menu **File $\rightarrow$ Open Folder**).
3. Chọn thư mục thực hành của khóa học tại đường dẫn:  
   `claude-ai/demo-files/buoi-04/`  
   *(Nếu bạn dùng dữ liệu công việc thật của mình, hãy chọn thư mục chứa các file cần xử lý hôm nay).*
4. Nhìn sang cột bên trái: Bạn sẽ thấy 5 file mẫu đã xuất hiện trực tiếp trên cây thư mục:
   - `hop_dong_dich_vu_det_may_nam_dinh_raw.docx`
   - `bang_ke_chi_phi_trien_khai_thang_3.xlsx`
   - `ghi_chu_hop_giao_ban_20260315.txt`
   - `Mau_Bien_Ban_Nghiem_Thu_Chuan_NovaTech.docx`
   - `hop_dong_phan_mem_an_phu_chua_ky.docx`
5. Bấm thử vào file `ghi_chu_hop_giao_ban_20260315.txt` để xem nội dung hiển thị ngay trên màn hình.
</details>

---

## PHẦN 1. TƯƠNG TÁC TỪNG BƯỚC VỚI FILE & KHOẢNH KHẮC "ÀAAA..."

### 1.1. Bài toán thực tế
Bạn vừa tiếp nhận bộ hồ sơ nghiệm thu của dự án phần mềm với khách hàng **Công ty Cổ phần Dệt may Nam Định**.
Hiện trong thư mục đang có các file rời rạc gồm hợp đồng, bảng kê chi phí, biên bản họp và biểu mẫu chuẩn của công ty.

> [!TIP]
> **Nguyên tắc giao tiếp tự nhiên với AI trên máy tính:**
> Đừng bao giờ quăng một câu lệnh khổng lồ dồn ép AI làm tất cả mọi thứ ngay từ đầu.
> Hãy tương tác như với một người cộng sự thực thụ qua 3 bước:
> - **Bước 1:** Bảo AI đọc trước và tóm tắt xem trong thư mục đang có những gì.
> - **Bước 2:** Bảo AI đi sâu vào so sánh, đối chiếu số liệu giữa các file.
> - **Bước 3:** Khi số liệu đã chuẩn xác, mới bảo AI tổng hợp và xuất ra file văn bản mới.

---

### 1.2. Bước 1: Quét thư mục & Nhận diện nội dung từng file (Prompt 1.1)

<details>
<summary><b>Thao tác thực hành: Nhờ Claude đọc và tóm tắt hồ sơ</b> (bấm để mở)</summary>

**Gõ câu lệnh đơn giản sau vào Claude Desktop:**

```markdown
Quét thư mục này và cho tôi biết trong đây đang có những file gì, nội dung chính của từng file nói về vấn đề gì nhé.
```

**Quan sát phản hồi của Claude:**
Claude sẽ duyệt qua từng file và tóm tắt ngắn gọn cho bạn:
- Có 2 hợp đồng dịch vụ phần mềm (của Dệt may Nam Định và An Phú).
- 1 file Excel bảng kê chi phí triển khai tháng 3/2026.
- 1 file text ghi chép cuộc họp giao ban nghiệm thu ngày 15/03/2026.
- 1 file Word biểu mẫu biên bản nghiệm thu chuẩn của công ty NovaTech.

👉 Chỉ với 1 câu lệnh, bạn và Claude đã cùng nắm rõ bức tranh toàn cảnh của thư mục mà không cần tự tay mở từng file lên đọc!
</details>

---

### 1.3. Bước 2: Đọc sâu & Đối chiếu chéo số liệu giữa Word và Excel (Prompt 1.2)

Bây giờ chúng ta cần kiểm tra xem thông tin giữa hợp đồng pháp lý và bảng kê chi phí kỹ thuật có trùng khớp với nhau không.

<details>
<summary><b>Thao tác thực hành: Đối chiếu số liệu chéo</b> (bấm để mở)</summary>

**Gõ tiếp câu lệnh tự nhiên này vào khung chat:**

```markdown
Xem kỹ cho tôi 2 file hop_dong_dich_vu_det_may_nam_dinh_raw.docx và bang_ke_chi_phi_trien_khai_thang_3.xlsx. Đối chiếu xem số tiền thanh toán và số lượng tài khoản user giữa hợp đồng với bảng kê có khớp nhau không?
```

**Quan sát kết quả đối chiếu:**
Claude tự động mở đồng thời cả file Word lẫn file Excel, so sánh từng dòng và báo cáo:
- *Giá trị hợp đồng:* Cả 2 file đều ghi nhận chính xác **45.000.000 VNĐ**.
- *Số lượng tài khoản user:* Cả 2 file đều khớp đúng **35 tài khoản hoạt động**.
- *Hạng mục phát sinh:* Các mục đào tạo và tích hợp Zalo ZNS đều được miễn phí (0 VNĐ) theo đúng hợp đồng.
</details>

---

### 1.4. Bước 3: Tổng hợp thông tin & Tạo Biên bản nghiệm thu mới (Prompt 1.3)

Sau khi số liệu đã được xác nhận chuẩn xác 100%, chúng ta mới yêu cầu Claude lấy thông tin điền vào mẫu chuẩn để xuất file Word.

<details>
<summary><b>Thao tác thực hành: Tạo file biên bản nghiệm thu hoàn chỉnh</b> (bấm để mở)</summary>

**Gõ câu lệnh tiếp theo:**

```markdown
Số liệu khớp rồi đấy. Giờ đọc thêm file ghi_chu_hop_giao_ban_20260315.txt lấy thông tin tiến độ và người ký, rồi điền vào mẫu Mau_Bien_Ban_Nghiem_Thu_Chuan_NovaTech.docx để tạo cho tôi 1 file biên bản nghiệm thu hoàn chỉnh nhé.
```

**Quan sát Claude thực thi:**
1. Hộp thoại xin quyền xuất hiện: Claude hỏi bạn có cho phép tạo file Word mới trên máy tính không $\rightarrow$ Bấm **Approve (Cho phép)**.
2. Claude tự động đọc nội dung cuộc họp từ file text, lấy thông tin đại diện 2 bên (bà Nguyễn Thị Hương và ông Nguyễn Văn Hùng), điền vào file mẫu chuẩn.
3. Xuất hiện một file Word mới tinh ngay trên cây thư mục máy tính của bạn (ví dụ: `bien_ban_nghiem_thu.docx`)!
</details>

---

### 1.5. Khoảnh khắc "Àaaa..." - Nhìn ra "nỗi đau" khi làm việc lộn xộn

> [!WARNING]
> **Hãy dừng lại 1 phút và nhìn vào cây thư mục của bạn lúc này:**
> 1. **File nằm lẫn lộn một đống:** File hợp đồng gốc của khách gửi sang, file bảng kê, file ghi chú tạm và file biên bản nghiệm thu mới tạo ra... tất cả nằm chung một chỗ trong một thư mục duy nhất!
> 2. **Tên file đặt tùy tiện:** AI đặt tên theo ý nó (ví dụ: `bien_ban_nghiem_thu.docx`, không có ngày tháng năm, không có tên khách hàng). Nếu đồng nghiệp của bạn mở thư mục này ra, họ sẽ không biết file nào là file thô, file nào là mẫu, file nào là bản chính thức đã chốt.
> 3. **Nguy cơ xóa nhầm hoặc ghi đè:** Nếu bạn tiếp tục bảo Claude làm hợp đồng cho khách hàng khác, rất có thể nó sẽ ghi đè lên file mẫu chuẩn hoặc sửa nhầm vào file hợp đồng gốc!
> 4. **AI "mất trí nhớ" khi mở phiên mới:** Ngày mai bạn mở máy lên làm việc tiếp, Claude hoàn toàn không nhớ công ty bạn quy định đặt tên file thế nào, lưu ở đâu, và bạn lại phải ngồi gõ dặn dò lại từ đầu.

👉 **Rút ra kết luận xương máu:** *"Đưa AI xuống máy tính mà không có quy chuẩn sắp xếp thư mục và không có bảng nội quy, thì chẳng mấy chốc ổ cứng của bạn sẽ biến thành một bãi rác khổng lồ!"*

---

## PHẦN 2. CHUẨN HÓA CÂY THƯ MỤC LÀM VIỆC & CẤU TRÚC THƯ MỤC `.claude/`

### 2.1. Tư duy "5S" cho dữ liệu máy tính trong kỷ nguyên AI
Để làm việc chuyên nghiệp, mọi thư mục dự án cần được chia thành **3 ngăn dữ liệu rõ ràng** và **1 ngăn kỹ thuật ngầm**:

```
📁 buoi-04/
│
├── 📁 01_input/       <-- Ngăn dữ liệu thô (Hợp đồng khách gửi, file Excel số liệu, ghi chú)
│                           Nguyên tắc: CHỈ ĐỌC, TUYỆT ĐỐI KHÔNG SỬA HAY XÓA FILE GỐC.
│
├── 📁 02_templates/   <-- Ngăn chứa biểu mẫu chuẩn của công ty (Mẫu hợp đồng, mẫu biên bản)
│                           Nguyên tắc: File mẫu để AI nhân bản và điền thông tin vào.
│
├── 📁 03_output/      <-- Ngăn thành phẩm (Nơi AI xuất các file tài liệu đã hoàn thiện)
│                           Nguyên tắc: Mọi file mới sinh ra đều phải lưu vào đây.
│
└── 📁 .claude/         <-- Ngăn kỹ thuật ngầm của riêng Claude (Chuẩn bị cho Buổi 5)
    ├── 📁 skills/     <-- Nơi cất giữ các kỹ năng quy trình tự động hóa
    └── 📁 agents/     <-- Nơi khai sinh các nhân viên AI chuyên vai
```

---

### 2.2. Thao tác thực hành: Nhờ Claude tự động dọn dẹp và phân loại thư mục (Prompt 2)

Thay vì phải dùng chuột tạo từng thư mục rồi kéo thả thủ công, bạn chỉ cần giao việc cho Claude bằng 1 câu lệnh ngắn gọn:

<details>
<summary><b>Thao tác thực hành: Dọn dẹp thư mục tự động</b> (bấm để mở)</summary>

**Gõ câu lệnh sau vào Claude Desktop:**

```markdown
Dọn dẹp lại thư mục này cho ngăn nắp giúp tôi với:
1. Tạo các thư mục con: 01_input, 02_templates, 03_output.
2. Tạo thêm thư mục .claude (bên trong .claude tạo sẵn 2 thư mục con là skills và agents để dành cho buổi sau).
3. Di chuyển các file hợp đồng thô, bảng kê chi phí và ghi chú cuộc họp vào 01_input.
4. Di chuyển file Mau_Bien_Ban_Nghiem_Thu_Chuan_NovaTech.docx vào 02_templates.
5. Di chuyển file biên bản nghiệm thu vừa tạo vào 03_output.
```

**Quan sát kết quả trên cây thư mục:**
- Chỉ sau vài giây, toàn bộ file đã được di chuyển gọn gàng vào đúng các ngăn:
  - `01_input/`: Chứa các file tài liệu thô.
  - `02_templates/`: Chứa file mẫu nghiệm thu chuẩn.
  - `03_output/`: Chứa file biên bản nghiệm thu đã hoàn thành.
  - `.claude/`: Đã có sẵn 2 thư mục `skills/` và `agents/` sẵn sàng cho Buổi 5!
</details>

---

## PHẦN 3. "BỘ NÃO NGỮ CẢNH" `CLAUDE.MD` - ĐƯA NỘI QUY CÔNG TY CHO AI

### 3.1. `CLAUDE.md` là gì? Cầu nối với Buổi 1
- **Hãy tưởng tượng:** Bạn vừa tuyển một cộng tác viên rất giỏi mới nhận việc sáng nay. Bạn chưa kịp nói gì đã bắt bạn ấy soạn hợp đồng hay biên bản ngay. Chắc chắn bạn ấy sẽ làm sai — không phải vì bạn ấy dở, mà vì **chưa ai đưa cho bạn ấy "tờ giấy giới thiệu công ty"**: công ty bán gì, làm việc theo quy tắc nào, file mẫu để ở đâu, từ ngữ nào cấm dùng.
- Claude trên máy tính lúc mới mở ra cũng y hệt như cộng tác viên đó: Nó rất thông minh, nhưng chưa biết gì về bạn và quy định của công ty bạn!
- **Tờ giấy giới thiệu ấy, trong Claude Code Desktop, chính là file `CLAUDE.md`:**
  - File này được đặt ngay tại thư mục gốc của dự án với tên chính xác là `CLAUDE.md`.
  - Mỗi khi bạn mở Claude Desktop tại thư mục này, **việc đầu tiên Claude làm luôn là đọc file `CLAUDE.md`** trước khi nhận bất kỳ câu lệnh nào từ bạn.

> [!NOTE]
> **Cầu nối với Buổi 1 (claude.ai):**
> Nếu bạn còn nhớ ở Buổi 1, mỗi lần tạo một Trợ lý trong mục **Projects** trên web, việc đầu tiên luôn là dán nội dung vào ô **Instructions** ở cột bên phải. Ô đó chính là bộ não của trợ lý.
> **File `CLAUDE.md` chính là ô Instructions đó!** Vai trò y hệt nhau, chỉ khác chỗ đặt:
> 
> | Buổi 1, trên Web (claude.ai) | Từ Buổi 4, trên Máy tính (Claude Code Desktop) |
> |---|---|
> | Ô **Instructions** trong Project | File **`CLAUDE.md`** nằm ngay tại thư mục gốc |
> | Kéo tài liệu vào ô **Project Knowledge** | Các file tài liệu để sẵn trong các ngăn thư mục |
> | Sửa bằng cách bấm biểu tượng cây bút gõ tay | Sửa bằng cách nhờ chính Claude viết lại |
> | Chỉ áp dụng trong đúng Project đó trên web | Tự động áp dụng cho mọi phiên làm việc mở tại thư mục đó |

- **Phép thử một câu (The One-Sentence Test):** Viết xong hồ sơ công ty trong `CLAUDE.md`, thử thay tên công ty của bạn bằng một tên doanh nghiệp bất kỳ. Nếu câu văn vẫn đúng, tức là nội dung còn chung chung. Một file `CLAUDE.md` chuẩn phải gắn chặt với công việc, sản phẩm và quy chuẩn riêng của chính bạn!

---

### 3.2. Giải phẫu cấu trúc 1 file `CLAUDE.md` chuẩn công sở

Một file `CLAUDE.md` văn phòng thường ngắn gọn dưới 80 dòng, gồm 4 phần chính:
1. **Vai trò & Bối cảnh:** Bạn là ai trong thư mục này? (Ví dụ: Trợ lý Quản trị Hồ sơ Dự án NovaTech).
2. **Quy định phân luồng thư mục:** Đọc dữ liệu ở đâu, lấy mẫu ở đâu, xuất kết quả vào đâu.
3. **Quy tắc đặt tên file bắt buộc:** `[YYYYMMDD]_[TenDoiTac]_[LoaiVanBan].docx`.
4. **Quy chuẩn định dạng & Điều cấm kỵ:** Font chữ, định dạng số tiền (VNĐ), cấm xóa hoặc sửa file gốc trong `01_input/`.

---

### 3.3. Thao tác thực hành: Tạo file `CLAUDE.md` cho dự án

Bạn có thể lựa chọn 1 trong 2 cách dưới đây tùy theo nhu cầu học tập:

<details>
<summary><b>LỰA CHỌN A: Tạo nhanh theo case study NovaTech của lớp (Prompt 3A)</b> (bấm để mở)</summary>

**Gõ câu lệnh sau vào Claude Desktop:**

```markdown
Tạo cho tôi 1 file CLAUDE.md ngay tại thư mục gốc này để làm bản hướng dẫn làm việc cho bạn mỗi khi tôi mở thư mục lên nhé:

- Bạn là Trợ lý Quản trị Hồ sơ Dự án của công ty NovaTech.
- Quy định về thư mục:
  + Tài liệu khách hàng gửi hoặc dữ liệu thô luôn nằm ở 01_input (chỉ đọc, tuyệt đối không sửa hay xóa).
  + Khi cần lập văn bản mới, luôn lấy mẫu chuẩn từ thư mục 02_templates.
  + Mọi văn bản hoàn thiện sau khi xử lý phải lưu vào thư mục 03_output.
- Quy tắc đặt tên file xuất ra:
  Bắt buộc theo định dạng: [YYYYMMDD]_[TenDoiTac]_[LoaiVanBan].docx
  (Ví dụ: 20260322_DetMayNamDinh_BienBanNghiemThu.docx).
- Quy chuẩn nội dung: Dùng tiếng Việt chuẩn công sở, số tiền phải có dấu chấm phân cách hàng nghìn (VNĐ) và có dòng ghi số tiền bằng chữ.
```
</details>

<details>
<summary><b>LỰA CHỌN B: Để Claude "phỏng vấn" và tự viết cho công việc thật của bạn (Prompt 3B)</b> (bấm để mở)</summary>

*Nếu bạn đang thực hành trên thư mục công việc thật của mình và chưa biết viết gì vào `CLAUDE.md`, hãy để Claude phỏng vấn bạn từng câu một:*

**Gõ câu lệnh sau vào Claude Desktop:**

```markdown
Tôi muốn bạn tạo cho tôi một file CLAUDE.md đặt ngay tại thư mục gốc này để làm hồ sơ bạn đọc trước mọi việc tôi giao.

Trước khi viết, hãy phỏng vấn tôi. Hỏi từng câu một, chờ tôi trả lời xong câu này rồi mới hỏi câu tiếp theo:
1. Tôi là ai, làm việc ở công ty nào, phòng ban gì?
2. Ba công việc chính tôi thường làm lặp đi lặp lại trong thư mục này là gì?
3. Quy định về nơi lấy file dữ liệu, nơi lấy biểu mẫu và nơi lưu kết quả của tôi ra sao?
4. Quy tắc đặt tên file và quy chuẩn văn phong (xưng hô, từ ngữ cấm kỵ, định dạng)?

Hỏi xong 4 câu, hãy tóm tắt lại cho tôi xác nhận, tôi đồng ý rồi bạn mới viết file CLAUDE.md ngắn gọn dưới 80 dòng nhé.
```
👉 Claude sẽ lần lượt hỏi bạn 4 câu rất nhẹ nhàng, bạn chỉ cần trả lời bằng ngôn ngữ đời thường, Claude sẽ tự tổng hợp và viết ra file `CLAUDE.md` may đo chuẩn chỉnh cho riêng bạn!
</details>

---

### 3.4. Dán "Sơ đồ các phòng" vào `CLAUDE.md` (Mục lục thư mục)

Sau khi chia các phòng (`01_input`, `02_templates`, `03_output`), nếu bạn không chỉ rõ thì mỗi lần cần tìm file, Claude vẫn phải đi mở từng phòng để lục lọi. 
Cách chuẩn nhất là **dán sơ đồ chỉ dẫn các phòng ngay ở cửa ra vào** (chính là ghi mục lục vào `CLAUDE.md`):

<details>
<summary><b>Thao tác thực hành: Cập nhật sơ đồ thư mục vào CLAUDE.md</b> (bấm để mở)</summary>

**Gõ câu lệnh sau vào Claude Desktop:**

```markdown
Quét lại các thư mục vừa tạo (01_input, 02_templates, 03_output, .claude). Sau đó cập nhật vào file CLAUDE.md một mục tên là "Cấu trúc thư mục", ghi rõ mỗi thư mục một dòng kèm chức năng của nó để bạn luôn biết đường vào đúng phòng lấy và lưu file nhé.
```

**Kết quả:** File `CLAUDE.md` được bổ sung thêm một bảng mục lục ngắn gọn, giúp Claude định vị đường đi tức thì trong 1 giây mà không bao giờ mở nhầm phòng!
</details>

---

### 3.5. Kiểm tra phản xạ định vị của Claude

Trước khi giao việc lớn, hãy thử kiểm tra xem Claude đã thực sự nạp "bản đồ và nội quy" chưa bằng 1 câu hỏi phản xạ:

<details>
<summary><b>Thao tác thực hành: Kiểm tra phản xạ định vị</b> (bấm để mở)</summary>

**Gõ câu hỏi sau vào Claude Desktop:**

```markdown
Nếu bây giờ tôi giao cho bạn một hợp đồng mới toanh của khách hàng, bạn sẽ lấy dữ liệu ở đâu, lấy mẫu ở đâu và xuất file vào thư mục nào, đặt tên file ra sao?
```

**Quan sát câu trả lời:**
Claude sẽ trả lời rành mạch:
- Lấy dữ liệu hợp đồng khách hàng tại: `01_input/`.
- Lấy mẫu biểu nghiệm thu chuẩn tại: `02_templates/`.
- Xuất file hoàn thiện vào: `03_output/`.
- Đặt tên file theo định dạng: `[YYYYMMDD]_[TenDoiTac]_[LoaiVanBan].docx`.
</details>

---

### 3.6. Thao tác kiểm chứng thực chiến: Xử lý hồ sơ mới bằng 1 câu lệnh ngắn (Prompt 4)

Bây giờ là lúc bạn chứng kiến sự tự động hóa kỳ diệu! Trong thư mục `01_input/` hiện có sẵn file hợp đồng thứ hai: `hop_dong_phan_mem_an_phu_chua_ky.docx` (của Tập đoàn Bất động sản An Phú).

Bạn **không cần** phải dặn lại: *"Lấy mẫu ở đâu, lưu vào đâu, đặt tên thế nào..."*. Hãy chỉ gõ đúng 1 câu nói tự nhiên như với đồng nghiệp:

<details>
<summary><b>Thao tác thực hành: Kiểm chứng tự động hóa theo nội quy</b> (bấm để mở)</summary>

**Gõ câu lệnh ngắn gọn này vào Claude:**

```markdown
Xử lý tiếp hợp đồng của công ty An Phú trong thư mục 01_input giúp tôi, tạo biên bản nghiệm thu tương ứng nhé.
```

**Quan sát phản xạ của Claude:**
1. Claude tự động đọc `CLAUDE.md` để nắm quy tắc.
2. Tự động vào `01_input/` mở file hợp đồng An Phú để bóc tách: *Gói NovaEnterprise Suite, 100 user, trị giá 120.000.000 VNĐ, đại diện là ông Vũ Hoàng Quân (CIO)*.
3. Tự động vào `02_templates/` lấy file `Mau_Bien_Ban_Nghiem_Thu_Chuan_NovaTech.docx`.
4. Điền toàn bộ thông tin chính xác 100%.
5. **Tự động lưu vào đúng thư mục `03_output/`** với tên file chuẩn xác:  
   `03_output/20260322_AnPhu_BienBanNghiemThu.docx`.
6. File gốc trong `01_input/` và file mẫu trong `02_templates/` hoàn toàn nguyên vẹn, không bị xáo trộn!
</details>

---

## PHẦN 4. NGHIỆM THU BUỔI 4, CHIA SẺ & BƯỚC NGOẶT SANG BUỔI 5

### 4.1. Nghiệm thu Buổi 4: Danh mục kiểm tra thành phẩm

Hãy tự kiểm tra lại các sản phẩm bạn đã tạo ra trên máy tính trước khi rời lớp:

#### Về hiểu biết bản chất:
- [ ] Hiểu rõ sự khác biệt giữa **Claude trên Web** (hộp cát dữ liệu) và **Claude Code Desktop** (cộng sự làm việc trực tiếp trên ổ cứng máy tính).
- [ ] Nắm được cách xem cây thư mục, xem trước file và sử dụng **Built-in Browser** để preview kết quả.
- [ ] Hiểu cơ chế xin quyền an toàn (*Allow / Approve*) để bảo vệ dữ liệu công ty.
- [ ] Thấu hiểu nỗi đau khi làm việc lộn xộn và lý do vì sao phải áp dụng quy tắc "5S" cho dữ liệu.
- [ ] Hiểu rõ vai trò của file `CLAUDE.md` như một bản nội quy tự động.

#### Về sản phẩm thực tế trên máy:
- [ ] **Sản phẩm 1:** 01 Cây thư mục dự án chuẩn hóa 3 ngăn (`01_input`, `02_templates`, `03_output`).
- [ ] **Sản phẩm 2:** Khởi tạo sẵn thư mục ngầm `.claude/` (với 2 thư mục con `skills/` và `agents/`).
- [ ] **Sản phẩm 3:** 01 file `CLAUDE.md` hoàn chỉnh đóng vai trò "Bộ não ngữ cảnh" cho toàn bộ thư mục.
- [ ] **Sản phẩm 4:** 02 Biên bản nghiệm thu dự án Word chuẩn chỉ (`DetMayNamDinh` và `AnPhu`) nằm ngay ngắn trong thư mục `03_output/`.

---

### 4.2. Cầu nối sang Buổi 5: Đóng gói Skill & Phân vai Agent trong thư mục `.claude/`

- **Thành tựu hôm nay:** Bạn đã xây dựng xong một "ngôi nhà" ngăn nắp và ban hành một "bản nội quy" `CLAUDE.md` hoàn hảo. Claude đã biết tự động đọc, sửa và lưu file đúng quy chuẩn.
- **Vấn đề tiếp theo cần giải quyết:**
  - Hiện tại, mỗi lần muốn xử lý một hợp đồng hay làm báo cáo, bạn vẫn phải gõ câu lệnh mô tả công việc.
  - Nếu quy trình nghiệm thu hay bóc tách báo giá của phòng ban bạn gồm **5-7 bước phức tạp lặp đi lặp lại hàng tuần**, làm sao để bạn chỉ cần gõ một lệnh tắt duy nhất (ví dụ: `/nghiem-thu`) là AI tự động chạy từ A đến Z?
  - Làm sao để tạo ra nhiều "nhân viên AI chuyên trách" (1 bạn chuyên soát lỗi pháp lý hợp đồng, 1 bạn chuyên kiểm tra số liệu kế toán) cùng phối hợp làm việc trong thư mục này?
- 👉 **Hẹn gặp lại ở Buổi 5: Mở cánh cửa thư mục `.claude/` — Đóng gói kỹ năng thành SKILL và nhân bản trợ lý thành AGENT chuyên vai!**
