# Khai báo dùng AI — Phạm Lâm Anh

Nhắc lại quy định: Không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho bất kỳ công cụ AI nào.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Antigravity AI Assistant | Đọc README, tài liệu hướng dẫn và tóm tắt quy trình các bước làm lab, lịch trình checkpoint và yêu cầu sản phẩm nộp. | Nắm vững lộ trình làm bài từ Task 0 đến Task 4, cách tổ chức thư mục và quy cách nộp bài. | Có, kiểm tra đối chiếu trực tiếp với các file `GUIDE.md`, `CHECKPOINTS.md` và `SUBMISSION.md`. |
| 2 | Antigravity AI Assistant | Hỏi về quy tắc gán ghế: Ghế giữa trống có cần vẽ box không, cách phân biệt `infant_seat` và `child_seat`, quy ước trái/phải của ghế sau theo xe. | Hiểu rõ ghế trống không vẽ box; chỉ vẽ ôm sát ghế trẻ em chứ không vẽ trùm lên ghế ô tô; bên trái ảnh là ghế sau bên phải (`rear_right`). | Có, kiểm tra lại mục 4.2 và 4.8 của `GUIDE.md`. |
| 3 | Antigravity AI Assistant | Hỏi quy tắc gán nhãn DMS cho ảnh D01–D06 bị xoay 90° (cách định vị mắt trái/phải theo trục y, 13 điểm skeleton `face13`, thuộc tính kính râm dưới tia NIR). | Định hướng đúng mắt trái của tài xế nằm ở vị trí toạ độ y lớn hơn (nằm thấp hơn); đặt đúng vị trí 13 điểm mốc khuôn mặt và cờ occluded. | Có, chạy lệnh kiểm tra Checkpoint B và đọc giải thích cảnh báo trong `COMMON_ERRORS.md`. |
| 4 | Antigravity AI Assistant | Hỗ trợ phân tích nguyên nhân các lỗi khi chạy script `cabin_check.py` trên file export lần 1; hỗ trợ phân tích các bất đồng trong `disagreement_log.csv`; gợi ý hoàn thiện danh sách lớp `class_list_v0.md` và giải thích câu hỏi `exit_ticket.md`. | Sửa triệt để các lỗi (bổ sung frame_meta, đổi occupied thành no, sửa seat=driver thành ghế sau); hoàn thiện hồ sơ nộp bài đạt chuẩn 0 lỗi. | Có, chạy lại lệnh `python3 scripts/cabin_check.py check export_final_v2.zip --expect 22` xác nhận đạt 0 lỗi, 0 cảnh báo. |
