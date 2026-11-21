# TEAM — Ngày 12

Mã bộ ảnh: **G01** · Hình thức: cá nhân (ghép cặp review chéo)

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Phạm Lâm Anh | 03029 | có | Phạm Thanh Tùng | 77 dòng |

Ca hai bạn trao đổi kỹ và xin ý kiến coach (ghi tên ảnh + đối tượng):

- `D04.png`, `person.seatbelt`: Trên ảnh NIR thiếu sáng, dải dây an toàn chéo vai có độ tương phản rất thấp so với màu áo sẫm của tài xế. Bạn Tùng chọn `unknown` do không thấy rõ đường biên; bản thân mình ban đầu phân vân giữa `worn_correct` và `unknown`. Sau khi đối chiếu quy tắc 4.4-1 ("Không thấy thì unknown, không suy đoán"), hai bạn thống nhất chọn `unknown`.
- `D01.png` – `D06.png`, `hand.side`: Bạn Tùng ban đầu gán cả 2 tay thành `left` do nhầm chiều màn hình. Mình đã giải thích quy tắc 4.4-2 và 4.7 (trái/phải theo giải phẫu cơ thể của người lái), bạn Tùng đã hiểu và sửa lại.

## Cá nhân

### PhamLamAnh-03029
- **Phần mình làm:** Tự gán đủ 22 ảnh cốt lõi (16 ảnh SVIRO + 6 ảnh Drive&Act); thực hiện chạy script diff và phân tích toàn bộ 77 dòng khác biệt trong `disagreement_log.csv`; chỉnh sửa và export bản v2 đạt chuẩn 0 lỗi.
- **Điều mình học được hôm nay:** 
  1. Tư duy hệ thống gán nhãn xe hơi: Ghế luôn gọi theo xe (camera nhìn ngược thì trái ảnh là phải xe); trái/phải luôn theo cơ thể người dù ảnh bị xoay $90^\circ$.
  2. Sự khác biệt cơ bản giữa ảnh hồng ngoại mô phỏng (IR-sim không có hiệu ứng phản xạ vật lý thật) và ảnh NIR thực tế (chói lóa đèn LED, kính râm trong suốt).
  3. Giá trị của chu trình Tự kiểm tra (Check script) $\rightarrow$ Review chéo (Peer review) $\rightarrow$ Sửa đổi (Rework) để bảo đảm chất lượng dữ liệu huấn luyện AI.
