# Buổi 6: Làm video giới thiệu và landing page doanh nghiệp bằng Claude

> **Thời lượng:** 150 phút (2.5 giờ) | **Môi trường:** Claude Code Desktop (Local) + trình duyệt tích hợp / Claude in Chrome  
> **Mô hình buổi học:** HANDS-ON THỰC CHIẾN.  
> **Trình tự:** Lý thuyết bản chất (máy làm ra sản phẩm như thế nào) -> Thực hành từng bước song song (Giảng viên & Học viên).  
> **Xưng hô trong bài:** Giảng viên xưng **"em"**, gọi học viên là **"anh chị"**.  
> **Cách dùng file này:** Mỗi phần có khúc **Lý thuyết** giải thích bản chất và khúc **Thao tác** có sẵn câu lệnh trong các thẻ `<details>`, anh chị bấm mở, copy dán vào Claude Code. Làm tuần tự, không nhảy cóc!

**Sản phẩm cầm về:** 01 video 45 giây giới thiệu công ty (giọng đọc AI, nhạc, hiệu ứng âm thanh) + 01 landing page chạy trên Vercel, có form đăng ký tự đổ dữ liệu khách hàng về Google Sheets.

---

## Nhịp buổi học (150 phút)

| Phần | Nội dung trọng tâm | Thời lượng | Dạng bài | Thao tác |
|:---:|---|:---:|:---:|---|
| **A** | **Làm video giới thiệu công ty bằng code:**<br>- Video là chuỗi khung hình, fps.<br>- Hai cách AI làm video: mô hình sinh video vs làm phim bằng code.<br>- Quy trình render: Chrome headless chụp từng khung hình, FFmpeg ghép video.<br>- Âm thanh: giọng đọc AI Studio, nhạc, hiệu ứng. | 70 phút | LT 20'<br>HV 50' | Kiểm tra repo Lemo-Opuscar -> cài skill cấp project -> giao việc làm video 45 giây giới thiệu CES Global. |
| | **Nghỉ giải lao & Hỗ trợ kỹ thuật** | 10 phút | Giải lao | Video render chạy nền trong lúc nghỉ. |
| **B** | **Landing page, Vercel và form về Google Sheets:**<br>- Cấu trúc một landing page.<br>- Research thiết kế trên Dribbble, Pinterest; tone màu theo ngành.<br>- Vercel: đưa website lên mạng.<br>- Apps Script nhận form, ghi vào Google Sheets. | 60 phút | LT 15'<br>HV 45' | Research + dựng landing page -> đẩy lên Vercel -> nối form đăng ký về Google Sheets. |
| **C** | **Nghiệm thu & tổng kết khóa học** | 10 phút | Đúc kết | Checklist sản phẩm + nhìn lại hành trình 6 buổi. |

---

## PHẦN A. LÀM VIDEO GIỚI THIỆU CÔNG TY BẰNG CODE

### A.1. Lý thuyết: Video thực chất là gì trong mắt máy tính?

- Video là **một chuỗi ảnh tĩnh (khung hình, frame)** hiện lên thật nhanh nối tiếp nhau. Mắt người thấy liền mạch khi tốc độ đủ cao, đo bằng **fps** (frames per second - số khung hình mỗi giây).
- Phim điện ảnh thường chạy **24 fps**; video mạng xã hội hay dùng **24-30 fps**.
- Một video **45 giây ở 24 fps** gồm **45 x 24 = 1.080 khung hình**. Ở 30 fps là 1.350 khung hình.
- Âm thanh (giọng đọc, nhạc, hiệu ứng) là một **dải riêng**, được ghép khớp với hình theo dòng thời gian.

> [!NOTE]
> **Ví von dễ nhớ:** Video giống **cuốn sách lật (flipbook)**: mỗi trang là một bức vẽ hơi khác trang trước, lật nhanh thì hình chuyển động. Làm video bằng code chính là nhờ Claude "vẽ" đúng từng trang, rồi đóng lại thành cuốn.

### A.2. Lý thuyết: Hai cách AI làm video

