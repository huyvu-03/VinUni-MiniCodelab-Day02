# 📄 03 — AI Log: Nhật ký tương tác AI

## 1. Mục tiêu sử dụng AI

Trong quá trình thực hiện MiniLab02, mình sử dụng ChatGPT như một trợ lý đồng hành để phân tích bài toán **tự động hóa quy trình Check-in / Check-out tại Vinpearl**.

Mục tiêu của mình không phải là để AI đưa ra toàn bộ giải pháp, mà là tận dụng AI để hỗ trợ tư duy, hệ thống hóa thông tin, nhận diện vấn đề và tìm kiếm hướng cải tiến quy trình vận hành hiện tại.

## 2. AI đã hỗ trợ mình như thế nào?

Trong quá trình làm việc, ChatGPT hỗ trợ mình ở một số khía cạnh:

### 2.1. Phân tích và hệ thống hóa vấn đề

Ban đầu, mình có cái nhìn khá tổng quát về quy trình Check-in / Check-out. AI giúp mình chia nhỏ quy trình thành các bước cụ thể:

1. Khách hàng cung cấp mã đặt phòng hoặc giấy tờ tùy thân.
2. Lễ tân xác minh thông tin khách hàng.
3. Đối chiếu thông tin đặt phòng, thanh toán và dịch vụ.
4. Nhập hoặc cập nhật thông tin trên hệ thống PMS.
5. Xác nhận và bàn giao chìa khóa hoặc hoàn tất thủ tục.

Nhờ đó, mình có thể hình dung rõ hơn cách quy trình vận hành và xác định những công đoạn cần được phân tích sâu hơn.

### 2.2. Nhận diện điểm nghẽn (Bottleneck)

AI giúp mình xem xét từng bước để xác định những công đoạn có khả năng tiêu tốn nhiều thời gian hoặc cần nhiều thao tác thủ công.

Ba công đoạn đáng chú ý là:

- **Bước 2:** Xác minh thông tin khách hàng.
- **Bước 3:** Đối chiếu thông tin đặt phòng và thanh toán.
- **Bước 4:** Nhập liệu và cập nhật thông tin trên PMS.

Đây là những vị trí có khả năng phát sinh thời gian chờ, sai sót nhập liệu hoặc phải trao đổi qua lại giữa nhân viên và hệ thống.

### 2.3. Tìm kiếm hướng ứng dụng AI

Từ những điểm nghẽn trên, AI gợi ý một số hướng ứng dụng:

- OCR: Hỗ trợ trích xuất thông tin từ giấy tờ tùy thân.
- Rule Engine: Kiểm tra thông tin theo các điều kiện nghiệp vụ.
- Workflow Automation: Hỗ trợ tự động hóa thao tác tra cứu và cập nhật dữ liệu.
- AI Assistant: Hỗ trợ nhân viên tra cứu thông tin và xử lý các tình huống thường gặp.

Những gợi ý này giúp mình có thêm cơ sở để thảo luận về khả năng cải tiến quy trình với các thành viên trong nhóm.

## 3. Những hạn chế và sai lệch của AI

Mặc dù hữu ích, mình nhận thấy AI có thể đưa ra những câu trả lời nghe rất hợp lý nhưng chưa chắc đã chính xác.

### 3.1. Tự suy diễn số liệu

Khi phân tích thời gian xử lý, AI đề xuất một baseline khoảng 5 phút/khách, được chia thành thời gian cho từng công đoạn.

Tuy nhiên, đây chỉ là con số ước tính để phục vụ việc mô phỏng và phân tích, không phải dữ liệu đo lường thực tế tại Vinpearl.

Nếu không kiểm tra, mình có thể vô tình trình bày những con số này như dữ liệu chính thức.

**Cách khắc phục:** Yêu cầu AI phân biệt rõ số liệu thực tế, giả định và ước tính. Những thông tin chưa có nguồn xác minh phải được ghi chú rõ ràng.

### 3.2. Giả định về hệ thống vận hành

AI có xu hướng đề xuất việc kết nối trực tiếp với PMS để tự động tra cứu và cập nhật thông tin.

Tuy nhiên, mình chưa có tài liệu xác nhận Vinpearl đang sử dụng hệ thống PMS nào, hệ thống có API hay không và khả năng tích hợp thực tế ra sao.

**Cách khắc phục:** Giới hạn AI chỉ phân tích ở mức quy trình nghiệp vụ và đề xuất giải pháp tiềm năng. Không khẳng định một công nghệ hoặc hệ thống cụ thể đang được Vinpearl sử dụng nếu chưa có bằng chứng.

