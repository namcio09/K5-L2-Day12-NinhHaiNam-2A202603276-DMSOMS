# Danh sách lớp v0 — NinhHaiNam · G04

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver | Xác định người lái để gắn các dự đoán DMS đúng người. | Thường có thể thấy dáng người; chi tiết giảm khi tối hoặc bị che. |
| 2 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Phát hiện việc thắt dây an toàn đúng cách. | Có thể khó thấy khi dây chìm trong bóng tối hoặc bị áo che. |
| 3 | eye state | open / closed / unknown | Phát hiện dấu hiệu nhắm mắt kéo dài để cảnh báo buồn ngủ. | Có thể thấy, nhưng phản xạ NIR hoặc kính tối làm mắt khó phân biệt. |
| 4 | glasses | none / clear / sun / unknown | Nhận biết kính làm ảnh hưởng đến khả năng quan sát mắt. | Không phải lúc nào cũng phân biệt được kính râm với kính trong trên NIR. |
| 5 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Nhận biết tài xế có nhìn đường hay nhìn sang vùng khác trong xe. | Hướng đầu thường còn thấy; hướng mắt có thể bị phản xạ hoặc che khuất. |
| 6 | face13 | 13 điểm mặt | Theo dõi vị trí mắt, mũi, miệng để hỗ trợ ước lượng trạng thái mặt. | Độ tin cậy giảm khi điểm bị che, mặt nhỏ hoặc ảnh tối. |
| 7 | hand / on_wheel | whose, side, yes / no / unknown | Nhận biết tay tài xế và việc tay có chạm vô lăng không. | Có thể thấy tay; bóng tối hoặc vật cầm trên tay làm giảm chi tiết. |
| 8 | phone / state | held / mounted / lap | Phát hiện điện thoại được cầm, đặt trên giá hay để trên đùi. | Hình dạng máy có thể thấy; không nên suy ra chỉ từ tay gần tai. |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver, front_passenger, rear_left, rear_middle, rear_right | Xác định người ngồi ở ghế nào để biết tình trạng chiếm chỗ. | Thường thấy dáng người; cần gán ghế theo xe, không theo phía ảnh. |
| 2 | face | có box / không thấy mặt | Ghi nhận mặt người lớn trong cabin; hỗ trợ các chức năng DMS khi có camera phù hợp. | Có thể thấy hình dáng mặt, nhưng chi tiết giảm khi bị che hoặc tối. |
| 3 | child_seat / occupied | yes / no / unknown | Nhận biết ghế trẻ em và liệu có trẻ ngồi trong đó. | Hình dạng ghế thường có thể thấy; bên trong có thể bị che. |
| 4 | infant_seat / facing | rear / front | Nhận biết nôi xách và hướng đặt nôi để hỗ trợ kiểm tra an toàn ghế. | Hình dạng thường thấy; hướng quay cần nhận ra cấu trúc nôi. |
| 5 | object / type | bag / box / cup / other | Nhận biết đồ vật để cảnh báo đồ rời hoặc hỗ trợ hiểu tình trạng cabin. | Có thể phân biệt hình dạng; màu sắc không đáng tin trên IR. |
| 6 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Theo dõi tình trạng dây an toàn của người ngồi trong cabin. | Có thể khó thấy nếu dây chìm trong bóng tối hoặc bị che. |

## 2 câu hỏi leo thang

1. Khi một điểm mặt bị vật che nhưng vị trí ước lượng được, ranh giới nào phân biệt `occluded` với `outside` nếu điểm nằm sát mép ảnh?
   Khung ví dụ: `D01`, điểm `mouth_right` có bất đồng về hai cờ.
   Tạm gán: nếu điểm còn nằm trong ảnh và ước lượng được vị trí thì `occluded`; chỉ dùng `outside` khi điểm ở ngoài khung.
2. Khi hướng mắt và hướng đầu gợi ý hai vùng khác nhau, quy tắc nào ưu tiên để chọn `gaze_zone`?
   Khung ví dụ: `D04`, bất đồng `road` / `center`.
   Tạm gán: xem cả mắt và đầu; nếu vẫn không xác định chắc vùng nào thì chọn `other` và ghi chú.