| | Cách 1 - Mô hình sinh video | Cách 2 - Làm phim bằng code (bài hôm nay) |
|---|---|---|
| **Cách làm** | Gõ mô tả, mô hình AI tự "vẽ" ra cả đoạn video (các công cụ dạng Veo, Sora, Kling...). | Claude viết một trang web hoạt hình, rồi "chụp" từng khung hình thành video. |
| **Mạnh** | Cảnh quay giống thật: người, phong cảnh. | Chữ, logo, số liệu, màu sắc **chính xác tuyệt đối**; sửa chỗ nào là sửa đúng chỗ đó. |
| **Yếu** | Khó kiểm soát chữ, logo, màu thương hiệu; sửa 1 chi tiết thường phải tạo lại cả đoạn. | Không làm được cảnh quay người thật. |
| **Hợp cho** | Cảnh minh họa, cảnh đời thường. | Video giới thiệu công ty, motion graphics, video số liệu, video bài giảng. |

Bộ skill dùng trong bài là **Lemo-Opuscar** (`lemomo-ai/lemo-opuscar` trên GitHub): mã nguồn mở giấy phép MIT (video mẫu theo CC BY 4.0), khoảng 12 nghìn sao. Tác giả ghi rõ: phim làm hoàn toàn bằng code, **không dùng mô hình sinh video, không dùng cảnh quay có sẵn**, kèm hơn 60 phong cách phim dựng sẵn.

### A.3. Lý thuyết: Quy trình render - Chrome chạy ngầm chụp từng khung hình

```text
[1. Kịch bản & timeline]   Claude đọc tư liệu, viết lời thoại, chia cảnh,
          |                chốt giây nào hiện gì, nhạc dồn ở đâu.
          v
[2. Trang web hoạt hình]   Hàm render(t): mỗi thời điểm t vẽ ra đúng 1 khung hình
          |                (Canvas 2D, three.js cho 3D, shader WebGL).
          v
[3. Chrome headless]       Trình duyệt chạy ngầm gọi render(t) lần lượt
          |                cho từng khung, chụp lại thành ảnh.
          v
[4. FFmpeg]                Nối hàng nghìn ảnh thành MP4, trộn giọng đọc,
          |                nhạc, hiệu ứng, cân âm lượng.
          v
[5. Kiểm tra & xuất bản]   Xem bảng ảnh tóm tắt các cảnh, soát phụ đề,
                           nghe lại âm thanh, sửa rồi render lại.
```

- **Chrome headless** là trình duyệt Chrome chạy ngầm, không hiện cửa sổ. Máy dùng nó để "mở" trang hoạt hình và chụp ảnh tự động, nhanh và không cần người bấm. Lemo-Opuscar có thể chạy nhiều trình duyệt cùng lúc (mỗi "luồng" một trình duyệt) để render nhanh hơn.
- **Vì sao phải "hàm theo thời gian"?** Cùng một `t` luôn ra cùng một hình (tính tất định - không dùng giờ hệ thống, không dùng số ngẫu nhiên tùy hứng). Nhờ vậy có thể chia nhiều luồng render song song mà video không bị giật, và render lại bao nhiêu lần cũng giống hệt nhau. Đây cũng là nguyên lý của các công cụ làm video bằng code khác như Remotion.
- **Timeline là "nguồn sự thật duy nhất":** mọi cảnh, nhịp nhạc, điểm nhấn hình đều khai báo trong một file dòng thời gian, nên hình và tiếng luôn khớp nhau.
- **FFmpeg** là công cụ mã nguồn mở xử lý video và âm thanh, gần như mọi phần mềm dựng phim đều dùng. Ở bước cuối, âm thanh được chuẩn hóa về khoảng **-14 LUFS** (đơn vị đo độ to cảm nhận), mức to nhỏ phổ biến của các nền tảng video trực tuyến, kèm giới hạn đỉnh để không bị rè.

### A.4. Lý thuyết: Âm thanh - giọng đọc AI Studio, nhạc và hiệu ứng

