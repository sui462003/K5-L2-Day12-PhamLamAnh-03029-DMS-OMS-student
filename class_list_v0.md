# Danh sách lớp v0 — Phạm Lâm Anh · G01

Mỗi lớp trả lời câu hỏi nghiệp vụ: **Model cần nhận diện đối tượng / thuộc tính này để phục vụ chức năng cụ thể nào trong hệ thống DMS/OMS?**

---

## DMS (Driver Monitoring System)

| # | Lớp / thuộc tính | Giá trị cho phép | Để làm gì (Chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_state` (`eye_left`, `eye_right`) | `open` / `closed` / `unknown` | Đo tỷ lệ nhắm mắt PERCLOS và phát hiện cơn buồn ngủ (drowsiness), vi ngủ (microsleep) để phát cảnh báo âm thanh/rung vô lăng kịp thời. | Có rất rõ; đèn LED NIR 940 nm giúp thấy rõ khe mắt ban đêm mà không làm chói mắt tài xế, trừ khi bị đốm lóa phản xạ trên kính. |
| 2 | `gaze_zone` | `road`, `mirror_l`, `mirror_r`, `mirror_c`, `cluster`, `center`, `lap`, `other` | Phát hiện xao nhãng hướng nhìn (Visual Distraction); cảnh báo nếu tài xế rời mắt khỏi đường (`road`) quá 2–3 giây liên tục. | Có; nhận diện qua hướng đồng tử, hốc mắt kết hợp với góc quay của đầu. |
| 3 | `face13` (13 điểm mốc khuôn mặt) | 13 keypoints (mí mắt, khóe mắt, mũi, môi) | Ước lượng tư thế đầu 3D (Head Pose: yaw, pitch, roll) để xác định góc gật gù buồn ngủ và hỗ trợ định hướng vùng nhìn khi mắt bị che khuất. | Có; các mốc giải phẫu trên mặt phản xạ ánh sáng NIR tốt, ngay cả trong điều kiện cabin hoàn toàn không có ánh sáng khả kiến. |
| 4 | `hand_on_wheel` (`hand.on_wheel`) | `yes` / `no` / `unknown` | Giám sát tiếp quản xe (Hands-on detection) cho các cấp độ tự lái L2/L3; cảnh báo tài xế phải đặt tay lên vô lăng khi hệ thống chuẩn bị bàn giao quyền điều khiển. | Có; phân biệt được bàn tay đang nắm vành vô lăng hoặc buông thõng dựa trên hình khối và tương phản sáng tối. |
| 5 | `phone_use` (`phone.state`) | `held` / `mounted` / `lap` | Phát hiện hành vi sử dụng điện thoại khi đang điều khiển xe (nghe điện thoại áp tai, cầm máy nhắn tin), ngăn ngừa vi phạm luật giao thông và tai nạn do mất tập trung. | Có nếu thấy cạnh viền máy, góc máy hoặc ánh sáng phát ra từ màn hình điện thoại; nếu chỉ thấy tay áp tai thì gán theo quy tắc cẩn trọng. |
| 6 | `seatbelt_driver` (`person.seatbelt`) | `worn_correct` / `worn_incorrect` / `not_worn` / `unknown` | Cảnh báo thắt dây an toàn trước khi xe khởi hành; phân biệt thắt đúng quy cách với thắt đối phó (luồn dây sau lưng, kẹp dưới nách) để tối ưu kích nổ túi khí. | Có; dải dây phản quang có độ phản xạ NIR khác biệt với vải quần áo, trừ trường hợp áo quá sẫm màu và thiếu sáng. |
| 7 | `glasses_type` (`face.glasses`) | `none` / `clear` / `sun` / `unknown` | Hiệu chỉnh thuật toán phát hiện mắt; nếu tài xế đeo kính râm hoặc kính cận thì hệ thống chuyển sang thuật toán bù trừ đốm lóa hoặc tăng độ nhạy phân tích đầu. | Có; tia NIR có thể nhìn xuyên qua tròng kính râm tối màu để phát hiện mắt bên trong, nhưng gọng kính vẫn thể hiện rõ. |

---

## OMS (Occupant Monitoring System)

