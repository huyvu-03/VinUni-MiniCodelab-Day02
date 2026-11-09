# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

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
|1.|Vinhomes|Lặp lại |Nhân viên phải lặp đi lặp lại việc đọc, phân loại và chuyển tiếp hàng trăm yêu cầu cư dân từ hotline, email, app và Zalo mỗi ngày.|
|2.|Vinhomes|Tốn thời gian|Đội vận hành mất nhiều thời gian kiểm tra thiết bị kỹ thuật (thang máy, HVAC, điện nước), tổng hợp dữ liệu và lập kế hoạch bảo trì thủ công.|
|3.|Vinhomes|AI có thể làm tốt hơn|Quy trình đối soát điện, nước và phí dịch vụ hiện phụ thuộc Excel và nhập liệu thủ công; AI có thể tự đọc công tơ, phát hiện bất thường và nhắc thanh toán chính xác hơn.|
|4.|Vinhomes|AI có thể làm tốt hơn|Việc giám sát hàng trăm camera CCTV bằng con người dễ bỏ sót sự cố; AI có thể tự động phát hiện khói, xâm nhập trái phép hoặc hành vi bất thường theo thời gian thực.|
|5.|Vinhomes|Pain từ người khác|Cư dân và nhà thầu thường phàn nàn về việc nghiệm thu căn hộ chậm, lỗi bị bỏ sót hoặc phải sửa chữa nhiều lần trước khi bàn giao.|
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu): Tự động hóa quy trình tiếp nhận, phân loại,
│ chuyển bộ phận và theo dõi xử lý yêu cầu của cư dân Vinhomes│
│nhằm giảm thời gian xử lý, hạn chế bỏ sót yêu cầu và nâng cao│
│chất lượng dịch vụ.                                          │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│- Nhân viên lễ tân / Customer Service tại Ban quản lý.       │
│- Nhân viên trực hotline và tiếp nhận phản ánh.              │
│- Trưởng bộ phận kỹ thuật, vệ sinh, an ninh và CS.           │
│- Ban quản lý dự án (BQL).                                   │
│- Cư dân là người chịu ảnh hưởng cuối cùng khi yêu cầu bị    │
│chậm hoặc xử lý sai.                                         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi yêu cầu qua hotline, ứng dụng, email, Zalo hoặc trực tiếp tại quầy.
──> 2. Nhân viên tiếp nhận đọc nội dung, ghi chép và nhập thông tin vào hệ thống/Excel. 
──> 3. Nhân viên phân loại yêu cầu và xác định bộ phận chịu trách nhiệm. 
──> 4. Chuyển yêu cầu cho bộ phận liên quan, theo dõi tiến độ và nhắc xử lý.
──> 5. Nhận kết quả, liên hệ cư dân xác nhận, cập nhật trạng thái và đóng yêu cầu.                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? 
Bước 2 và 3: Đọc, nhập liệu, phân loại và chuyển yêu cầu. 
(⏱ 5-10 phút/lượt)      │
Có thể phát sinh: nhập trùng, phân loại sai, chuyển nhầm bộ phận, thiếu thông tin, bỏ sót yêu cầu.

│ AI có thể nhảy vào hỗ trợ ở bước nào?
Bước 1: AI tiếp nhận đa kênh, chuyển giọng nói thành văn bản, trích xuất thông tin từ ảnh/video.
Bước 2: NLP/LLM tự động tóm tắt nội dung và tạo ticket.
Bước 3: AI phân loại yêu cầu, xác định mức độ ưu tiên, bộ phận xử lý và SLA.
Bước 4: Agent tự động chuyển ticket, theo dõi trạng thái, nhắc việc và cảnh báo quá hạn.
Bước 5: AI soạn phản hồi, tổng hợp kết quả; nhân viên xác nhận trước khi đóng các trường hợp cần kiểm tra.│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
Thời gian tiếp nhận và phân loại: 8 phút → dưới 2 phút/yêu cầu.
Tỷ lệ phân loại đúng: đạt từ 95%.
Tỷ lệ yêu cầu được tạo ticket tự động: đạt từ 90%.
Tỷ lệ yêu cầu bị bỏ sót: giảm ít nhất 80%.
Thời gian điều phối đến đúng bộ phận: giảm ít nhất 50%.
Tỷ lệ yêu cầu xử lý đúng SLA: tăng ít nhất 15 điểm phần trăm so với baseline.
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [x] Agent
 │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                      │
│                                                             │
│ Bài toán (1 câu): Tự động hóa quy trình thu thập chỉ số công tơ, tính toán chi phí điện nước, lập thông báo phí dịch vụ, đối soát thanh toán và theo dõi công nợ nhằm giảm thời gian xử lý, sai sót dữ liệu và thất thoát doanh thu tại Vinhomes.
  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│Nhân viên kế toán dịch vụ.
Nhân viên kỹ thuật ghi chỉ số công tơ.
Ban quản lý tòa nhà.
Bộ phận tài chính và quản lý công nợ.
Cư dân/khách hàng thuê căn hộ.
                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Thu thập chỉ số điện, nước từ công tơ hoặc BMS. 
