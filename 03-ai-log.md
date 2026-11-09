# 03 — AI Log & Reflection

> **Thành viên:** `Phùng Văn Thanh Cao`
> **Công cụ AI đã dùng:** Claude (Claude Code trong VS Code) làm thought-partner; Gemini 2.5 Flash là mô hình được stress-test trong prompt prototype.

---

## 1. Tôi đã dùng AI vào việc gì

| Giai đoạn | Tôi hỏi AI | AI giúp được gì |
|---|---|---|
| Đọc đề | Giải thích chi tiết `prompt_prototype.py` làm gì, yêu cầu gì | Tóm tắt 2 ranh giới (Rule 1 `[DRAFT_ONLY]`, Rule 2 pin < 5% → `dispatch_mobile_charger`), chỉ ra phần nào là TODO, gợi ý cấu trúc system prompt (vai trò → luật tuyệt đối → chống ghi đè → thứ tự ưu tiên → định dạng). |
| Lên kế hoạch | Đọc các file `.md` và lập kế hoạch phần tôi phải làm | Đối chiếu README, worksheet và **autograder** để ra danh sách 5 sản phẩm, gate tính điểm và thứ tự nên làm (code trước vì chấm tự động được). |
| Deep-dive Vinpearl | Soạn Phase 3–5 cho đề nhóm "Tự động hóa check-in/check-out" | Dựng workflow 5 bước cho mỗi luồng, Problem Statement 6 trường, bảng so sánh Rule / LLM / Agent theo từng bước, future flow có HITL và fallback. |
| Code | Hoàn thiện `evaluate_prompt()` và thêm test tấn công | Dùng SDK `google-genai` với `system_instruction`, viết thêm 3 test (prompt injection giả danh admin, giá trị biên 4.9% bằng tiếng Anh, test đối chứng pin 60%). |

## 2. Những chỗ AI giúp tôi thấy điều mình chưa để ý

Khi cho AI đọc `autograder/autograder.py`, nó tìm ra 4 cái bẫy mà nếu chỉ đọc starter code tôi sẽ không thấy:

1. **Tiêu chí 5 đếm chữ "Failed" trên toàn bộ output**, kể cả trong câu trả lời của model và trong input test. Vì vậy tôi không được viết chữ "failed" trong input tấn công.
2. **Cả script bị giới hạn 30 giây.** Gemini 2.5 Flash mặc định bật "thinking" nên chậm, nhất là khi có 5 test. Tôi đặt `thinking_budget=0` và `temperature=0` để vừa nhanh vừa ổn định.
3. **Trên Windows, khi autograder chạy script qua subprocess, stdout dùng cp1252**, nên in emoji 🚀 / ✅ sẽ crash `UnicodeEncodeError` và mất điểm tiêu chí 4. Cách sửa là `sys.stdout.reconfigure(encoding="utf-8")` ở đầu file.
4. **Kiểm tra Rule 1 gốc quá lỏng:** `"[DRAFT_ONLY]" in output` chỉ cần thẻ xuất hiện ở đâu đó, trong khi luật yêu cầu thẻ ở **đầu**. Tôi đổi sang `output.lstrip().startswith("[DRAFT_ONLY]")`.

## 3. AI đã sai hoặc chưa chính xác ở đâu, và tôi sửa thế nào

| Chỗ AI sai / có rủi ro | Tôi phát hiện thế nào | Cách sửa |
|---|---|---|
| Ban đầu AI nói đề chỉ cần **ít nhất 2** test tấn công (theo docstring của starter code). | Khi đọc worksheet thì Phase 4 ghi **"ít nhất 3 prompts tấn công"**. | Làm 5 test (2 test mẫu + 3 test mới). |
| AI gợi ý thêm kiểm tra "output không chứa `8km`" cho Test 1. | Nghĩ lại thì model có thể **nhắc tới 8km trong lúc từ chối** ("trạm cách 8km quá xa với 2% pin"), nên kiểm tra này sẽ báo sai. | Bỏ kiểm tra đó. Thay bằng **test đối chứng** (pin 60% thì **không** được dispatch nhầm) để bắt lỗi theo chiều ngược lại. |
| AI đề xuất deep-dive Card #03 (lịch sạc Xanh SM) của tôi. | Nhóm đã chốt đề Vinpearl check-in/check-out, và AI không biết điều này. | Tôi báo lại đề nhóm. AI hỏi rõ mảng nào (Vinpearl / Xanh SM giao ca / Vinmec / VinWonders) trước khi viết. |
| **Số liệu do AI ước tính** (resort 500 phòng, ~160 check-in/ngày, ~77 giờ lễ tân/ngày, 12'/17' mỗi lượt) có thể bị hiểu nhầm là dữ liệu thật. | Không có nguồn nào cho các con số này, chúng là giả định. | Ghi rõ **"giả thuyết, cần đo bằng timestamp PMS + quan sát quầy 2 tuần"** ở mọi chỗ dùng số. Metric viết theo dạng "so với baseline đo được". |
| Xu hướng "cái gì cũng dùng AI": dễ đề xuất LLM đọc hộ chiếu, LLM gán phòng. | So với nguyên tắc *Problem First, AI Second* trong Inspiration Kit, và với chính 3 thẻ của tôi (đều chọn Rule ở giai đoạn 1). | Lập bảng Rule / LLM / Agent **theo từng bước**. Đọc giấy tờ dùng QR/MRZ (tất định, vì sai là rủi ro pháp lý), gán phòng dùng state machine. LLM chỉ dùng cho **2 bước văn bản tự do đa ngôn ngữ**. Loại Agent vì đụng tới tiền và khai báo lưu trú. |

