# 01 — Problem Scan & Quick Cards (Vin Smart Future)

> **Thành viên:**`Phùng Văn Thanh cao`
> Nội dung Phase 1 (SCAN) và Phase 2 (QUICK-ASSESS) lấy từ [01-worksheet.md](01-worksheet.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Lặp lại + Pain từ người khác | **Điểm đón sai, tài xế phải gọi xác nhận thủ công.** Ước tính 15–20% chuyến bị lệch điểm đón, mất khoảng 8.500 giờ tài xế/ngày. AI học điểm đón chuẩn từ lịch sử GPS lúc khách lên xe và tự động xác nhận điểm đón. |
| 2 | Xanh SM | Lặp lại + AI tốt hơn | **Ghép chuyến theo khoảng cách gần nhất, xe chạy rỗng nhiều, ETA dài.** Rút được 1 phút đi đón mỗi chuyến thì có thêm khoảng 40.000 chuyến năng lực/ngày. AI dự báo cầu theo khu vực, ghép chuyến theo lô và gợi ý tài xế di chuyển trước đến nơi sắp có nhu cầu. |
| 3 | Xanh SM | Tốn thời gian + Pain từ người khác | **Tài xế tự quyết thời điểm sạc, hay trùng giờ cao điểm và phải xếp hàng ở trạm.** Ước tính mất khoảng 6,5 tỷ/năm cho mỗi 1.000 xe. AI lập lịch sạc tối ưu theo mức pin, dự báo cầu và công suất trạm V-Green. |
| 4 | Xanh SM | Tốn thời gian + AI tốt hơn | **Xử lý khiếu nại của khách và giải trình vi phạm của tài xế bằng tay.** Ước tính khoảng 4.000 ticket/ngày, tương đương hơn 80 nhân sự toàn thời gian. LLM phân loại ticket, tự lấy bằng chứng từ GPS, giá, thời gian chờ và soạn sẵn phản hồi. |
| 5 | Xanh SM | Lặp lại + Pain từ người khác | **Gian lận thưởng, bù thu nhập (36.000đ/cuốc) và hỗ trợ sạc** qua chuyến ảo, giả GPS, đội km. Ước tính rò rỉ 17–55 tỷ/năm. AI phát hiện bất thường trên quỹ đạo GPS và mạng quan hệ tài xế–khách–thiết bị, chấm điểm rủi ro trước khi chi thưởng. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01            │
│                                                                  │
│ Bài toán (1 câu): Tại các điểm nóng (tòa Vinhomes, sân bay,      │
│   bệnh viện, TTTM), pin đón không khớp cổng/sảnh thực tế, gây    │
│   chờ, gọi lại và hủy chuyến.                                    │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes       │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________       │
│                                                                  │
│ Ai đang đau (Actor)? Tài xế (mất phút vận doanh, bị đánh giá     │
│   thấp); khách (chờ, đi bộ tìm xe); CSKH (khiếu nại).            │
│                                                                  │
│ Workflow thủ công hiện tại (3-5 bước):                           │
│   1. Khách đặt xe, pin GPS trôi / ghi chú tự do mơ hồ            │
│   ──> 2. Tài xế nhận cuốc, gọi khách (bắt buộc theo SOP)         │
│   ──> 3. Đến nơi không thấy khách: gọi lại, chat, đi vòng        │
│   ──> 4. Đón được khách, hoặc một bên hủy chuyến                 │
│                                                                  │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (baseline cần đo;        │
│   giả thuyết ~3-4 phút/lượt). Chỉ tính ca do pin sai/chọn sai    │
│   địa chỉ; loại trừ ca thiếu chỗ đỗ và ca khách chưa ra.         │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Giai đoạn 1 KHÔNG dùng     │
│   AI. Ở bước 1: bảng tra điểm đón chuẩn cho 500 điểm nóng        │
│   (sơ đồ cổng/sảnh Vinhomes + trung vị GPS lên xe), app bắt      │
│   chọn nút "Sảnh A / Cổng chính / Hầm B1" thay ghi chú tự do.    │
│   Điều kiện tiên quyết: Ops miễn cuộc gọi bắt buộc khi điểm      │
│   đón đã chuẩn hóa.                                              │
│                                                                  │
│ Đo thành công bằng gì (Metric có số)?                            │
│   - Chính: Phút mất tại điểm đón/chuyến ở điểm nóng (từ "đã      │
│     đến" ──> bắt đầu tính cước, đối chiếu GPS xe) giảm >=40%     │
│     so với baseline đo trong 2 tuần đầu.                         │
│   - Quy ra tiền: Số chuyến hủy tránh được x ~50.000đ, cộng       │
│     số chuyến tăng thêm trong giờ cao điểm.                      │
│   - Guardrail: quãng đi bộ của khách +<=50m; ETA không tăng;     │
│     CSAT không giảm.                                             │
│   - Thiết kế: A/B theo điểm nóng ghép cặp, 4 tuần.               │
│                                                                  │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent      │
│   Giai đoạn 2 (chỉ khi qua cổng): ML cho phần long tail ngoài    │
│   bảng tra, nếu phần còn lại chiếm >X% tổng phút mất và lợi      │
│   ích ròng >Y tỷ/năm sau khi trừ chi phí vận hành mô hình.       │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02           │
│                                                                  │
│ Bài toán (1 câu): Giờ cao điểm mất chuyến vì thiếu xe tại điểm   │
│   nóng, do tài xế không có động lực chạy rỗng đến trước và Ops   │
│   kéo xe thủ công, phản ứng chậm.                                │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes       │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________       │
│                                                                  │
│ Ai đang đau (Actor)? Khách (đặt không có xe); tài xế toàn thời   │
│   gian (km rỗng không được trả); Ops khu vực (kéo xe bằng tay).  │
│   Phạm vi: chỉ tài xế toàn thời gian; chưa áp dụng Platform.     │
│                                                                  │
│ Workflow thủ công hiện tại (3-5 bước):                           │
│   1. Ops theo dõi heatmap, thấy vùng đã thiếu xe                 │
│   ──> 2. Ops tự quyết gửi thông báo/thưởng kéo xe                │
│   ──> 3. Tài xế cân nhắc pin, kẹt xe, tiền; phần lớn bỏ qua      │
│   ──> 4. Nhiều xe đổ về cùng vùng, vùng cũ lại thiếu             │
│                                                                  │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3: phản ứng sau khi      │
│   thiếu xe đã xảy ra, trễ ~15-30 phút (giả thuyết, cần đo từ     │
│   log thông báo và log thiếu xe).                                │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Giai đoạn 1 KHÔNG dùng     │
│   AI. Tự động hóa bước 1-2 bằng luật:                            │
│   - Dự báo = trung bình 4 tuần cùng thứ/giờ x hệ số sự kiện      │
│     (lịch bay, trận đấu, lễ) x hệ số mưa.                        │
│   - NẾU ô X thiếu N xe trong 20 phút tới THÌ gợi ý tối đa        │
│     1,2 x N xe rảnh, bán kính 2 km, pin >40%, kèm thưởng cố      │
│     định nếu nhận chuyến trong 15 phút. Ghi rõ lý do             │
│     (VD: "14 chuyến bay hạ cánh trong 30 phút tới").             │
│   - Ghép theo lô: chỉ chạy shadow mode, chưa thay hệ thống lõi.  │
│                                                                  │
│ Đo thành công bằng gì (Metric có số)?                            │
│   - Chính (duy nhất): Chuyến mất vì thiếu xe ở giờ cao điểm      │
│     giảm >=20% so với baseline đo trong 2 tuần đầu.              │
│   - Quy ra tiền: Biên đóng góp tăng thêm = chuyến cứu được x     │
│     phần GSM giữ lại, trừ chi phí thưởng kéo xe. Phải > 0.       │
│   - Theo dõi: Km rỗng (chấp nhận tăng nếu biên vẫn dương).       │
│   - Guardrail: thu nhập/giờ tài xế không giảm; không ô nào       │
│     nhận >1,5 x N xe; vùng nguồn không tăng tỷ lệ thiếu xe.      │
│   - Thiết kế: switchback khu vực x khung 2 giờ, washout 30       │
│     phút, 4 tuần, 1 thành phố.                                   │
│                                                                  │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent      │
│   Rủi ro: chạy ngoài hệ thống Dispatch lõi (chỉ gửi gợi ý),      │
│   có công tắc tắt ngay; owner: Ops khu vực + team Platform.      │
│   Giai đoạn 2 (chỉ khi qua cổng): ML dự báo nếu sai số sau       │
│   bảng tra vẫn >X% và biên tăng thêm > chi phí vận hành.         │
└──────────────────────────────────────────────────────────────────┘


┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03               │
│                                                                  │
│ Bài toán (1 câu): Lần sạc tùy chọn (không bắt buộc) rơi vào      │
│   lúc cầu cao và dồn hàng chờ tại trạm V-Green, do giờ giao ca,  │
│   giá sạc và thời điểm sạc chưa được thiết kế đồng bộ.           │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes       │
│                     [ ] Vinmec   [x] Khác (Ghi rõ) V-Green       │
│                                                                  │
│ Ai đang đau (Actor)? Tài xế toàn thời gian (mất cuốc, chờ trạm); │
│   khách (thiếu xe lúc cầu cao); Ops (không thấy kế hoạch sạc).   │
│   Phạm vi: xe công ty có dữ liệu pin (SoC), 1 thành phố.         │
│                                                                  │
│ Workflow thủ công hiện tại (3-5 bước):                           │
│   1. Giao ca/xe theo lịch cố định, không xét đường cầu           │
│   ──> 2. Tài xế tự theo dõi % pin, tự chọn trạm                  │
│   ──> 3. Đến trạm: xếp hàng, sạc nhanh DC ~30-45 phút            │
│   ──> 4. Quay lại vận doanh, thường đã lỡ đỉnh cầu               │
│                                                                  │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1+3: giờ giao ca và hàng   │
│   chờ trạm (giả thuyết; cần đo). Tách sạc BẮT BUỘC (pin <15%)    │
│   khỏi sạc TÙY CHỌN; chỉ phần tùy chọn mới tối ưu được.          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Giai đoạn 1 KHÔNG dùng     │
│   AI. Ba đòn bẩy tất định:                                       │
│   - Bước 1: dời giờ giao ca ra khỏi đỉnh cầu (quyết định HR).    │
│   - Bước 2: km còn lại = SoC x dung lượng / tiêu thụ; thiếu      │
│     km cho ca thì cấp slot: giờ bắt đầu + (mã TX mod K) x 15'.   │
│   - Bước 3: đặt trước trụ theo slot với V-Green (tối đa 1        │
│     xe/trụ/slot); giá sạc theo khung giờ, bỏ ưu đãi lúc cầu      │
│     cao. Pin thấp chỉ CẢNH BÁO tài xế, không chặn ghép chuyến.   │
│                                                                  │
│ Đo thành công bằng gì (Metric có số)?                            │
│   - Chính (duy nhất): Chuyến mất do sạc tùy chọn, có trọng       │
│     số theo cầu thực tế (phút sạc x cầu cùng giờ, cùng khu       │
│     vực) giảm >=30% so với baseline 2 tuần đầu.                  │
│   - Quy ra tiền: Biên đóng góp CẤP TẬP ĐOÀN (GSM + V-Green) =    │
│     chuyến cứu được x phần giữ lại, trừ chi phí điện thực.       │
│   - Theo dõi: thời gian chờ trạm; số lần hết pin giữa ca.        │
│   - Guardrail: thu nhập/giờ tài xế không giảm; số lần sạc        │
│     nhanh/xe/ngày không tăng (sức khỏe pin).                     │
│   - Thiết kế: slot + đặt trụ: switchback theo ngày toàn TP,      │
│     6 tuần (tránh nhiễu giữa cụm trạm). Giao ca + giá: không     │
│     bật/tắt hằng ngày được, đo trước/sau với TP đối chứng.       │
│                                                                  │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent      │
│   Phụ thuộc: SoC (VinFast), API trạm + đặt trụ (V-Green); chốt   │
│   owner + SLA trước. Fallback: API lỗi thì giữ slot đã cấp,      │
│   không gợi ý trạm theo dữ liệu realtime.                        │
│   Giai đoạn 2 (chỉ khi qua cổng): tối ưu OR/ML nếu sau slot +    │
│   đặt trụ + giá theo giờ, chuyến mất do sạc vẫn >X%.             │
└──────────────────────────────────────────────────────────────────┘


```

---

# 🗳️ Quyết định lựa chọn của nhóm

Sau khi review thẻ của các thành viên, nhóm chọn bài toán **Vinpearl — Tự động hóa check-in/check-out khách lưu trú** để Deep-Dive ([02-deep-dive-report.md](02-deep-dive-report.md)).

## Lý do lựa chọn và vì sao chưa chọn 3 thẻ Xanh SM của tôi
* **Vinpearl check-in/check-out** có bottleneck nhìn thấy và đo được ngay tại quầy (xếp hàng giờ cao điểm, nhập tay giấy tờ, chờ kiểm minibar). Phạm vi gói gọn trong 1 resort, ít phụ thuộc hệ thống lõi. Có phần **xử lý ngôn ngữ tự do, đa ngôn ngữ** (yêu cầu đặc biệt từ OTA, giải thích phụ thu), là chỗ LLM thực sự có ích.
* **Card #01 (điểm đón ở điểm nóng)** và **Card #02 (thiếu xe giờ cao điểm):** giai đoạn 1 giải được bằng Rule, không cần LLM. Hai thẻ còn phụ thuộc dữ liệu GPS/Dispatch lõi và quyết định của Ops trước khi thử nghiệm được.
* **Card #03 (lịch sạc V-Green):** phụ thuộc 3 bên (Xanh SM, VinFast SoC, V-Green), cần chốt owner và SLA API trước, và có đòn bẩy nằm ở quyết định HR (giờ giao ca). Phạm vi quá rộng cho 1 lab.