──> 2. Nhập Excel/phần mềm và đối chiếu chỉ số kỳ trước. 
──> 3. Tính sản lượng, áp dụng biểu giá điện, nước và phí dịch vụ.
──> 4. Đối chiếu thông báo phí, hợp đồng, thanh toán và công nợ.
──> 5. Lập thông báo thanh toán, gửi cư dân, nhắc nợ và báo cáo.                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? 
Bước 1, 2 và 4: Thu thập, nhập liệu và đối soát.
___ (⏱ 4-8 phút/can ho/ky)      │
Lỗi thường gặp: Đọc sai công tơ, nhập nhầm mã căn, sai biểu giá, thiếu/trùng dữ liệu, bỏ sót thanh toán

│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
OCR/Vision Agent: Đọc ảnh công tơ, nhận diện mã đồng hồ và chỉ số.
Data Validation Agent: Phát hiện dữ liệu thiếu, trùng, sai lệch.
Billing Engine: Tính phí theo biểu giá và hợp đồng đã cấu hình.
Reconciliation Agent: Đối chiếu chỉ số, thông báo phí, giao dịch thanh toán và công nợ.
Report Agent: Tạo thông báo phí, báo cáo công nợ và nhắc thanh toán. 
                                                          │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│ Thời gian nhập và kiểm tra chỉ số: 5 phút → dưới 1 phút/công tơ.
Độ chính xác OCR: ≥98% với ảnh đạt chuẩn.
Tỷ lệ dữ liệu tự động đối soát: ≥90%.
Thời gian lập thông báo phí: giảm ≥70%.
Sai sót nhập liệu: giảm ≥80%.
Thời gian tổng hợp công nợ: giảm ≥70%.
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                     │
│                                                             │
│ Bài toán (1 câu): Ứng dụng AI Computer Vision để tự động giám sát hệ thống camera CCTV, phát hiện hành vi và sự kiện bất thường, cảnh báo nhân viên an ninh và hỗ trợ truy xuất video nhằm giảm thời gian giám sát thủ công và nâng cao khả năng phản ứng sự cố tại Vinhomes.
  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│ Nhân viên trực phòng điều khiển an ninh CCTV.
Nhân viên bảo vệ tại các tòa nhà và khu đô thị.
Trưởng bộ phận an ninh.
Ban quản lý dự án.
Cư dân và khách hàng sử dụng tiện ích.
                                                            │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhân viên an ninh theo dõi nhiều màn hình camera tại phòng điều khiển.
2. Phát hiện sự cố qua quan sát trực tiếp hoặc nhận thông tin phản ánh từ cư dân.
3. Xác định camera, khu vực, thời điểm và kiểm tra lại video.
4. Liên hệ bộ phận bảo vệ hoặc nhân viên phụ trách để xác minh và xử lý hiện trường.
5. Trích xuất video, lập biên bản, báo cáo và lưu hồ sơ sự cố. 
                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 và 3: Theo dõi nhiều camera và tìm kiếm video khi xảy ra sự cố.
Thời gian giả định: 10–30 phút/sự cố để xác định và truy xuất đoạn video liên quan.

Rủi ro:
Bỏ sót sự kiện khi nhân viên phải quan sát nhiều màn hình.
Phản ứng chậm khi sự cố xảy ra ngoài tầm quan sát trực tiếp.
Tốn thời gian tìm kiếm video theo camera và mốc thời gian.
Khó tổng hợp dữ liệu sự cố giữa nhiều camera và khu vực.
Báo cáo không đồng nhất, thiếu dữ liệu chứng minh.      │
│ 
AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
Computer Vision Agent: Phân tích luồng video, phát hiện sự kiện như xâm nhập khu vực cấm, tụ tập bất thường, khói/lửa, phương tiện dừng đỗ sai quy định.
Event Detection Agent: Xác định thời gian, camera, vị trí và loại sự kiện.
Alert Agent: Tự động gửi cảnh báo đến nhân viên an ninh qua hệ thống quản lý.
Video Search Agent: Tìm kiếm video theo thời gian, địa điểm và mô tả sự kiện bằng ngôn ngữ tự nhiên.
Incident Report Agent: Tổng hợp bằng chứng video, tạo báo cáo sự cố và theo dõi kết quả xử lý.│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│ Thời gian phát hiện sự kiện: giảm từ 5 phút xuống dưới 30 giây đối với sự kiện AI hỗ trợ phát hiện.
Thời gian tìm kiếm video: 15 phút → dưới 3 phút/sự cố.
Độ chính xác phát hiện (Precision): ≥90% trên các nhóm sự kiện được kiểm thử.
Tỷ lệ cảnh báo giả: ≤10% trên bộ dữ liệu pilot.
Thời gian lập báo cáo sự cố: giảm ≥70%.
Tỷ lệ sự kiện được ghi nhận và chuyển xử lý đúng quy trình: ≥95%.
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```
> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