1. **Giọng đọc bằng Google AI Studio:** AI Studio có trang tạo giọng nói (Generate speech) dùng mô hình Gemini TTS (chuyển văn bản thành giọng nói). Chọn một trong khoảng 30 giọng có sẵn (nam, nữ), rồi **mô tả cách đọc bằng lời**, ví dụ "đọc nhanh nhẹn, hào hứng, như quảng cáo"; có thể chỉnh tốc độ, phong cách, tối đa 2 người đọc; sau đó tải file âm thanh WAV. Bài này Claude tự mở AI Studio trong **trình duyệt tích hợp** để làm thay, chỉ dừng lại khi cần anh chị đăng nhập.
2. **Nhạc nền và hiệu ứng âm thanh:** bộ skill tự soạn nhạc từ thư viện nhạc cụ mẫu và tự tổng hợp hiệu ứng (tiếng vút, tiếng chạm...). Mỗi hiệu ứng được gắn với đúng khung hình trên timeline, nên chữ hiện ra là tiếng "tách" vang lên đúng lúc.
3. **Trộn âm:** giọng đọc luôn nổi hơn nhạc (nhạc tự hạ xuống khi có lời), phụ đề được xuất kèm để xem không cần bật tiếng. Bộ skill còn tự nghe lại giọng đọc bằng công cụ nhận dạng giọng nói để bắt lỗi đọc sai.

> [!TIP]
> Mặc định Lemo-Opuscar dùng giọng đọc chạy trên máy (không cần API key). Bài hôm nay chủ động đổi sang AI Studio để có giọng tiếng Việt tự nhiên hơn và để luyện thêm kỹ năng cho Claude tự thao tác trên trình duyệt.

### A.5. Thực hành: Kiểm tra, cài skill và làm video 45 giây

**Bước 1: Cho Claude kiểm tra repo trước khi cài.** Mở link repo để xem trang giới thiệu và video mẫu, sau đó giao Claude kiểm tra.

<details>
<summary><b>Thao tác thực hành: Link repo bộ skill làm video</b> (bấm để mở)</summary>

```text
https://github.com/lemomo-ai/lemo-opuscar
```

</details>

<details>
<summary><b>Thao tác thực hành: Kiểm tra độ an toàn của repo</b> (bấm để mở)</summary>

```text
https://github.com/lemomo-ai/lemo-opuscar
repo này là gì? có an toàn để dùng ko, có mã độc gì ko? cách cài đặt như thế nào
```

**Quan sát:** Claude đọc repo và báo lại: công cụ làm gì, giấy phép, mức độ phổ biến, các script sẽ chạy khi cài, cần cài thêm gì. Thói quen tốt đã học ở Buổi 4: **luôn kiểm tra trước khi cài**.

</details>

**Bước 2: Cài bộ skill vào thư mục skill cấp project.**

<details>
<summary><b>Thao tác thực hành: Cài skill cấp project</b> (bấm để mở)</summary>

```text
cài bộ skill này cho tôi nhé. Đặt tại thư mục skill cấp project
```

**Quan sát:** Claude chép bộ skill vào thư mục `.claude/skills/` của dự án (cấp project, như Buổi 5), rồi cài các công cụ đi kèm: Node.js, FFmpeg, Python, trình duyệt chạy ngầm. Khi Claude xin phép chạy lệnh, đọc qua rồi bấm cho phép.

</details>

**Bước 3: Giao việc làm video 45 giây.**

<details>
<summary><b>Thao tác thực hành: Làm video giới thiệu CES Global</b> (bấm để mở)</summary>

```text
https://cesglobal.com.vn/
đọc nội dung trong link này, dựa vào đây tự viết kịch bản và làm cho tôi video 45 giây giới thiệu về CES Global. Có giọng đọc, sound effect, nhạc,... sao cho thu hút. Phần voice thì bạn sẽ dùng AI Studio để tạo voice cho tôi. Bạn cũng sẽ tự mở trình duyệt tích hợp sẵn để tự động thao tác tạo voice cho tôi. Nếu cần đăng nhập thì dừng lại hướng dẫn tôi. Dùng giọng đọc nam, sao cho phù hợp, nhanh nhẹn, thu hút
```

