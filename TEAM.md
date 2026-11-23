# TEAM — Ngày 12

Mã bộ ảnh: **G01** · Hình thức: cá nhân

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Trần Trọng Hoàng Vũ | 2A202603261 | có | Bạn cùng mã G01 (peer_export_final.zip) | 74 |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- `D02.png`: Thuộc tính `glasses` của người lái khi ảnh hồng ngoại nhìn xuyên qua kính râm tối màu (sun vs clear).
- `D03.png`: Điểm landmark vùng mắt khi bị đốm lóa phản xạ LED che khuất hoàn toàn (nên dùng cờ `occluded` hay `outside`).

## Cá nhân

### TranTrongHoangVu-2A202603261
- Phần mình làm: Tự thực hiện toàn bộ 22 khung hình (S01–S08 RGB/IR và D01–D06 NIR), tự chạy script `cabin_check`, thực hiện diff với file peer và phân tích các điểm bất đồng theo Guideline v1.0.
- Điều mình học được hôm nay: Hiểu rõ sự khác biệt giữa ảnh hồng ngoại thực tế (NIR) và ảnh hồng ngoại mô phỏng (IR-sim); nắm vững quy tắc ánh xạ tọa độ không gian cabin theo hệ quy chiếu xe và giải phẫu con người thay vì góc nhìn người xem ảnh.
