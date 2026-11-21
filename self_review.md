# Tự đánh giá — Phạm Lâm Anh · G01

## 1. Tự rà soát 4 cảnh

Rà soát lại bài gán nhãn của mình trên 4 ảnh đại diện (2 ảnh OMS SVIRO và 2 ảnh DMS Drive&Act):

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| `S02_ir.png` | `person` (vùng nôi sơ sinh) | `extra` | Nhìn nhầm hoa văn vải bọc nôi em bé thành trẻ em ngồi và vẽ thêm box `person` (trong khi SVIRO quy định không có trẻ em ngồi). | Đã sửa (xóa box thừa trong v2). |
| `S04_ir.png` | `person` & `object` | `seat_flip` | Khi sao chép các shape từ ảnh màu `S04_rgb` sang ảnh hồng ngoại `S04_ir`, quên mở mục DETAILS để chọn lại thuộc tính `seat` nên bị giữ giá trị mặc định đầu danh sách (`driver`). | Đã sửa (đổi lại `rear_middle` và `rear_right`). |
| `D01.png` | `face13` & `hand` | `ok` | 13 điểm mốc khuôn mặt kéo chuẩn trên ảnh xoay 90°, mắt trái nằm thấp hơn mắt phải (toạ độ y lớn hơn); phân biệt đúng tay trái/tay phải theo người lái. | Đúng chuẩn từ đầu. |
| `D03.png` | `frame_meta` | `missing` | Bắt tay vào vẽ box người và mặt ngay mà quên bấm đặt tag `frame_meta` đầu tiên cho ảnh. | Đã sửa (bổ sung tag `frame_meta: ir`). |

---

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

- **Lỗi:** Quên cập nhật lại các trường thuộc tính trong tab DETAILS của thanh đối tượng bên phải sau khi vẽ mới hoặc copy box từ ảnh RGB sang ảnh IR (khiến CVAT tự gán giá trị mặc định đầu danh sách như `seat = driver`, `occupied = yes`).
- **Vì sao mình mắc:** Thao tác vẽ nhanh trên canvas và chuyển ảnh liên tục bằng phím tắt mà không chú ý kiểm tra thanh thuộc tính bên phải ngay sau khi tạo shape.
- **Lần sau tránh bằng cách:** 
  1. Tuân thủ nghiêm ngặt quy trình 4 bước: Đặt tag `frame_meta` $\rightarrow$ Vẽ box $\rightarrow$ Mở DETAILS kiểm tra thuộc tính $\rightarrow$ Nhấn `Ctrl+S` lưu dữ liệu.
  2. Luôn chạy script kiểm tra `cabin_check.py` ngay ở từng checkpoint (Checkpoint A, Checkpoint B) để phát hiện sớm các lỗi thuộc tính lặp lại trước khi gán hàng loạt.

---

## 3. Ghi chú về disagreement_log

- **Một dòng bạn của mình đúng và mình sai:** Dòng ảnh `D03.png` (và `D05.png`, `D06.png`), trường `frame_meta`. Bạn Phạm Thanh Tùng đã đặt đầy đủ tag `frame_meta` cho toàn bộ 22 khung hình, trong khi bản export đầu tiên của mình bị sót tag này ở 3 ảnh tài xế.
- **Mình học được gì từ dòng đó:** Tag `frame_meta` là metadata toàn khung hình cực kỳ quan trọng cho pipeline huấn luyện đa phương thức (multimodal), giúp model phân biệt kênh ảnh RGB hay IR và điều kiện ánh sáng. Việc đối chiếu chéo (diff) với bạn giúp phát hiện ngay các lỗi thiếu sót mang tính quy trình mà mắt thường dễ bỏ qua.