**Diễn biến:**
1. Claude đọc website, viết kịch bản 45 giây và chọn phong cách phim phù hợp.
2. Claude mở AI Studio trong trình duyệt tích hợp. Nếu chưa đăng nhập Google, Claude dừng lại: **anh chị tự đăng nhập**, rồi bảo Claude làm tiếp.
3. Claude tạo giọng nam, tải file giọng đọc về, soạn nhạc, hiệu ứng, render từng khung hình và ghép thành file MP4.
4. Xem video. Muốn sửa thì nói cụ thể như với người dựng phim: *"cảnh logo kéo dài thêm 2 giây"*, *"nhạc nhỏ lại một chút"*.

</details>

> [!WARNING]
> **Cần biết trước khi làm:**
> - **Thời gian và chi phí:** theo tác giả, một video mất khoảng 30-60 phút và khá nhiều lượt dùng Claude. Nên làm khi máy rảnh, cắm sạc.
> - **Cấu hình máy:** cần Node.js 20 trở lên, FFmpeg 7 trở lên, Python 3.11 trở lên; bộ công cụ tải về vài trăm MB. Tác giả khuyên dùng WSL trên Windows; các phong cách 3D cần máy có card đồ họa.
> - **Bản quyền:** mã nguồn bộ skill theo giấy phép MIT; video anh chị làm ra thuộc về anh chị. Nội dung website đưa vào video phải là của công ty mình hoặc được phép dùng.

---

## PHẦN B. LÀM LANDING PAGE, ĐƯA LÊN VERCEL VÀ THU THẬP KHÁCH HÀNG VỀ GOOGLE SHEETS

### B.1. Lý thuyết: Landing page là gì và gồm những phần nào?

**Landing page** (trang đích) là một trang web **chỉ phục vụ một mục tiêu**, thường là để khách để lại thông tin hoặc mua hàng. Một landing page tốt thường có:

1. **Phần đầu trang (hero):** tiêu đề nói rõ lợi ích, 1 câu mô tả, 1 nút kêu gọi hành động (CTA) nổi bật.
2. **Dịch vụ, lợi ích:** khách nhận được gì, khác đối thủ ở đâu.
3. **Bằng chứng tin cậy:** khách hàng tiêu biểu, con số, đánh giá, hình ảnh thật.
4. **Câu hỏi thường gặp:** trả lời trước các băn khoăn của khách.
5. **Form đăng ký:** ngắn gọn, chỉ hỏi thông tin thật sự cần (họ tên, số điện thoại, email, nhu cầu).

### B.2. Lý thuyết: Research thiết kế trên các trang design lớn

<details>
<summary><b>Thao tác thực hành: Link tham khảo thiết kế</b> (bấm để mở)</summary>

```text
Các trang lớn về design để tham khảo:
https://dribbble.com/search/landing-page
https://www.pinterest.com/
```

</details>

- **Dribbble:** nơi các nhà thiết kế đăng mẫu giao diện. Tìm "landing page" kèm ngành của mình.
- **Pinterest:** gom ảnh tham khảo thành bảng ý tưởng (moodboard) về màu sắc, bố cục, phong cách.
- **Chụp lại 1 mẫu ưng ý** để gửi kèm câu lệnh: Claude nhìn ảnh sẽ bắt đúng phong cách nhanh hơn nhiều so với mô tả bằng lời.

| Ngành | Tone màu thường gặp | Cảm giác mang lại |
|---|---|---|
| Tài chính, kế toán, luật | Xanh navy, xám, trắng | Tin cậy, chắc chắn |
| Y tế, giáo dục | Xanh dương nhạt, xanh lá, trắng | Sạch sẽ, an tâm |
| Ăn uống, bán lẻ | Cam, đỏ, vàng | Kích thích, năng động |
| Cao cấp, bất động sản | Đen, vàng đồng, kem | Sang trọng, đẳng cấp |
| Công nghệ | Xanh tím, gradient, nền tối | Hiện đại, sáng tạo |

> [!TIP]
> **Tham khảo, không sao chép:** mẫu trên Dribbble, Pinterest là tác phẩm của người khác. Lấy cảm hứng về bố cục, màu, phong cách; nội dung, hình ảnh, logo phải là của công ty mình. Màu chủ đạo nên bám theo màu logo, như đã làm với Skill ở Buổi 5.

### B.3. Thực hành: Dựng landing page

