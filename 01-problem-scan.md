## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Hằng**, AI Engineer tại **Vin Smart Future**. Nhóm chúng tôi được giao nhiệm vụ phối hợp với Khối Vận Hành của **Vinpearl / VinWonders** để tìm kiếm các cơ hội tối ưu hóa bằng trí tuệ nhân tạo. 

Thông qua đợt khảo sát thực tế tại hệ thống quần thể nghỉ dưỡng và vui chơi giải trí Vinpearl Nha Trang / Phú Quốc, tôi nhận thấy các quản lý và nhân viên vận hành đang phải đối mặt với áp lực lớn vào mùa cao điểm: khách hàng xếp hàng dài chờ check-in, tình trạng nghẽn luồng khách tại các cổng trò chơi trọng điểm, cùng với việc xử lý hàng loạt yêu cầu thay đổi lịch trình cá nhân hóa thủ công. Các bài toán dưới đây được đúc kết trực tiếp từ thực trạng vận hành này.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinpearl** | Lặp lại | Nhân viên lễ tân phải kiểm tra thông tin đặt phòng, xác minh giấy tờ tùy thân, đối chiếu thanh toán và cập nhật trạng thái phòng thủ công trong quy trình check-in/check-out, gây mất thời gian vào mùa cao điểm. |
| 2 | **Vinpearl** | Tốn thời gian | Quản lý phải tổng hợp dữ liệu đặt phòng, tỷ lệ lấp đầy và lịch sử sử dụng dịch vụ để dự báo nhu cầu, lập kế hoạch và phân bổ nhân sự cho các bộ phận như lễ tân, buồng phòng và nhà hàng. |
| 3 | **Vinpearl** | Pain từ người khác | Khách hàng phải chờ nhận phòng do việc cập nhật trạng thái dọn dẹp, kiểm tra và bàn giao phòng giữa bộ phận lễ tân và buồng phòng chưa đồng bộ kịp thời. |
| 4 | **VinWonders** | Lặp lại | Nhân viên tại cổng phải liên tục quét mã vé, xác minh loại vé, kiểm tra quyền sử dụng và xử lý các trường hợp vé lỗi hoặc không hợp lệ, đặc biệt khi lượng khách tăng cao. |
| 5 | **VinWonders** | AI-upgrade | Khách tham quan phải tự tìm kiếm thông tin về trò chơi, thời gian biểu diễn, thời gian chờ và vị trí các khu vực để xây dựng lịch trình phù hợp với sở thích và thời gian tham quan. |

---
# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#1 (Vinpearl Check-in/Check-out), #2 (Vinpearl Dự báo nhân sự), #5 (VinWonders Cá nhân hóa lịch trình).**

## Thẻ bài toán tiêu biểu: Card #1 — Vinpearl Tự động hóa Check-in/Check-out

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Nhân viên lễ tân phải kiểm tra thông tin đặt      │
│ phòng, giấy tờ tùy thân và thanh toán thủ công, khiến       │
│ khách phải chờ lâu vào mùa cao điểm.                        │
│ Công ty thành viên: [x] Khác (Vinpearl)                     │
│                                                             │
│ Ai đang đau? Khách lưu trú (chờ đợi), Nhân viên lễ tân      │
│ (quá tải), Quản lý khách sạn (hiệu suất vận hành).          │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Khách cung cấp mã đặt phòng và giấy tờ tùy thân        │
│   → 2. Lễ tân kiểm tra và xác minh thông tin khách          │
│   → 3. Đối chiếu thông tin thanh toán và dịch vụ đã đặt     │
│   → 4. Nhập/cập nhật dữ liệu vào hệ thống quản lý khách sạn │
│   → 5. Xác nhận nhận phòng và bàn giao chìa khóa            │
│                                                             │
│ Bước nào tốn nhất? Bước 2-4 (⏱ 3-5 phút/khách)              │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ (OCR giấy tờ -> Đối chiếu dữ liệu -> Tự động điền thông tin)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian xử lý check-in từ 5 phút -> dưới 2 phút.    │
│ Giảm ít nhất 50% thời gian nhập liệu thủ công.              │
│                                                             │
│ Quick Architecture: [x] Rule (OCR + Workflow Automation)    │
└─────────────────────────────────────────────────────────────┘
```

## Thẻ bài toán: Card #2 — Vinpearl Dự báo nhu cầu và phân bổ nhân sự

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Quản lý khách sạn phải tổng hợp dữ liệu đặt phòng │
│ và lượng khách thủ công để dự báo nhu cầu, phân bổ nhân sự, │
│ dẫn đến thiếu hoặc thừa nhân lực vào giờ cao điểm.          │
│ Công ty thành viên: [x] Khác (Vinpearl)                     │
│                                                             │
│ Ai đang đau? Quản lý vận hành (khó lập kế hoạch),           │
│ Trưởng bộ phận (khó điều phối), Nhân viên (quá tải).        │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Thu thập dữ liệu đặt phòng và tỷ lệ lấp đầy            │
│   → 2. Tổng hợp lịch sử lưu trú và sử dụng dịch vụ          │
│   → 3. Ước tính lượng khách theo ngày và khung giờ          │
│   → 4. Lập kế hoạch phân bổ nhân sự từng bộ phận            │
│   → 5. Điều chỉnh lịch làm việc khi nhu cầu thay đổi        │
│                                                             │
│ Bước nào tốn nhất? Bước 2-4 (⏱ 60-120 phút/chu kỳ)          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ (Tổng hợp dữ liệu -> Dự báo lượng khách -> Đề xuất nhân sự) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian lập kế hoạch từ 120 phút -> dưới 30 phút.   │
│ Giảm ít nhất 20% sai lệch giữa nhân sự dự báo và thực tế.   │
│                                                             │
│ Quick Architecture: [x] Rule (ML Forecasting + Optimization)│
└─────────────────────────────────────────────────────────────┘
```

## Thẻ bài toán: Card #3 — VinWonders Cá nhân hóa lịch trình vui chơi

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Khách tham quan phải tự tìm kiếm và sắp xếp thông │
│ tin trò chơi, thời gian biểu diễn, vị trí và thời gian chờ  │
│ để xây dựng lịch trình phù hợp với nhu cầu cá nhân.         │
│ Công ty thành viên: [x] Khác (VinWonders)                   │
│                                                             │
│ Ai đang đau? Khách tham quan (mất thời gian lập lịch),      │
│ Gia đình có trẻ nhỏ (khó lựa chọn hoạt động),               │
│ Nhân viên CSKH (phải tư vấn nhiều yêu cầu lặp lại).         │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Tìm kiếm thông tin trò chơi và chương trình biểu diễn  │
│   → 2. Lựa chọn hoạt động theo sở thích và độ tuổi          │
│   → 3. Tra cứu vị trí các khu vực trên bản đồ               │
│   → 4. Ước tính thời gian di chuyển và thời gian chờ        │
│   → 5. Tự sắp xếp và điều chỉnh lịch trình                  │
│                                                             │
│ Bước nào tốn nhất? Bước 4-5 (⏱ 10-20 phút/lịch trình)       │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-5              │
│ (Phân tích sở thích -> Gợi ý hoạt động -> Tối ưu lịch trình)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian lập lịch từ 20 phút -> dưới 2 phút.         │
│ Tỷ lệ khách chấp nhận lịch trình đề xuất đạt ít nhất 70%.  │
│                                                             │
│ Quick Architecture: [x] Agent (LLM + Recommendation System) │
└─────────────────────────────────────────────────────────────┘
```
