# Exit ticket — Ngày 12

Làm cá nhân, không mở slide, khoảng 10 phút. Ghi đáp án ngay dưới mỗi câu.

**Họ tên:** Phạm Lâm Anh · **Mã:** G01 · **MSSV:** 03029

---

**Câu 1 · Chọn một.** Camera DMS trên nhiều xe tự chiếu đèn LED cận hồng ngoại khoảng 940 nm lên mặt tài xế. Lý do chính là gì?

- A. Để đo nhiệt độ da và phát hiện tài xế bị sốt
- B. Để có ảnh mặt ổn định cả ngày lẫn đêm mà không làm chói mắt tài xế
- C. Để có ảnh màu đẹp hơn cho cuộc gọi video
- D. Để camera nhìn xuyên qua mọi loại kính râm

Đáp án: **B**

*Giải thích:* Bước sóng 940 nm thuộc dải cận hồng ngoại (NIR), nằm ngoài vùng quang phổ khả kiến của mắt người nên hoàn toàn vô hình, không gây chói mắt hay phân tâm cho tài xế khi lái xe ban đêm, đồng thời cung cấp nguồn sáng chủ động liên tục giúp camera thu được hình ảnh khuôn mặt ổn định trong mọi điều kiện ánh sáng môi trường.

---

**Câu 2 · Số, 2 chữ số thập phân.** Camera DMS chạy 30 khung hình/giây. Model ước lượng yaw của đầu tài xế lớn hơn 30° liên tục từ khung hình số 240 đến khung hình số 314, **tính cả khung 240 và khung 314**. Tài xế không nhìn đường trong bao nhiêu giây?

Đáp án: **2.50 s**

*Giải thích chi tiết:*
- Số khung hình tài xế quay đầu liên tục: $N = 314 - 240 + 1 = 75$ khung hình.
- Thời gian tài xế không nhìn đường: $t = \frac{75}{30} = 2.50$ giây.

---

**Câu 3 · Chọn tất cả đáp án đúng.** Những câu nào đúng về dữ liệu cabin so với dữ liệu camera ngoài xe?

- A. Không thể làm mờ mặt tài xế như làm mờ mặt người qua đường, vì model DMS cần chính khuôn mặt.
- B. Ban đêm, ảnh cabin thường là ảnh hồng ngoại đen trắng, nên thuộc tính màu áo không gán được.
- C. Camera OMS nhìn về phía sau xe, nên ghế ở bên trái ảnh là ghế bên phải của xe.
- D. Vật trong cabin thường ở xa và nhỏ, nhiều vật trong một ảnh.
- E. Cảnh cabin cố định nên không cần guideline hay QC riêng.

Đáp án: **A, B, C**

*Giải thích chi tiết:*
- **A đúng:** Thuật toán DMS bắt buộc phải phân tích cử động mi mắt, con ngươi và khóe miệng nên không thể làm mờ mặt như bảo vệ quyền riêng tư ngoài đường.
- **B đúng:** Camera NIR ban đêm ghi nhận phổ đơn sắc theo độ phản xạ hồng ngoại, mất hoàn toàn thông tin màu sắc khả kiến nên không thể gán nhãn màu áo.
- **C đúng:** Vị trí camera OMS đặt trên kính lái nhìn ngược về khoang sau xe, do đó bên trái khung hình chính là ghế bên phải của thân xe (`rear_right`).
- **D sai:** Không gian cabin ô tô là cự ly cực gần (chỉ từ 0.5 m đến 1.5 m), đối tượng chiếm tỷ lệ khung hình lớn chứ không phải ở xa và nhỏ.
- **E sai:** Cabin có mức độ phức tạp rất cao về góc che khuất, bóng đổ, phụ kiện người ngồi nên càng đòi hỏi guideline chi tiết và quy trình QC chặt chẽ.