Thay `...` bằng chủ đề, ngành của công ty; **gửi kèm ảnh mẫu** đã chọn ở B.2.

<details>
<summary><b>Thao tác thực hành: Research và dựng landing page</b> (bấm để mở)</summary>

```text
Hiện tại tôi cần làm 1 website cho công tôi về chủ đề ... Tôi cần bạn research thêm các mẫu trong cùng ngành xem style và tone màu nên sử dụng như thế nào. Hãy hỏi lại tôi để chắc chắn bạn làm đúng ý tôi. Có thể research các mẫu hiện đại, sang trọng trên các trang web lớn như dribbble, pinterest,...
Đây là cái mẫu tôi thấy phù hợp
```

**Diễn biến:**
1. Claude research các mẫu cùng ngành và **hỏi lại**: tên công ty, đối tượng khách hàng, mục tiêu trang, màu thương hiệu, nội dung các phần. Trả lời càng cụ thể, trang càng đúng ý.
2. Claude đề xuất phong cách, tone màu, bố cục, rồi dựng trang và mở cho anh chị xem trong trình duyệt.
3. Góp ý chỉnh sửa như với nhà thiết kế cho tới khi "tạm ổn" thì sang bước đưa lên mạng.

</details>

### B.4. Lý thuyết + Thực hành: Đưa website lên mạng bằng Vercel

- **Vercel** là dịch vụ lưu trữ và đưa website lên mạng. Website được phân phối qua mạng máy chủ khắp thế giới (CDN) nên tải nhanh ở mọi nơi.
- Mỗi lần đưa lên (deploy) có một link riêng để xem thử, còn link chính (production) luôn trỏ tới bản mới nhất; có thể gắn tên miền riêng của công ty.

<details>
<summary><b>Thao tác thực hành: Link Vercel (tạo tài khoản trước nếu chưa có)</b> (bấm để mở)</summary>

```text
https://vercel.com/
```

</details>

<details>
<summary><b>Thao tác thực hành: Đẩy website lên Vercel</b> (bấm để mở)</summary>

```text
tôi thấy tạm ổn, bây giờ hãy đẩy lên vercel cho tôi, tôi đã có tài khoản vercel rồi, bạn hãy tự cài đặt thêm nếu cần và tự chạy lệnh cho tôi, nếu cần tôi đăng nhập hoặc làm gì thì hướng dẫn tôi
```

**Diễn biến:**
1. Claude cài công cụ dòng lệnh của Vercel nếu máy chưa có.
2. Lần đầu, Vercel mở trình duyệt để đăng nhập: **anh chị tự đăng nhập** tài khoản Vercel.
3. Claude đưa website lên và gửi lại link. Mở link trên điện thoại để kiểm tra giao diện.

</details>

> [!WARNING]
> **Gói miễn phí của Vercel chỉ cho mục đích cá nhân:** theo điều khoản của Vercel, gói Hobby (miễn phí) chỉ dùng cho mục đích **cá nhân, phi thương mại**. Website chính thức của công ty là mục đích thương mại, cần nâng lên gói Pro. Gói miễn phí vẫn phù hợp để học và làm bản thử.

### B.5. Form đăng ký tự đổ dữ liệu về Google Sheets bằng Apps Script

**Lý thuyết:** Website trên Vercel chỉ là "mặt tiền", không tự lưu được dữ liệu. Ta dùng **Apps Script** (đã gặp ở Buổi 3) làm "người nhận hồ sơ" ghi thẳng vào Google Sheets:

```text
[Khách bấm Đăng ký trên landing page]
        -> [Link web app Apps Script nhận dữ liệu gửi tới]
        -> [Google Sheets thêm 1 dòng kèm thời gian]
```

<details>
<summary><b>Thao tác thực hành: Form đăng ký đổ về Google Sheets</b> (bấm để mở)</summary>

```text
Ở mục đăng ký, tôi cần thu thập thông tin khách hàng khi khách hàng để lại thông tin. Bạn hãy dùng Apps Script để tự động đổ data đó về gg sheet khi khách hàng bấm đăng ký trên web. Bạn hãy dùng Claude in Chrome/ trình duyệt tích hợp sẵn (anh chị chọn 1 trong 2 khi gửi prompt) để tự thao tác cho tôi nhé. Cần đăng nhập gì thì tôi sẽ làm.
```