### 3.3. Đề xuất tự động hóa quá mức

Một số hướng tiếp cận có thể khiến mình hiểu rằng AI có thể tự động xác minh danh tính, kiểm tra thanh toán và phê duyệt thủ tục nhận phòng.

Tuy nhiên, đây là những nghiệp vụ quan trọng, liên quan trực tiếp đến thông tin cá nhân và quyền lợi của khách hàng.

**Cách khắc phục:** Xác định rõ AI chỉ đóng vai trò hỗ trợ. Nhân viên vẫn phải kiểm tra và xác nhận những thông tin quan trọng, đặc biệt khi dữ liệu không khớp hoặc hệ thống phát hiện bất thường.

## 4. Điều chỉnh Prompt để đạt kết quả tốt hơn

Qua quá trình tương tác, mình nhận ra rằng chất lượng câu trả lời phụ thuộc rất nhiều vào cách đặt câu hỏi.

Thay vì đưa ra một yêu cầu chung chung như:

> Hãy đề xuất giải pháp AI để tối ưu quy trình Check-in / Check-out tại Vinpearl.

Mình điều chỉnh prompt theo hướng cụ thể và có giới hạn hơn:

**Prompt đã điều chỉnh:**

> Hãy phân tích quy trình Check-in / Check-out dựa trên 5 bước nghiệp vụ đã cung cấp.
>
> Với mỗi bước, hãy xác định người thực hiện, thời gian xử lý ước tính, đầu vào, đầu ra và điểm chuyển giao (Handoff).
>
> Đánh dấu các công đoạn có khả năng trở thành Bottleneck và giải thích nguyên nhân.
>
> Không tự tạo dữ liệu hoặc khẳng định các thông tin chưa được xác minh là quy trình chính thức của Vinpearl.
>
> Khi đề xuất ứng dụng AI, hãy phân biệt rõ công việc có thể tự động hóa và công việc cần nhân viên kiểm tra hoặc phê duyệt.

**Những thay đổi mình đã thực hiện:**

- Cung cấp bối cảnh và quy trình cụ thể thay vì hỏi quá rộng.
- Chia yêu cầu lớn thành từng nhiệm vụ nhỏ.
- Yêu cầu AI giải thích nguyên nhân thay vì chỉ đưa ra kết luận.
- Phân biệt dữ liệu thực tế với giả định.
- Đặt giới hạn cho những nội dung AI chưa có đủ thông tin để kết luận.

## 5. Ranh giới khi sử dụng AI

Mình xác định một số nguyên tắc để sử dụng AI có trách nhiệm:

| Nội dung | Ranh giới sử dụng |
|---|---|
| Phân tích quy trình | AI được phép hỗ trợ phân tích và đề xuất |
| Dữ liệu vận hành | Phải kiểm chứng, không mặc định tin số liệu AI đưa ra |
| Thông tin khách hàng | Không cung cấp dữ liệu cá nhân thật cho AI |
| Xác minh danh tính | Không giao toàn bộ quyết định cho AI |
| Thanh toán | Không để AI tự phê duyệt giao dịch |
| Cập nhật PMS | Cần phân quyền và xác nhận của nhân viên |
| Quyết định nghiệp vụ | Con người chịu trách nhiệm cuối cùng |

## 6. Kết luận và bài học cá nhân

Qua MiniLab02, mình nhận thấy AI là một công cụ hữu ích giúp tiết kiệm thời gian tìm kiếm ý tưởng, hệ thống hóa thông tin và nhìn nhận vấn đề từ nhiều góc độ khác nhau.

Tuy nhiên, AI không phải lúc nào cũng đưa ra câu trả lời chính xác. Một câu trả lời được trình bày rõ ràng và có vẻ thuyết phục vẫn có thể chứa những giả định chưa được kiểm chứng.

Bài học lớn nhất mình rút ra là **không nên chỉ học cách đặt câu hỏi cho AI mà còn phải học cách kiểm tra và phản biện câu trả lời của AI**.

Mình cần chủ động cung cấp đủ bối cảnh, giới hạn phạm vi yêu cầu, kiểm chứng thông tin quan trọng và giữ quyền quyết định cuối cùng ở con người.

Đối với mình, AI nên là một người trợ lý giúp nâng cao khả năng tư duy và làm việc, chứ không phải công cụ thay thế hoàn toàn tư duy của chính mình.