| # | Lớp / thuộc tính | Giá trị cho phép | Để làm gì (Chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `seat_occupancy` (`person.seat`) | `rear_left`, `rear_middle`, `rear_right`, `front_passenger`, `driver` | Xác định vị trí có người ngồi trong xe để bật/tắt nhắc thắt dây an toàn ghế sau, tự động điều chỉnh điều hòa đa vùng và chuẩn bị túi khí rèm hông tương ứng. | Có; nhận diện qua hình dạng đầu, thân người và chuyển động cơ thể trong khoang xe. |
| 2 | `infant_seat` | Có / không theo ghế; hướng xoay: `rear` / `front` | Tự động vô hiệu hóa túi khí hành khách phía trước (nếu đặt nôi ở ghế phụ) tránh va đập chấn thương cổ trẻ sơ sinh; kích hoạt hệ thống chống bỏ quên trẻ em (CPD - Child Presence Detection). | Có; nhận diện đặc thù qua quai xách vòng cung, hình dáng lòng máng và hướng xoay nôi. |
| 3 | `child_seat` | Có / không theo ghế; trạng thái: `occupied: no / unknown` | Cảnh báo trẻ em bị bỏ quên trong xe khóa kín dưới trời nắng nóng; tối ưu ngưỡng bung túi khí rèm phù hợp tầm vóc trẻ nhỏ. | Có; nhận diện qua cấu trúc ghế nâng (booster seat), đệm đỡ đầu hai bên và dây an toàn riêng của ghế. |
| 4 | `seatbelt_rear` (`person.seatbelt`) | `worn_correct` / `not_worn` / `unknown` | Cảnh báo hành khách hàng ghế sau chưa cài dây an toàn theo tiêu chuẩn an toàn hiện đại (Euro NCAP). | Nhìn thấy một phần; phụ thuộc vào độ tương phản giữa dải dây an toàn và trang phục của hành khách trên ảnh IR. |
| 5 | `leftover_object` (`object.type`) | `bag`, `box`, `cup`, `other` | Cảnh báo đồ đạc bỏ quên (ví dụ quên ví, balo, laptop) khi tài xế tắt máy mở cửa rời xe; cảnh báo vật thể nặng có nguy cơ văng đập khi phanh gấp. | Có; phân biệt được qua đường nét hình học, góc cạnh ba lô/hộp và bóng đổ dù mất thông tin màu sắc. |
| 6 | `passenger_posture` | Bình thường / Out-of-Position (OOP) | Phát hiện hành khách ngồi sai tư thế nguy hiểm (ngả lưng quá thấp khi xe đang chạy, gác chân lên táp-lô) để cảnh báo và điều chỉnh lực bung túi khí phù hợp. | Có; nhận diện được qua góc nghiêng thân người và vị trí chân tay so với ghế xe. |

---

## 2 Câu hỏi leo thang (Escalation Questions)

### Câu hỏi 1
- **Nội dung câu hỏi:** Trong trường hợp trên ghế an toàn trẻ em (`child_seat` hoặc `infant_seat`) có đặt một đồ vật (ví dụ ba lô, thú bông, túi đồ) chứ không phải trẻ em thật, và dataset không có trẻ em ngồi, thì hệ thống phân loại quy định gán thuộc tính `occupied` như thế nào và có bắt buộc vẽ đồng thời 2 box đè lên nhau (`child_seat` và `object`) không?
- **Khung hình ví dụ:** `S03_rgb.png` / `S03_ir.png` và `S08_rgb.png`.
- **Cách tạm gán và lý do:** Tạm gán vẽ 2 box riêng biệt cùng vị trí ghế (`child_seat` với `occupied = no` và `object` với `type = bag/other`) theo hướng dẫn mục 4.8. Lý do là để model OMS học được sự khác biệt giữa "ghế có trẻ em ngồi" (nguy hiểm cần báo động CPD) và "ghế chỉ dùng để chứa hành lý", tránh báo động giả khi khóa xe.

### Câu hỏi 2
- **Nội dung câu hỏi:** Với ảnh hồng ngoại cabin ban đêm hoặc khu vực góc khuất thiếu sáng, khi dải dây an toàn màu tối chìm hoàn toàn vào màu áo sẫm của người ngồi (không thể phân biệt ranh giới bằng mắt thường), guideline quy định dứt khoát chọn `unknown` hay cho phép suy luận từ việc nhìn thấy đầu chốt dây đã cắm vào ổ khóa cạnh hông ghế?
- **Khung hình ví dụ:** `D01.png` và `S02_ir.png`.
- **Cách tạm gán và lý do:** Tạm gán chọn `unknown` tuân thủ tuyệt đối quy tắc chung 4.4-1 ("Không thấy thì unknown, không suy đoán"). Lý do: Nếu người gán nhãn tự suy đoán từ ổ khóa, model thị giác máy tính sẽ bị ép học các đặc trưng ảo từ nhiễu pixel tối màu, dẫn đến phán đoán sai lệch trên thực tế xe chạy.
