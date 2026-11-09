# 01 — Problem Scan: AI Product Scoping (Vin Smart Future)

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast | Lặp lại | Phân loại, đối chiếu và xác minh hồ sơ yêu cầu bảo hành (Warranty Claims). Nhân viên phải kiểm tra thông tin xe, mã lỗi, lịch sử sửa chữa, điều kiện bảo hành và hóa đơn trước khi phê duyệt. Có thể phát sinh hàng nghìn hồ sơ cần xử lý. |
| 2 | VinFast | Tốn thời gian | Chẩn đoán nguyên nhân lỗi xe từ dữ liệu kỹ thuật, mã DTC, lịch sử sửa chữa và ghi chú của kỹ thuật viên. Kỹ thuật viên phải tra cứu nhiều tài liệu để tìm nguyên nhân gốc (Root Cause Analysis), đặc biệt với các lỗi tái diễn hoặc liên quan nhiều bộ phận. |
| 3 | VinFast | Pain từ người khác | Dự báo nhu cầu và phân bổ phụ tùng giữa các xưởng dịch vụ. Tình trạng thiếu phụ tùng tại một xưởng trong khi xưởng khác tồn kho dư thừa khiến xe phải nằm chờ sửa chữa, khách hàng phải quay lại nhiều lần. |
| 4 | VinFast | AI-upgrade | Phân tích tự động phản hồi, khiếu nại và đánh giá của khách hàng từ hotline, ứng dụng và mạng xã hội. Nhân viên CSKH phải đọc, phân loại, xác định mức độ nghiêm trọng và chuyển tiếp từng trường hợp đến bộ phận liên quan. |
| 5 | VinFast | Lặp lại | Phát hiện bất thường trong kiểm tra chất lượng sản xuất (Quality Inspection). Nhân viên cần kiểm tra hình ảnh, kết quả kiểm định và thông số kỹ thuật để phát hiện lỗi lắp ráp, lỗi bề mặt hoặc sai lệch linh kiện giữa các công đoạn. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Tự động trích xuất, đối chiếu và kiểm tra điều kiện bảo hành│
│ từ hồ sơ yêu cầu bảo hành để giảm thao tác thủ công.        │
│                                                             │
│ Công ty thành viên:                                         │
│ [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec         │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên Warranty Claims, nhân viên hậu mãi, quản lý bảo hành│
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận hồ sơ                                             │
│      ──> 2. Đọc hóa đơn, phiếu sửa chữa và thông tin VIN     │
│      ──> 3. Đối chiếu chính sách bảo hành                    │
│      ──> 4. Kiểm tra mã lỗi và lịch sử sửa chữa              │
│      ──> 5. Phê duyệt hoặc yêu cầu bổ sung hồ sơ             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Đọc tài liệu và đối chiếu điều kiện bảo hành                │
│ (⏱ Ước tính: 10-15 phút/hồ sơ)                              │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Document AI + LLM trích xuất thông tin từ hồ sơ,             │
│ tự động đối chiếu VIN, mã lỗi, linh kiện và chính sách      │
│ bảo hành; cảnh báo hồ sơ thiếu thông tin hoặc bất thường.   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian kiểm tra từ 10-15 phút -> dưới 3 phút/hồ sơ  │
│ Mục tiêu: Giảm ít nhất 70% thời gian xử lý thủ công.        │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Hỗ trợ kỹ thuật viên chẩn đoán nguyên nhân lỗi xe từ mã DTC,│
│ lịch sử sửa chữa và tài liệu kỹ thuật của VinFast.          │
│                                                             │
│ Công ty thành viên:                                         │
│ [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec         │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Kỹ thuật viên xưởng dịch vụ và cố vấn kỹ thuật VinFast.     │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tiếp nhận xe và mô tả lỗi từ khách hàng                │
│      ──> 2. Đọc mã DTC và dữ liệu chẩn đoán                  │
│      ──> 3. Tra cứu tài liệu kỹ thuật, lịch sử sửa chữa      │
│      ──> 4. Khoanh vùng nguyên nhân và thực hiện kiểm tra     │
│      ──> 5. Xác nhận nguyên nhân và đề xuất phương án sửa    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Tra cứu nhiều nguồn và khoanh vùng nguyên nhân gốc          │
│ (⏱ Ước tính: 30-60 phút/ca lỗi phức tạp).                   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ LLM kết hợp RAG tổng hợp mã DTC, lịch sử sửa chữa và tài    │
│ liệu kỹ thuật để xếp hạng nguyên nhân khả dĩ, trích dẫn tài │
│ liệu liên quan và đề xuất bước kiểm tra cho kỹ thuật viên.  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian khoanh vùng lỗi từ 30-60 phút xuống dưới     │
│ 15 phút/ca; ít nhất 80% gợi ý có tài liệu nguồn phù hợp.    │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Tự động phân loại, ưu tiên và chuyển tiếp phản hồi, khiếu   │
│ nại của khách hàng VinFast đến đúng bộ phận xử lý.          │
│                                                             │
│ Công ty thành viên:                                         │
│ [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec         │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên CSKH, điều phối viên và quản lý dịch vụ VinFast.  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận phản hồi từ hotline, ứng dụng và mạng xã hội      │
│      ──> 2. Đọc nội dung và xác định mức độ nghiêm trọng     │
│      ──> 3. Gắn nhãn và nhập thông tin vào hệ thống          │
│      ──> 4. Chuyển đến bộ phận phụ trách                     │
│      ──> 5. Theo dõi SLA và cập nhật trạng thái cho khách    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Đọc, phân loại mức độ nghiêm trọng và chọn đúng bộ phận     │
│ (⏱ Ước tính: 5-10 phút/phản hồi).                           │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ LLM phân tích nội dung, cảm xúc và mức độ khẩn cấp; đề xuất │
│ nhãn, tóm tắt vụ việc và bộ phận tiếp nhận. Trường hợp rủi  │
│ ro cao phải được nhân viên duyệt trước khi chuyển tiếp.     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian phân loại từ 5-10 phút xuống dưới 1 phút;    │
│ đạt ít nhất 90% độ chính xác khi định tuyến phản hồi.       │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

Chọn top 3 từ danh sách SCAN: #1 (VinFast xử lý hồ sơ bảo hành), #2 (VinFast hỗ trợ chẩn đoán lỗi xe), #4 (VinFast AI CSKH).

---

# 🗳️ Quyết định lựa chọn của nhóm

Sau khi review các đề xuất của thành viên, nhóm quyết định chọn **tự động hóa quy trình check-in tại Vinpearl bằng OCR và workflow automation** để thực hiện Phase 3 — Deep Dive.

## Tóm tắt bài toán được chọn

- **Công ty thành viên:** Vinpearl.
- **Bài toán:** Nhân viên lễ tân phải kiểm tra thủ công thông tin đặt phòng, giấy tờ tùy thân và thanh toán, khiến khách phải chờ lâu vào mùa cao điểm.
- **Actor:** Khách lưu trú, nhân viên lễ tân và quản lý khách sạn.
- **Workflow hiện tại:**
  1. Khách cung cấp mã đặt phòng và giấy tờ tùy thân.
  2. Lễ tân kiểm tra và xác minh thông tin khách.
  3. Đối chiếu thông tin thanh toán và dịch vụ đã đặt.
  4. Nhập hoặc cập nhật dữ liệu vào hệ thống quản lý khách sạn.
  5. Xác nhận nhận phòng và bàn giao chìa khóa.
- **Bottleneck:** Các bước 2–4, mất khoảng **3–5 phút/khách**.
- **Giải pháp:** OCR giấy tờ, đối chiếu dữ liệu và tự động điền thông tin tại các bước 2–4.
- **Success metric:** Giảm thời gian check-in từ khoảng **5 phút xuống dưới 2 phút**, đồng thời giảm ít nhất **50% thời gian nhập liệu thủ công**.
- **Quick Architecture:** **Rule-based workflow kết hợp OCR và workflow automation**.

## Lý do lựa chọn

- Quy trình check-in có các bước tuần tự, đầu vào và đầu ra rõ ràng nên dễ xác định phạm vi prototype.
- Bottleneck 3–5 phút mỗi khách có thể đo trực tiếp, đặc biệt có ý nghĩa trong mùa cao điểm.
- OCR và workflow automation phù hợp hơn một hệ thống LLM hoặc agent phức tạp, giúp giảm chi phí và rủi ro triển khai.
- Nhân viên lễ tân vẫn kiểm tra các trường hợp giấy tờ không rõ, dữ liệu không khớp hoặc thanh toán bất thường trước khi xác nhận nhận phòng.

## Lý do chưa chọn các bài toán khác

- **Xử lý hồ sơ bảo hành VinFast:** Cần tích hợp nhiều nguồn dữ liệu và diễn giải chính sách bảo hành; quyết định sai có thể gây tổn thất tài chính.
- **Hỗ trợ chẩn đoán lỗi xe VinFast:** Có rủi ro kỹ thuật và an toàn cao, đồng thời cần dữ liệu DTC và tài liệu sửa chữa đáng tin cậy.
- **Phân loại khiếu nại VinFast:** Khả thi nhưng ngôn ngữ khiếu nại đa dạng, khó xác lập baseline và độ chính xác định tuyến trong phạm vi buổi lab.
