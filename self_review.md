# Tự đánh giá — Trần Trọng Hoàng Vũ · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png | frame_meta | guess | Để light=night theo cảm quan thay vì unknown cho ảnh dựng | Đã sửa |
| S08_rgb.png | child_seat | seat_flip | Lúc đầu chọn seat=driver nhầm sang ghế trước | Đã sửa thành rear seat |
| D02.png | object | extra | Vẽ box chai nước/vật cầm tay trong DMS (DMS không gán object) | Đã sửa |
| D04.png | face | flag | Mắt bị che nhưng chưa kịp gán cờ occluded cho landmark | Đã sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

**Lỗi:** Nhầm lẫn quy ước tọa độ trái/phải theo góc nhìn của ảnh thay vì theo quy ước xe (OMS) và theo người lái (DMS).

**Vì sao mình mắc:** Phản xạ tự nhiên khi nhìn ảnh là quy chiếu theo mắt người xem (bên trái ảnh thì nghĩ là left), trong khi camera OMS nhìn ngược từ trước ra sau (trái ảnh là bên phải xe), và camera DMS bị xoay nghiêng 90 độ.

**Lần sau tránh bằng cách:** Luôn tự nhẩm quy tắc trước khi đặt box: đặt mình vào vị trí ghế lái xe nhìn về phía trước để xác định ghế `rear_right` / `rear_left`, và nghiêng đầu theo góc ảnh D## để xác định mắt trái / mắt phải (mắt trái có tọa độ y lớn hơn).

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai:
- **Dòng:** `D02.png`, nhãn `object`.
- **Học được:** Tôi đã vẽ box cho vật cầm trên tay của tài xế. Bạn peer không vẽ vì theo mục 4.2 của Guideline, hệ thống DMS chỉ tập trung vào người, mặt, mắt, tay, và điện thoại; các vật thể khác (cốc, chai, vật dụng) không được gán `object` để tránh gây nhiễu cho mô hình phát hiện phân tâm.
