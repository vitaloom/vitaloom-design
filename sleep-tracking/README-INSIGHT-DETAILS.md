# VitaLoom F2 — Insight Detail Visual Baselines

9 màn hình thiết kế riêng theo [insight-catalog-v2.md](https://github.com/vitaloom/vitaloom-business-docs-and-tools/blob/main/docs/usecase_spec/sleep-tracking/f2-sleep-goals-insights/insight-catalog-v2.md).

- A01: Recording Coverage — lịch 7 ngày có/thiếu MAIN.
- A02: Goal Achievement — ngày MAIN đạt Goal hiệu lực / ngày đủ điều kiện.
- A03: Duration Trend — hai kỳ 7 ngày **đã kết thúc**, chênh lệch phút.
- A04: Bedtime/Wake Variation — hai biên độ giờ ngủ và giờ thức, Main RANGE cùng timezone.
- A05: Weekday/Weekend Duration — hai trung bình mẫu ngày thường/cuối tuần.
- B01: Feeling Distribution — tỷ lệ 3 cảm nhận theo MAIN có feeling.
- B02: Duration vs Feeling — so sánh 2 nhóm Dễ chịu và Mệt mỏi, >=3/nhóm.
- B03: Feeling Trend — hai biểu đồ phân bố 100% trên 2 kỳ đã kết thúc, chênh lệch điểm %.
- B04: Long-duration Tired Exceptions — MAIN >= Goal ngày đó nhưng feeling Mệt mỏi.

**Lưu ý:** Các con số trên 9 màn hình là dữ liệu mô phỏng độc lập, không đảm bảo đồng nhất giữa các mockup. Các điều kiện READY, period, số mẫu, consent và evidence được xác thực ở Backend khi triển khai. Trạng thái Locked, Empty, Unverified và AI loading sẽ cần biến thể giao diện bổ sung. UI không tạo phán đoán y khoa, không hiểu ngày chưa ghi nhận là 0 giờ ngủ.

**Visual:** Soft Wellness green / mint, purple accents restrained. Files PNG 941 × 1672 px, từng ảnh độc lập.

Giải nén các file PNG trực tiếp vào `vitaloom-design/sleep-tracking/`. Giữ các file thiết kế cũ để truy vết cho đến khi update manifest.
