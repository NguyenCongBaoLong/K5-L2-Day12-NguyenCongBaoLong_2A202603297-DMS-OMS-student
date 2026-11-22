# Danh sách lớp v0 — Nguyen Cong Bao Long · G03

Đã được người làm rà soát theo slide 54. Danh sách có 8 mục DMS, 6 mục OMS và 2 câu hỏi leo thang kèm khung ví dụ.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver | Xác định tài xế để gắn các tín hiệu hành vi vào đúng người | Thường thấy hình dáng người; vị trí ghế suy từ bố cục |
| 2 | eye_state | open / closed / unknown | Theo dõi mắt nhắm để hỗ trợ phát hiện buồn ngủ; một khung hình không tự kết luận trạng thái kéo dài | Có thể thấy; phản xạ/kính tối có thể làm không rõ |
| 3 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện hướng nhìn rời đường hoặc nhìn vùng khác trong cabin | Có thể ước lượng hướng đầu/mắt; có thể không rõ |
| 4 | glasses | unknown / none / clear / sun | Ghi nhận kính che vùng mắt để diễn giải độ tin cậy của tín hiệu mắt | Hình kính có thể thấy; loại tròng có thể không phân biệt được |
| 5 | face13 | 13 điểm; occluded / outside | Mô tả hình học mặt và hỗ trợ ước lượng tư thế mặt; cờ cho biết điểm không quan sát được | Một phần có thể thấy; điểm bị che phải gắn cờ, không đoán |
| 6 | hand / on_wheel | whose / side / yes / no / unknown | Ghi nhận tay tài xế và việc tay có chạm vô lăng hay không | Thường thấy hình bàn tay; chi tiết có thể mất trong vùng tối |
| 7 | phone / state | held / mounted / lap | Nhận biết hành vi dùng điện thoại trong cabin | Thường nhận ra qua hình dạng/vị trí; màu sắc không đáng tin trên IR |
| 8 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Hỗ trợ nhận biết tình trạng thắt dây an toàn của tài xế | Có thể khó thấy vì tối/che khuất; khi không rõ dùng unknown |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định người và vị trí ngồi để biết ghế nào đang có người | Thường thấy hình dáng; ghế phải gọi theo xe, không theo phía ảnh |
| 2 | child_seat / occupied | no / unknown | Nhận biết ghế trẻ em và tình trạng quan sát được bên trong ghế | Thường thấy hình dáng; phần bên trong có thể bị che |
| 3 | infant_seat / facing | rear / front | Nhận biết nôi xách trẻ em và hướng quay để hỗ trợ diễn giải cấu hình ghế | Thường thấy hình dáng/hướng; không dựa vào màu |
| 4 | object / type | bag / box / cup / other | Nhận biết đồ vật trong cabin để mô tả vật mang theo và vị trí của nó | Hình dáng thường còn; màu sắc không đáng tin, vật mơ hồ dùng other |
| 5 | seat (thuộc tính vị trí) | rear_left / rear_middle / rear_right / ... | Gắn người hoặc vật với đúng vị trí trong xe để truy vấn theo ghế | Có thể suy từ bố cục cabin; trái/phải theo xe |
| 6 | frame_meta | modality / light / camera_blocked | Ghi bối cảnh ảnh và tình trạng camera để lọc, phân tích chất lượng dữ liệu | Modality lấy từ nguồn ảnh; mức sáng và che camera cần quan sát khung hình |

## 2 câu hỏi leo thang

1. Câu hỏi: Với `hand.on_wheel`, guideline nói `yes` khi tay chạm vô lăng nhưng chưa định nghĩa mức bằng chứng khi tay chồng lên/ở sát vành vô lăng. Trường hợp nào bắt buộc chọn `unknown` thay vì `yes`?
   Khung ví dụ: D03.png
   Bạn tạm gán thế nào và vì sao: Giữ nhãn mine đã được review; chỉ chọn `yes` khi thấy điểm tiếp xúc, nếu không chứng minh được tiếp xúc thì dùng `unknown`.

2. Câu hỏi: Khi hình dáng đồ vật trên IR-sim chỉ cho thấy một phần và chưa đủ phân biệt hai loại, có ngưỡng quan sát nào để chọn một loại cụ thể thay vì `other` không?
   Khung ví dụ: S05_ir.png
   Bạn tạm gán thế nào và vì sao: Giữ nhãn mine đã được review; phân loại theo hình dáng, không suy từ màu hoặc ảnh RGB cùng cảnh, và dùng `other` nếu hình dáng không đủ chắc.