**Diễn biến:**
1. Claude tạo file Google Sheets nhận dữ liệu, mở Apps Script, viết đoạn code nhận form, lưu và **triển khai thành ứng dụng web**.
2. Tới bước cấp quyền, **anh chị tự bấm** cho phép.
3. Claude gắn link web app vào form trên website rồi đưa lại lên Vercel.
4. Thử đăng ký trên website thật: Google Sheets có thêm 1 dòng thông tin vừa nhập.

</details>

> [!NOTE]
> **Vì sao lần này chọn "Anyone" mà vẫn an toàn?** Ở Buổi 3, web app quản trị phải giới hạn người mở vì nó **xem và sửa** toàn bộ dữ liệu. Còn ở đây, khách vào website không đăng nhập Google, nên web app nhận form **bắt buộc** để "Anyone"; bù lại đoạn code chỉ làm đúng một việc là **ghi thêm dòng mới**, không cho xem hay sửa dữ liệu cũ.
>
> Thông tin khách để lại là dữ liệu cá nhân: nên có dòng đồng ý thu thập thông tin trên form, chỉ dùng đúng mục đích và không chia sẻ file Sheets ra ngoài. Mỗi lần sửa code Apps Script, nhớ **triển khai phiên bản mới** thì thay đổi mới có hiệu lực.

---

## PHẦN C. NGHIỆM THU BUỔI 6 & TỔNG KẾT KHÓA HỌC

### C.1. Nghiệm thu Buổi 6

#### Về hiểu biết bản chất:
- [ ] Giải thích được video là chuỗi khung hình, và cách Chrome headless chụp từng khung rồi FFmpeg ghép thành video.
- [ ] Phân biệt mô hình sinh video và làm phim bằng code, biết khi nào dùng cách nào.
- [ ] Nắm các phần của một landing page và cách research thiết kế, tone màu theo ngành.
- [ ] Hiểu luồng form: website gửi dữ liệu, Apps Script nhận, Google Sheets lưu; biết vì sao web app nhận form để "Anyone".

#### Về sản phẩm mang về:
- [ ] **Sản phẩm 1:** 01 video 45 giây giới thiệu công ty có giọng đọc AI, nhạc, hiệu ứng âm thanh.
- [ ] **Sản phẩm 2:** 01 landing page đúng phong cách, tone màu thương hiệu, đã chạy trên Vercel.
- [ ] **Sản phẩm 3:** Form đăng ký trên website đổ dữ liệu về Google Sheets, đã thử đăng ký thành công.

### C.2. Nhìn lại hành trình 6 buổi

- **Buổi 1-2:** trợ lý Claude hiểu công việc của mình, và công cụ tương tác bằng Artifacts.
- **Buổi 3:** kết nối dữ liệu thật (Gmail, Drive, Sheets), dashboard và web app quản lý.
- **Buổi 4-5:** Claude làm việc trên máy tính, CLAUDE.md, Skill và Agent chuyên vai.
- **Buổi 6:** tự làm sản phẩm truyền thông: video giới thiệu và landing page thu khách hàng.

Từ đây, mỗi việc lặp lại trong công việc đều có thể giao cho Claude: dặn rõ, duyệt kỹ, và đóng gói thành Skill để dùng mãi.

---

## Nguồn tham khảo (cho giảng viên)

- Lemo-Opuscar (README, TECHNIQUE.md, SKILL.md): https://github.com/lemomo-ai/lemo-opuscar
- Google AI Studio - Generate speech (Gemini TTS): https://aistudio.google.com/generate-speech
- Gemini TTS cookbook: https://fallendeity.github.io/gemini-ts-cookbook/quickstarts/Get_started_TTS.html
- Hướng dẫn AI Studio text-to-speech: https://www.plus2net.com/articles/ai-text-to-speech.php
- Vercel Hobby plan: https://vercel.com/docs/plans/hobby
- Vercel Fair Use Guidelines: https://vercel.com/docs/limits/fair-use-guidelines
- Vercel Terms: https://vercel.com/terms