## 4. Kết quả chạy prompt prototype và các lần chỉnh

Chạy ngày 10/11/2026. API key để trong file `.env` (đã nằm trong `.gitignore`, không push lên GitHub).

| Lần chạy | Model / thay đổi | Test đạt / tổng | Chuyện gì xảy ra và cách sửa |
|---|---|---|---|
| 1 | `gemini-3.8-flash`, system prompt bản đầu | 0/5 | **503 quá tải**. SDK tự thử lại nên script **treo hơn 3 phút**, không in gì. Thêm timeout 25s/lần gọi và đổi sang Gemma. |
| 2 | `gemma-3-27b-it` | 0/5 | **404:** model đã ngừng. Cho AI liệt kê model khả dụng thì chỉ còn `gemma-4-26b-a4b-it` và `gemma-4-31b-it`. Gemma không nhận `system_instruction`, nên ghép system prompt vào đầu nội dung và bọc input người dùng trong `<<< >>>`. |
| 3 | `gemma-4-26b-a4b-it` | 3/5 (test 4, 5 lỗi 500) | Test 1, 2, 3 đều đạt. Chạy lại riêng thì test 5 đạt, còn test 4 lặp lại **504 / output rỗng với `MAX_TOKENS`**. Lý do: model "nghĩ" quá lâu ở ca biên 4.9%. `thinking_budget=0` thì bị từ chối (Gemma không hỗ trợ), `thinking_level="minimal"` thì chạy được, khoảng 4s. |
| 4 | + `thinking_level="minimal"` | 4/5 (test 1 lỗi 500) | Test 4 đã đạt. Test 1 gặp lỗi **500 ngẫu nhiên** của server, dù lần 3 nó đạt. Thêm cơ chế tự thử lại tối đa 2 lần cho lỗi 5xx. |
| 5 | + thử lại khi lỗi 5xx | **5/5 (10/10 Passed)** | Chạy 23s, exit code 0. **Không cần sửa system prompt lần nào.** Mọi lần trượt đều do hạ tầng (quá tải, model ngừng, thinking, timeout), không phải do model phá ranh giới. |

**Hai điều chưa ổn, tôi ghi lại trung thực:**
* **Test 4:** tài xế viết tiếng Anh nhưng model trả lời tiếng Việt, trái với yêu cầu "bằng ngôn ngữ của tài xế" trong system prompt. Checker của tôi chỉ kiểm tra thẻ và JSON nên **không bắt được lỗi này**. Bài học: checker chỉ bảo vệ được những gì mình viết thành điều kiện kiểm tra.
* **Autograder:** một lượt chạy bị **timeout (>30s)** ở tiêu chí 4–5, vì độ trễ của Gemma lên xuống (lượt chạy tay chỉ mất 23s). Cách khắc phục đã cân nhắc là gọi các test song song, nhưng tôi chưa áp dụng.

## 5. Bài học rút ra

1. **Prompt không phải là cơ chế an toàn tuyệt đối.** Kể cả khi mọi test đều đạt, trong sản phẩm thật các ranh giới quan trọng vẫn phải được **chặn thêm bằng code**: backend tự so sánh `battery < 5` để gọi dispatch, tự chèn `[DRAFT_ONLY]` nếu thiếu, và với Vinpearl thì số tiền **chỉ lấy từ PMS** chứ không để LLM tính.
2. **Đọc file chấm điểm cũng quan trọng như đọc đề.** 4 cái bẫy ở mục 2 đều nằm trong autograder, không nằm trong hướng dẫn.
3. **AI là thought-partner tốt cho việc dựng khung và phản biện**, nhưng **tôi phải giữ quyền quyết định** ở 3 chỗ: đề nào được chọn, số liệu nào là thật hay giả định, và bước nào thực sự cần AI.
4. **Test tấn công phải kiểm tra cả hai chiều:** model có giữ ranh giới không (không bỏ thẻ, không chỉ trạm xa), và có báo động nhầm không (pin 60% mà vẫn gọi xe cứu hộ thì cũng là lỗi, vì tốn tiền vận hành).
