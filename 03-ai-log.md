---
noteId: "dfa55430dc4e11f19dea45db7655599f"
tags: []

---

# Nhật Ký Tương Tác AI (AI Log & Reflection)

**Người viết:** Vương Quang Thắng
**Dự án:** Hệ thống AI Hỗ trợ Check-in cho Vinpearl
**Công cụ:** Gemini 2.5 Flash / ChatGPT

### 1. AI đã hỗ trợ tôi như thế nào?
Tôi đã sử dụng AI như một "nhà phản biện kỹ thuật" (Technical Sounding Board) qua các giai đoạn:
* **Phase 1-3 (Scan & Deep-Dive):** AI gợi ý tôi hướng góc nhìn (Lenses) vào luồng Tiền sảnh (Front-desk). Nhờ đó, tôi xác định được điểm nghẽn (bottleneck) không nằm ở khách hàng, mà ở việc Lễ tân tốn quá nhiều thời gian gõ lại thông tin từ giấy tờ vào hệ thống PMS.
* **Phase 4 (Prototyping):** AI hỗ trợ tạo System Prompt chuẩn định dạng JSON và đề xuất các kịch bản kiểm thử (Adversarial test) cực kỳ thực tế như ảnh lóa sáng hay đưa sai thẻ.

### 2. Sai sót của AI (Hallucination) và cách khắc phục
* **Ảo giác "Tự động hóa hoàn toàn":** AI ban đầu đề xuất Kiosk tự quét giấy tờ và nhả thẻ phòng. Tôi phải thiết lập ngay **Operational Boundary (Ranh giới vận hành)**, ép AI tuân thủ cơ chế **Human-in-the-loop (HITL)** — Lễ tân phải là người duyệt cuối cùng để tuân thủ luật lưu trú tại Việt Nam.
* **Bỏ sót ngoại lệ (Edge Cases):** AI mặc định xử lý mọi thẻ có chữ/ảnh. Tôi đã phải bổ sung các lệnh cấm (Negative Constraints) để hệ thống từ chối các loại giấy tờ không hợp lệ (như Thẻ sinh viên).

### 3. Bài học rút ra (Key Takeaways)
Nguyên tắc cốt lõi khi làm Product Scoping: **"Problem First, AI Second & Boundary is Everything"**.
Công nghệ OCR/Vision LLM hiện nay đã rất mạnh, nhưng ranh giới vận hành (Operational Boundary) và cơ chế chốt chặn của con người mới là yếu tố quyết định. Không có ranh giới rõ ràng, một AI giúp tiết kiệm thời gian hoàn toàn có thể biến thành thảm họa rủi ro pháp lý cho hệ thống.