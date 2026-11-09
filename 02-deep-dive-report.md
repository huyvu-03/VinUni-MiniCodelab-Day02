# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)

## 3.1. Current-State Workflow

**Đối tượng thực hiện:** Nhân viên lễ tân (Front Desk Staff) tại Vinpearl.

**Quy trình check-in hiện tại:**

| Bước | Hoạt động | Người / Hệ thống thực hiện | Thời gian ước tính | Đánh giá |
|---|---|---|---|---|
| 1 | Khách cung cấp mã đặt phòng và giấy tờ tùy thân | Guest | 0.5 phút | Bình thường |
| 2 | Kiểm tra và xác minh thông tin khách hàng | Front Desk Staff | 1.5 phút | 🔴 Bottleneck |
| 3 | Đối chiếu thông tin đặt phòng, thanh toán và dịch vụ | Front Desk Staff / PMS | 1 phút | 🔴 Bottleneck |
| 4 | Nhập hoặc cập nhật thông tin vào hệ thống PMS | Front Desk Staff / PMS | 1.5 phút | 🔴 Bottleneck |
| 5 | Xác nhận check-in và bàn giao chìa khóa phòng | Front Desk Staff | 0.5 phút | Bình thường |
| | **Tổng thời gian** | | **5 phút/khách** | |

*Lưu ý: Thời gian từng bước là số liệu ước tính phục vụ phân tích ban đầu, cần được xác nhận bằng quan sát thực tế tại khách sạn.*

**Sơ đồ quy trình hiện tại:**

```text
Guest
  |
  v
(1) Provide Booking Code + ID
  |
  v
(2) Verify Guest Information
  |  🔴 Manual ID Verification
  v
(3) Check Booking + Payment + Services
  |  🔴 Manual Cross-checking
  v
(4) Enter / Update Information in PMS
  |  🔴 Manual Data Entry
  v
(5) Confirm Check-in + Handover Key
  |
  v
Complete
```

**Các điểm nghẽn (Bottlenecks):**

| Bước | Vấn đề | Nguyên nhân | Tác động |
|---|---|---|---|
| Step 2 | Xác minh thông tin khách hàng mất thời gian | Nhân viên phải đọc và kiểm tra thủ công giấy tờ tùy thân | Tăng thời gian chờ, dễ xảy ra sai sót |
| Step 3 | Đối chiếu thông tin đặt phòng và thanh toán | Phải kiểm tra nhiều nguồn thông tin khác nhau | Chậm xử lý, tăng khối lượng công việc |
| Step 4 | Nhập lại thông tin vào PMS | Nhân viên phải nhập dữ liệu thủ công | Tốn thời gian, có nguy cơ nhập sai hoặc trùng lặp |

**Handoff (Bàn giao thông tin):**

- Guest → Front Desk Staff: Cung cấp mã đặt phòng và giấy tờ tùy thân.
- Front Desk Staff → PMS: Kiểm tra và cập nhật thông tin đặt phòng.
- PMS → Front Desk Staff: Cung cấp thông tin đặt phòng và trạng thái thanh toán.

**Kết luận:** Step 2, Step 3 và Step 4 là những điểm nghẽn chính, chiếm khoảng 4/5 tổng thời gian check-in ước tính.

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor (Ai gặp vấn đề?)** | Nhân viên lễ tân (Front Desk Staff) tại Vinpearl là đối tượng trực tiếp thực hiện quy trình check-in. Quản lý khách sạn là người chịu trách nhiệm giám sát hiệu quả vận hành và chất lượng dịch vụ. |
| **2. Current Workflow (Quy trình hiện tại)** | Khách cung cấp mã đặt phòng và giấy tờ tùy thân. Nhân viên lễ tân kiểm tra thông tin, đối chiếu đặt phòng và thanh toán, nhập dữ liệu vào PMS, sau đó xác nhận check-in và bàn giao chìa khóa. Quy trình gồm 5 bước, mất khoảng 5 phút/khách (ước tính). |
| **3. Bottleneck (Điểm nghẽn)** | Step 2, 3 và 4: Nhân viên phải kiểm tra giấy tờ tùy thân, đối chiếu thông tin đặt phòng và thanh toán, sau đó nhập lại dữ liệu vào PMS. Các thao tác thủ công làm tăng thời gian xử lý và nguy cơ sai sót. |
| **4. Business Impact (Tác động kinh doanh)** | Khách hàng phải chờ lâu hơn, đặc biệt trong mùa cao điểm. Nhân viên lễ tân chịu áp lực công việc lớn, giảm thời gian hỗ trợ khách hàng. Sai sót khi nhập dữ liệu có thể gây nhầm lẫn thông tin đặt phòng, dịch vụ hoặc bàn giao phòng. |
| **5. Success Metrics (Chỉ số thành công)** | - Giảm thời gian check-in trung bình từ 5 phút xuống dưới 2 phút/khách.<br>- Giảm ít nhất 50% thời gian nhập dữ liệu thủ công.<br>- Đạt độ chính xác trích xuất thông tin OCR tối thiểu 98% trên bộ dữ liệu kiểm thử.<br>- 100% trường hợp dữ liệu không khớp hoặc có độ tin cậy thấp phải được chuyển cho nhân viên kiểm tra. |
| **6. Operational Boundary (Giới hạn vận hành)** | AI chỉ hỗ trợ OCR, trích xuất thông tin, đối chiếu dữ liệu với PMS và tạo bản nháp thông tin check-in. AI không được tự quyết định xác minh danh tính khi có sai lệch, xác nhận thanh toán, phê duyệt check-in hoặc tự ý thay đổi dữ liệu đặt phòng. Nhân viên lễ tân phải kiểm tra và phê duyệt trước khi cập nhật chính thức. |

