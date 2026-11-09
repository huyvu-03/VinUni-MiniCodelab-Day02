# 02 — Deep-Dive Report: Tự động hóa check-in tại Vinpearl

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)

## 3.1. Current-State Workflow

Quy trình check-in hiện tại tại quầy lễ tân Vinpearl:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Khách đưa mã │     │ Kiểm tra và  │     │ Đối chiếu    │     │ Nhập/cập nhật│
│ đặt phòng &  │ ──→ │ xác minh     │ ──→ │ booking,     │ ──→ │ dữ liệu vào  │
│ giấy tờ      │     │ giấy tờ      │     │ thanh toán   │     │ PMS          │
│ Ai: Khách/LT │     │ Ai: Lễ tân   │     │ Ai: Lễ tân   │     │ Ai: Lễ tân   │
│ ⏱ 0,5 phút   │     │ ⏱ 1,5 phút 🔴│     │ ⏱ 1 phút 🔴  │     │ ⏱ 1,5 phút 🔴│
│ Out: Hồ sơ   │     │ Out: Dữ liệu │     │ Out: Kết quả │     │ Out: Bản ghi │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Xác nhận và  │
                                                               │ giao thẻ phòng│
                                                               │ Ai: Lễ tân   │
                                                               │ ⏱ 0,5 phút   │
                                                               └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: khoảng 5 phút/khách.
```

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Nhân viên lễ tân Vinpearl; stakeholders gồm khách lưu trú và quản lý vận hành khách sạn. |
| **2. Current Workflow** | Khách đưa mã đặt phòng và giấy tờ; lễ tân xác minh, tra cứu booking/thanh toán, nhập dữ liệu vào PMS, sau đó xác nhận và giao thẻ phòng. 5 bước, mất khoảng 5 phút/khách. |
| **3. Bottleneck** | Bước 2–4 mất khoảng 4 phút: đọc giấy tờ, đối chiếu nhiều nguồn và nhập lại dữ liệu. Ảnh mờ hoặc thông tin không khớp làm tăng thời gian và nguy cơ sai sót. |
| **4. Business Impact** | Hàng chờ tăng vào mùa cao điểm và gây áp lực cho lễ tân. Với baseline 5 phút, một quầy chỉ xử lý lý thuyết khoảng 12 khách/giờ; con số này cần được kiểm chứng bằng log thực tế. |
| **5. Success Metric** | 1. Giảm thời gian check-in xuống **dưới 2 phút**.<br>2. Giảm ít nhất **50%** thời gian nhập liệu thủ công.<br>3. OCR đạt **≥95%** độ chính xác trên tập test; 100% trường hợp không khớp được chuyển cho lễ tân review. |
| **6. Operational Boundary** | Hệ thống được OCR, chuẩn hóa, đối chiếu booking và điền trước biểu mẫu. **CẤM:** tự xác nhận danh tính, sửa booking/thanh toán hoặc kích hoạt thẻ phòng. Lễ tân phải duyệt kết quả cuối cùng (HITL). |

---

## 3.3. Future-State Flow & AI Fit

- **AI Fit:** Chọn **Rule / State-Machine kết hợp OCR**. Quy trình và điều kiện đối chiếu cố định nên không cần LLM hay Agent tự trị; cách này dễ kiểm toán và giảm rủi ro xử lý sai danh tính.
- **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Lễ tân quét  │     │ 🔵 OCR đọc & │     │ 🔵 Rule đối  │     │ 🟢 Lễ tân    │
│ giấy tờ và   │ ──→ │ chuẩn hóa dữ │ ──→ │ chiếu booking│ ──→ │ review, duyệt│
│ mã booking   │     │ liệu         │     │ & thanh toán │     │ và giao thẻ  │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                   │
                                                   ▼
                                            ↩️ Fallback:
                                            OCR confidence thấp,
                                            dữ liệu không khớp hoặc
                                            hệ thống lỗi → lễ tân xử
                                            lý thủ công như quy trình cũ.
```

> Các mốc thời gian và công suất là baseline ước tính từ Quick Problem Card; nhóm cần xác nhận bằng quan sát hoặc log Vinpearl trước khi triển khai.

---
