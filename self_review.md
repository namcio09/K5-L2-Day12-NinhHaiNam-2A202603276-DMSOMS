# Tự đánh giá — Ninh Hải Nam · G04

## 1. Tự rà soát 4 cảnh

Đối chiếu hai ảnh S và hai ảnh D với box đã gán và kết quả review chéo.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S03_rgb | child_seat, infant_seat, object | ok | Box ôm phần nhìn thấy của ghế trẻ em, nôi em bé và cốc; ghế bên trái ảnh được gọi là rear_right theo xe. | không cần |
| S08_rgb | person, face, child_seat | ok | Người lớn bị cắt một phần ở mép trái nên box person chạm mép ảnh; box face và ghế trẻ em bao đúng phần nhìn thấy. | không cần |
| D02 | face13 · lip_lower | flag | Review chọn tắt `occluded`; đã cập nhật thành 0 trong bản v2. | có |
| D03 | face · gaze_zone | guess | Ban đầu chọn `road`; review thống nhất `center` theo hướng nhìn trong ảnh và đã cập nhật. | có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Mình có xu hướng chọn `road` cho `gaze_zone` trong các khung D03–D05 dù hướng nhìn có thể lệch về vùng giữa xe.

Vì sao mình mắc: Mình dựa nhiều vào hướng đầu và chưa so kỹ với hướng mắt cùng vị trí màn hình/bảng điều khiển.

Lần sau tránh bằng cách: Xét cả hướng mắt và đầu; chỉ chọn `road` khi hướng nhìn qua kính chắn gió rõ, chọn `center` khi nhìn màn hình/bảng giữa, còn không chắc thì dùng `other`.

## 3. Ghi chú về disagreement_log

Từ các dòng đã review, mình rút ra cần phân biệt `road` và `center` bằng cả hướng mắt lẫn đầu, đồng thời kiểm riêng cờ `occluded` và `outside` cho từng điểm mặt.