---

## 3.3. Future-State Flow & AI Fit

**AI Fit:**

- [x] **Rule / Workflow Automation:** Phù hợp vì quy trình check-in có các bước cố định và dữ liệu cần đối chiếu tương đối có cấu trúc.
- [x] **OCR (Optical Character Recognition):** Trích xuất thông tin từ giấy tờ tùy thân, giảm thao tác đọc và nhập dữ liệu thủ công.
- [x] **Rule Engine:** Đối chiếu thông tin trích xuất với dữ liệu đặt phòng và trạng thái thanh toán trong PMS.
- [ ] **LLM:** Chưa cần thiết trong phiên bản đầu tiên vì quy trình không yêu cầu xử lý ngôn ngữ tự nhiên phức tạp.
- [ ] **Agentic Loop:** Chưa phù hợp vì quy trình có các bước cố định, liên quan đến dữ liệu cá nhân và cần sự kiểm soát của nhân viên.

**Lý do lựa chọn:**

Sử dụng OCR kết hợp Rule Engine và Workflow Automation là giải pháp phù hợp nhất cho bài toán hiện tại. Hệ thống có thể tự động trích xuất, đối chiếu và điền thông tin vào biểu mẫu nháp, trong khi nhân viên lễ tân vẫn là người kiểm tra và phê duyệt cuối cùng.

**Các thành phần chính:**

| Thành phần | Vai trò |
|---|---|
| OCR | Trích xuất thông tin từ giấy tờ tùy thân |
| Rule Engine | Kiểm tra và đối chiếu dữ liệu |
| PMS Integration | Kết nối và truy xuất thông tin đặt phòng, thanh toán |
| Workflow Automation | Tự động điền thông tin vào biểu mẫu check-in |
| Human-in-the-Loop (HITL) | Nhân viên kiểm tra và phê duyệt trước khi cập nhật chính thức |

**Quy trình tương lai (Future-State):**

```text
Guest
  |
  v
Provide Booking Code + ID
  |
  v
[AI] OCR Extracts Guest Information
  |
  v
[AI] Rule Engine Matches Data
  |       ^
  |       |
  |     [PMS]
  |  Booking + Payment Data
  v
[AI] Generate Check-in Draft
  |
  v
[HITL] Front Desk Reviews Information
  |
  +------ Data Mismatch / Low Confidence ------+
  |                                            |
  v                                            v
Approve Information                    Manual Verification
  |                                            |
  v                                            |
Update Check-in Status in PMS <---------------+
  |
  v
Handover Room Key
  |
  v
Complete
```

**Fallback / Exception Handling:**

| Trường hợp | Cách xử lý |
|---|---|
| OCR không đọc được giấy tờ | Chuyển sang kiểm tra và nhập thông tin thủ công |
| Thông tin giấy tờ không khớp với PMS | Yêu cầu nhân viên xác minh trực tiếp |
| Không tìm thấy mã đặt phòng | Nhân viên kiểm tra lại thông tin đặt phòng |
| Trạng thái thanh toán không rõ ràng | Nhân viên kiểm tra với hệ thống thanh toán hoặc bộ phận liên quan |
| PMS hoặc dịch vụ OCR không hoạt động | Chuyển sang quy trình check-in thủ công |

**Data Privacy & Security:**

- Chỉ thu thập và xử lý những thông tin cần thiết cho quy trình check-in.
- Hạn chế thời gian lưu trữ hình ảnh giấy tờ tùy thân.
- Mã hóa dữ liệu trong quá trình truyền tải và lưu trữ.
- Áp dụng phân quyền truy cập theo vai trò nhân viên.
- Không sử dụng dữ liệu khách hàng cho mục đích khác khi chưa được cho phép.

**Kết luận Phase 3:**

Giải pháp OCR + Rule Engine + Workflow Automation có thể giảm đáng kể thao tác thủ công tại các bước 2, 3 và 4. Tuy nhiên, nhân viên lễ tân vẫn giữ quyền kiểm soát và phê duyệt cuối cùng để đảm bảo độ chính xác, an toàn dữ liệu và chất lượng dịch vụ.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

## AI Readiness Checklist

