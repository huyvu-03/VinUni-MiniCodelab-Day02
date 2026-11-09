# 03 — AI Log & Reflection

ChatGPT đã được sử dụng như một thought-partner để áp dụng 4 lenses, mở rộng năm bài toán VinFast, hoàn thiện ba Quick Problem Cards và đề xuất ma trận chấm điểm nhằm so sánh ý tưởng theo tác động, dữ liệu, tính khả thi và khả năng đo lường. 
AI giúp cấu trúc workflow, gợi ý giải pháp và KPI nhanh, nhưng các số liệu về thời gian xử lý, 
độ chính xác và tác động kinh doanh chỉ là giả định, không phải dữ liệu vận hành đã được VinFast/Vinpearl 
xác nhận; một số gợi ý ban đầu cũng thiên về LLM dù rule-based automation có thể phù hợp hơn => điều chỉnh prompt để yêu cầu AI ghi rõ giả định, so sánh Rule–LLM–Agent, ưu tiên PoC có dữ liệu thực tế và không tự đưa ra quyết định rủi ro. 
Với bài toán check-in Vinpearl được nhóm chọn, đã bổ sung ranh giới bắt buộc như `[DRAFT_ONLY]`, Human-in-the-loop, OCR confidence dưới 95% phải chuyển `manual_review`, không tự sửa booking/thanh toán hoặc kích hoạt thẻ phòng, và luôn fallback về quy trình thủ công. Kết quả AI được dùng để hỗ trợ phân tích, còn lựa chọn cuối cùng và việc kiểm chứng số liệu vẫn do nhóm chịu trách nhiệm.
