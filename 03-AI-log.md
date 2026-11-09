# 03 — AI Log: Nhật ký tương tác AI

## 1. Mục tiêu sử dụng AI

Trong quá trình thực hiện MiniLab02, tôi sử dụng ChatGPT như một trợ lý để phân tích quy trình **Check-in / Check-out tại Vinpearl**.

Mục tiêu là nhờ AI hỗ trợ tìm hiểu quy trình, phát hiện những bước còn mất nhiều thời gian và đề xuất hướng cải tiến bằng công nghệ AI. Tôi vẫn chủ động xem xét và lựa chọn những đề xuất phù hợp.

## 2. AI đã hỗ trợ tôi như thế nào?

### 2.1. Phân tích quy trình

AI giúp tôi chia quy trình Check-in / Check-out thành 5 bước chính:

1. Khách cung cấp thông tin đặt phòng và giấy tờ tùy thân.
2. Lễ tân xác minh thông tin khách hàng.
3. Kiểm tra đặt phòng và thanh toán.
4. Cập nhật thông tin lên hệ thống quản lý khách sạn (PMS).
5. Bàn giao chìa khóa hoặc hoàn tất thủ tục trả phòng.

Nhờ đó, tôi hiểu rõ hơn các bước công việc và cách chúng liên kết với nhau.

### 2.2. Tìm ra những điểm mất thời gian

AI giúp tôi nhận diện 3 bước có khả năng mất nhiều thời gian:

- Xác minh thông tin khách hàng.
- Kiểm tra thông tin đặt phòng và thanh toán.
- Nhập và cập nhật dữ liệu trên hệ thống.

Đây cũng là những bước có thể phát sinh sai sót hoặc phải thực hiện nhiều thao tác thủ công.

### 2.3. Đề xuất giải pháp

Từ những vấn đề trên, AI gợi ý một số giải pháp:

- **OCR:** Đọc và trích xuất thông tin từ giấy tờ tùy thân.
- **Rule Engine:** Kiểm tra thông tin theo các quy tắc có sẵn.
- **Workflow Automation:** Tự động hóa một số thao tác lặp lại.
- **AI Assistant:** Hỗ trợ nhân viên tra cứu và giải đáp các tình huống thường gặp.

Những gợi ý này giúp tôi có thêm ý tưởng để thảo luận và lựa chọn giải pháp cho bài tập.

## 3. Những hạn chế của AI

Trong quá trình sử dụng, tôi nhận thấy AI vẫn có thể đưa ra thông tin chưa chính xác.

**Thứ nhất, AI có thể tự đưa ra số liệu.**

Ví dụ, AI đề xuất thời gian xử lý trung bình khoảng 5 phút/khách. Tuy nhiên, đây chỉ là số liệu giả định, chưa được đo lường thực tế tại Vinpearl.

**Thứ hai, AI có thể tự giả định về hệ thống.**

AI đề xuất kết nối trực tiếp với PMS nhưng tôi chưa có thông tin xác nhận về phần mềm Vinpearl đang sử dụng hoặc khả năng kết nối của hệ thống.

**Thứ ba, AI có thể đề xuất tự động hóa quá mức.**

Những công việc như xác minh danh tính, kiểm tra thanh toán và xác nhận nhận phòng vẫn cần nhân viên kiểm tra và chịu trách nhiệm.

Để khắc phục, tôi cần kiểm chứng thông tin, phân biệt rõ giả định với dữ liệu thực tế và không giao toàn bộ quyết định quan trọng cho AI.

## 4. Điều chỉnh cách đặt Prompt

Ban đầu, tôi đặt câu hỏi khá chung chung:

> Hãy đề xuất giải pháp AI để tối ưu quy trình Check-in / Check-out tại Vinpearl.

Sau đó, tôi điều chỉnh câu hỏi cụ thể hơn:

**Prompt sau khi điều chỉnh:**

> Hãy phân tích quy trình Check-in / Check-out dựa trên 5 bước nghiệp vụ đã cung cấp.
>
> Với mỗi bước, hãy xác định người thực hiện, công việc, đầu vào, đầu ra và thời gian xử lý ước tính.
>
> Chỉ ra những bước có khả năng mất nhiều thời gian và giải thích nguyên nhân.
>
> Đề xuất giải pháp AI phù hợp, nhưng phải phân biệt công việc có thể tự động hóa và công việc cần nhân viên kiểm tra.
>
> Không tự tạo số liệu hoặc khẳng định những thông tin chưa được xác minh là thực tế tại Vinpearl.

Qua đó, tôi nhận thấy khi cung cấp bối cảnh rõ ràng và đặt yêu cầu cụ thể, kết quả AI đưa ra sẽ hữu ích hơn.

## 5. Nguyên tắc sử dụng AI

Tôi đặt ra một số nguyên tắc khi sử dụng AI trong bài toán này:

| Nội dung | Nguyên tắc |
|---|---|
| Phân tích quy trình | AI hỗ trợ phân tích và đề xuất |
| Số liệu | Phải kiểm tra trước khi sử dụng |
| Thông tin khách hàng | Không đưa dữ liệu cá nhân thật vào AI |
| Xác minh danh tính | Nhân viên chịu trách nhiệm |
| Thanh toán | Không để AI tự phê duyệt |
| Cập nhật PMS | Cần kiểm soát quyền truy cập |
| Quyết định cuối cùng | Do con người thực hiện |

## 6. Kết luận và bài học cá nhân

Qua MiniLab02, tôi hiểu rõ hơn cách sử dụng AI để hỗ trợ giải quyết một bài toán thực tế.

AI giúp tôi tiết kiệm thời gian, phân tích vấn đề có hệ thống và tìm ra những hướng cải tiến mà ban đầu có thể chưa nghĩ đến.

Tuy nhiên, tôi cũng nhận ra không phải câu trả lời nào của AI cũng chính xác. Có những thông tin nghe rất hợp lý nhưng thực chất chỉ là giả định.

**Bài học quan trọng nhất của tôi là: Không chỉ biết cách hỏi AI mà còn phải biết kiểm tra và phản biện câu trả lời của AI.**

Tôi xem AI là công cụ hỗ trợ tư duy và nâng cao hiệu quả công việc, còn việc đánh giá và đưa ra quyết định cuối cùng vẫn thuộc về con người.