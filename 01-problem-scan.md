---
noteId: "aa39ba60dbf011f1b01855b9461dd099"
tags: []

---
Vương Quang Thắng
Phase 1 (SCAN):

5 Pain Point cho Vinmec:

┌───┬────────────┬────────────────────┬────────────────────────────────────────┐
│ # │ Subsidiary │ Lens               │ Mô tả ngắn bài toán                    │
├───┼────────────┼────────────────────┼────────────────────────────────────────┤
│ 1 │ Vinmec     │ Tốn thời gian      │ Bác sĩ tiêu tốn 20-30 phút mỗi ca để   │
│   │            │                    │ trích xuất dữ liệu bệnh án và soạn     │
│   │            │                    │ thảo tóm tắt hồ sơ xuất viện.          │
├───┼────────────┼────────────────────┼────────────────────────────────────────┤
│ 2 │ Vinmec     │ Pain từ người khác │ Tổng đài viên và bệnh nhân thường      │
│   │            │                    │ xuyên phân loại sai chuyên khoa khám   │
│   │            │                    │ dựa trên triệu chứng ban đầu, gây      │
│   │            │                    │ lãng phí slot khám.                    │
├───┼────────────┼────────────────────┼────────────────────────────────────────┤
│ 3 │ Vinmec     │ Lặp lại            │ Nhân viên thu ngân phải rà soát thủ    │
│   │            │                    │ công mã bệnh (ICD-10) và đối chiếu     │
│   │            │                    │ chéo với các điều khoản loại trừ       │
│   │            │                    │ bảo hiểm lặp đi lặp lại mỗi ngày.      │
├───┼────────────┼────────────────────┼────────────────────────────────────────┤
│ 4 │ Vinmec     │ Tốn thời gian      │ Điều dưỡng viên gọi điện thoại thủ     │
│   │            │                    │ công cho từng bệnh nhân để nhắc nhở    │
│   │            │                    │ lịch uống thuốc và theo dõi biến       │
│   │            │                    │ chứng sau xuất viện.                   │
├───┼────────────┼────────────────────┼────────────────────────────────────────┤
│ 5 │ Vinmec     │ AI có thể tốt hơn  │ Khách hàng khó hiểu các thuật ngữ y    │
│   │            │                    │ khoa phức tạp trên kết quả chẩn đoán   │
│   │            │                    │ hình ảnh, khiến bác sĩ phải mất thêm   │
│   │            │                    │ thời gian giải thích trong phiên khám. │
└───┴────────────┴────────────────────┴────────────────────────────────────────┘



########################################################

Phase 2 (QUICK-ASSESS):

3 QUICSK PROBLEM CARD:
1.
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1 (Ambient Scribe Phòng Mổ)             │
│                                                             │
│ Bài toán: Trợ lý AI Voice-to-Text tự động ghi chép biên bản │
│ phẫu thuật/nội soi khi bác sĩ không rảnh tay gõ máy tính.   │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ phẫu thuật, Bác sĩ nội soi.     │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Bác sĩ mặc đồ vô trùng, đang thực hiện thủ thuật       │
│   ──> 2. Phải đọc to để điều dưỡng gõ lại vào máy tính      │
│   ──> 3. Điều dưỡng nghe nhầm thuật ngữ khó, gõ sai         │
│   ──> 4. Hậu phẫu, bác sĩ mất thời gian ngồi đọc lại từ đầu │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 10 ph/ca)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (AI Voice  │
│ chuyên ngành Y tế nghe trực tiếp lệnh của bác sĩ, lọc bỏ tạp│
│ âm máy thở, tự động điền chuẩn xác vào template phẫu thuật).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm 100% thời gian phụ thuộc điều dưỡng ghi chép.        │
│   Lý do Rule-based bất lực: Bác sĩ đang vô trùng, rảnh tay  │
│   đâu mà dùng chuột click chọn Template/Macro?              │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM (Voice)    │
└─────────────────────────────────────────────────────────────┘


2.
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2 (RAG cho Hội chẩn Ca Khó)             │
│                                                             │
│ Bài toán: Hệ thống RAG tổng hợp y văn và phác đồ chéo để    │
│ hỗ trợ Hội chẩn Đa chuyên khoa (Tumor Board/Ca bệnh phức).  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Hội đồng Y khoa, Bác sĩ chuyên khoa sâu│
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận ca bệnh khó: Ung thư kèm Suy thận, Tiểu đường     │
│   ──> 2. Các bác sĩ mất nhiều ngày lục tìm y văn thế giới   │
│   ──> 3. Đối chiếu chéo thủ công để tìm chống chỉ định thuốc│
│   ──> 4. Họp hội đồng tranh luận phác đồ                    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ Vài ngày)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (RAG quét  │
│ hàng ngàn báo cáo NCBI, PubMed và Phác đồ Vinmec để highlight│
│ các xung đột thuốc trên nền bệnh nhân đa chấn thương).      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian chuẩn bị hội chẩn từ 2 ngày ──> 2 tiếng.   │
│   Lý do Rule-based bất lực: CDSS If/Else chỉ dùng cho ca    │
│   chuẩn, không thể bao quát các ca "biến dị" hiếm gặp.      │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM (RAG)      │
└─────────────────────────────────────────────────────────────┘


3.
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3 (Social Listening AI)                 │
│                                                             │
│ Bài toán: Khai phá ngữ nghĩa (Sentiment & Root Cause) từ    │
│ các bài bóc phốt, review tự do trên MXH và Google Maps.     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Trưởng phòng CSKH, Giám đốc Marketing. │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Khách lên hội nhóm Facebook/Google Maps chê bai        │
│   ──> 2. Nhân viên Marketing phải đọc thủ công từng bài     │
│   ──> 3. Copy/Paste ra Excel để tag lỗi (Thái độ, Giá cả)   │
│   ──> 4. Báo cáo Ban Giám đốc khi khủng hoảng đã bùng phát  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ Chậm trễ)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (LLM quét  │
│ real-time, nhận diện giọng văn mỉa mai, teencode, tự động   │
│ phân loại lỗi và kích hoạt báo động đỏ nếu có phốt y khoa). │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Nhận diện nguy cơ khủng hoảng truyền thông < 5 phút.      │
│   Lý do Rule-based bất lực: Vinmec không thể bắt khách trên │
│   Facebook điền form Checkbox của bệnh viện. Regex bắt      │
│   từ khóa sẽ trượt nếu khách dùng từ lóng, mỉa mai.         │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
