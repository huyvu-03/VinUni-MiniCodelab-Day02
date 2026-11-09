
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

## 🏛️ Bối cảnh: Tôi là ai?

Tôi là Thắng, AI Engineer tại **Vin Smart Future**. Nhóm chúng tôi được giao nhiệm vụ phối hợp với Khối Vận Hành của **Vinhomes** để tìm kiếm các cơ hội tối ưu hóa bằng trí tuệ nhân tạo. 

Thông qua khảo sát thực địa tại Vinhomes, tôi nhận thấy nhiều vấn đề có thể cải tiến trong quy trình vận hành. Bài toán tôi mang vào buổi Lab hôm nay đến từ chính quan sát thực tế này.
---

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
│ Bài toán (1 câu): Tự động hóa quy trình tiếp nhận, phân loại, chuyển bộ phận và theo dõi xử lý yêu cầu của cư dân Vinhomes nhằm giảm thời gian xử lý, hạn chế bỏ sót yêu cầu và nâng cao chất lượng dịch vụ.  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________
Nhân viên lễ tân / Customer Service tại Ban quản lý.
Nhân viên trực hotline và tiếp nhận phản ánh.
Trưởng bộ phận kỹ thuật, vệ sinh, an ninh và chăm sóc khách hàng.
Ban quản lý dự án (BQL).
Cư dân là người chịu ảnh hưởng cuối cùng khi yêu cầu bị chậm hoặc xử lý sai. │
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