| STT | Tiêu chí đánh giá | Trạng thái | Giải thích |
|---|---|---|---|
| 1 | Có dữ liệu mẫu hoặc logs để thử nghiệm không? | [x] Partly | Có thể sử dụng giấy tờ tùy thân giả lập hoặc đã ẩn danh, kết hợp dữ liệu đặt phòng và thanh toán mô phỏng để xây dựng prototype. Cần dữ liệu thực tế được cấp phép trước khi triển khai. |
| 2 | Rủi ro có thể kiểm soát được không? | [x] Yes | OCR và kết quả đối chiếu chỉ mang tính hỗ trợ. Nhân viên lễ tân phải kiểm tra và phê duyệt trước khi cập nhật chính thức. Các trường hợp không khớp sẽ được chuyển sang xử lý thủ công. |
| 3 | Stakeholder có sẵn sàng tham gia không? | [ ] Not confirmed | Chưa có xác nhận từ quản lý khách sạn và nhân viên lễ tân về nhu cầu, quy trình thực tế cũng như khả năng tích hợp với hệ thống PMS hiện tại. |

## Quyết định cuối cùng: GO / NOT YET / NO-GO

- [x] **GO — Start Prototype**
- [ ] NOT YET
- [ ] NO-GO

**Lý do lựa chọn:**

1. **Problem rõ ràng:** Quy trình check-in có nhiều thao tác lặp lại, đặc biệt ở các bước xác minh thông tin, đối chiếu đặt phòng và nhập dữ liệu vào PMS.

2. **AI Fit phù hợp:** OCR có thể trích xuất thông tin từ giấy tờ tùy thân; Rule Engine có thể đối chiếu dữ liệu; Workflow Automation có thể hỗ trợ điền thông tin vào biểu mẫu.

3. **Khả thi về mặt kỹ thuật:** Có thể xây dựng prototype bằng dữ liệu giả lập hoặc dữ liệu đã ẩn danh mà chưa cần tích hợp trực tiếp với PMS thực tế.

4. **Rủi ro có thể kiểm soát:** Áp dụng Human-in-the-Loop để nhân viên lễ tân kiểm tra và phê duyệt. AI không tự quyết định xác minh danh tính, thanh toán hoặc check-in.

5. **Cần kiểm chứng thêm:** Chưa có dữ liệu thực tế để xác định chính xác hiệu quả, chi phí triển khai và khả năng tích hợp với PMS.

## Prototype Scope (Phạm vi thử nghiệm)

**Mục tiêu:** Xây dựng prototype chứng minh khả năng giảm thao tác nhập liệu thủ công trong quy trình check-in.

**Các chức năng cần triển khai:**

1. Nhận hình ảnh giấy tờ tùy thân mẫu.
2. Sử dụng OCR để trích xuất thông tin khách hàng.
3. Đối chiếu thông tin với dữ liệu đặt phòng giả lập.
4. Kiểm tra các trường dữ liệu và hiển thị kết quả đối chiếu.
5. Tự động điền thông tin vào biểu mẫu check-in dạng nháp.
6. Cho phép nhân viên kiểm tra và phê duyệt trước khi hoàn tất.

**Không nằm trong phạm vi Prototype:**

- Không kết nối trực tiếp với PMS đang vận hành.
- Không tự động xác nhận thanh toán.
- Không tự động xác minh danh tính khi có sai lệch.
- Không tự động hoàn tất check-in mà không có sự phê duyệt của nhân viên.

## Production Readiness (Điều kiện trước khi triển khai thực tế)

| STT | Điều kiện | Mục đích |
|---|---|---|
| 1 | Có bộ dữ liệu kiểm thử đa dạng và được cấp phép | Đánh giá OCR trong các điều kiện giấy tờ khác nhau |
| 2 | Đo độ chính xác OCR | Xác định khả năng trích xuất thông tin, mục tiêu tối thiểu 98% |
| 3 | Đo thời gian xử lý thực tế | Kiểm chứng mục tiêu giảm thời gian check-in từ 5 phút xuống dưới 2 phút |
| 4 | Kiểm thử khả năng tích hợp PMS | Đảm bảo việc truy xuất và cập nhật dữ liệu chính xác |
| 5 | Lấy ý kiến nhân viên lễ tân và quản lý | Đánh giá tính phù hợp với quy trình vận hành thực tế |
| 6 | Hoàn thiện bảo mật và quyền riêng tư | Đảm bảo dữ liệu cá nhân của khách hàng được bảo vệ |

## Final Conclusion

**GO cho giai đoạn Prototype, chưa GO cho triển khai Production.**

Giải pháp OCR kết hợp Rule Engine và Workflow Automation có tiềm năng cải thiện quy trình check-in tại Vinpearl bằng cách giảm thao tác xác minh và nhập liệu thủ công. Prototype sẽ tập trung vào việc trích xuất thông tin, đối chiếu dữ liệu giả lập và tạo biểu mẫu check-in nháp có sự phê duyệt của nhân viên.

Chỉ xem xét triển khai thực tế sau khi prototype đạt các chỉ số mục tiêu, được kiểm thử với dữ liệu phù hợp, xác nhận khả năng tích hợp PMS và nhận được sự đồng thuận từ các bên liên quan.

---