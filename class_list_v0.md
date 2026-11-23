# Danh sách lớp v0 — Trần Trọng Hoàng Vũ · G01

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_left` / `eye_right` | open / closed / unknown | Phát hiện tài xế ngủ gật (mắt nhắm quá thời gian ngưỡng quy định) | Có, trừ khi bị lóa đèn hồng ngoại trên tròng kính |
| 2 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (rời mắt khỏi cung đường phía trước) | Có, dựa trên hướng mắt hoặc góc xoay đầu |
| 3 | `glasses` | none / clear / sun / unknown | Điều chỉnh thuật toán nhận diện mắt (tránh lỗi nhận diện do gọng/tròng kính) | Có, nhưng kính râm có thể bị xuyên thấu trên NIR |
| 4 | `hand_on_wheel` | yes / no / unknown | Cảnh báo buông tay khỏi vô lăng (hands-off detection cho xe tự lái L2+) | Có, thông qua độ tương phản bàn tay và vành vô lăng |
| 5 | `phone_state` | held / mounted / lap | Phát hiện hành vi sử dụng điện thoại khi đang điều khiển xe | Có, thấy được đường viền và phản xạ màn hình |
| 6 | `face13` | 13 tọa độ landmark mặt | Ước lượng góc xoay đầu (Head Pose Yaw/Pitch/Roll) và độ mở mắt (EAR) | Có, camera NIR cho landmark khuôn mặt ổn định ban đêm |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `seat_occupancy` | person / empty / child_seat / object | Quản lý logic bung túi khí và nhắc nhở thắt dây an toàn cho từng vị trí | Có, nhận diện rõ người hoặc ghế trống qua hình khối |
| 2 | `child_seat` | occupied: no / unknown | Phát hiện có ghế trẻ em để nhắc nhở an toàn, chống bỏ quên trẻ (CPD) | Có, nhận dạng rõ kiểu dáng ghế trẻ em |
| 3 | `infant_seat` | facing: rear / front | Tự động vô hiệu hóa túi khí nếu nôi trẻ em quay mặt về sau (rear-facing) | Có, phân biệt được hướng quay của nôi trẻ em |
| 4 | `seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo hành khách chưa thắt dây an toàn hoặc thắt sai quy cách | Nhìn được nếu áo tương phản sáng; áo tối màu dễ bị lẫn |
| 5 | `object` | bag / box / cup / other | Cảnh báo đồ vật để quên trong xe sau khi tắt máy và khóa cửa | Có, phân biệt qua hình học biên dạng |
| 6 | `camera_blocked` | yes / no | Giám sát tình trạng phần cứng, cảnh báo hệ thống camera cabin bị che khuất | Có, nhận diện qua độ tối đồng nhất hoặc mờ toàn khung hình |

## 2 câu hỏi leo thang

1. **Câu hỏi:** Khi tài xế đeo kính râm mà camera NIR nhìn xuyên qua thấy rõ mắt đang mở, thuộc tính `glasses` nên ưu tiên là `sun` hay `clear`?
   - **Khung ví dụ:** `D02.png`
   - **Bạn tạm gán thế nào và vì sao:** Tạm gán `sun` vì bản chất vật lý người lái đang đeo kính râm chống chói ban ngày, dù tia hồng ngoại cận (NIR) có thể đi xuyên qua tròng kính.

2. **Câu hỏi:** Đồ vật kích thước nhỏ nằm bên trong nôi em bé hoặc ghế trẻ em (như bình sữa, đồ chơi nhỏ) thì có phải gán box `object` tách rời không, hay chỉ gán vật chiếm trọn ghế?
   - **Khung ví dụ:** `S03_rgb.png` (balo/túi đặt trên ghế trẻ em)
   - **Bạn tạm gán thế nào và vì sao:** Tạm gán 2 box riêng biệt (`child_seat` và `object`) vì guideline mục 4.8 quy định vật nằm trong ghế trẻ em vẽ 2 box riêng, cùng vị trí ghế.
