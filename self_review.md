# Tự đánh giá — Nguyen Cong Bao Long · G03

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01 | Ghế / người ngồi | ok | Gán tên ghế theo hướng xe (rear_right là ghế bên trái khung hình); không dùng `occupied = yes` và không gán dây an toàn trên SVIRO IR-sim. | Có |
| S05 | Vật thể / người | ok | Không suy đoán nhãn mơ hồ khi thiếu bằng chứng thị giác; chỉ giữ nhãn theo guideline. | Có |
| D01 | Face / hand | box, lr_flip | Thu gọn box face sát mặt, không lấy dư phần tóc/sau đầu; kiểm tra trái/phải theo người lái thay vì theo khung hình. | Có |
| D03 | Hand / face13 | lr_flip, flag | Sửa lỗi hai tay driver trùng `side=left`; rà cờ `occluded`/`outside` trên face13 khi điểm bị tối hoặc che. | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm trái/phải theo khung hình thay vì theo người (`lr_flip`).

Vì sao mình mắc: Ảnh DMS bị xoay, nên dễ lấy trái/phải theo vị trí trên ảnh thay vì theo cơ thể tài xế.

Lần sau tránh bằng cách: Trước khi lưu, đối chiếu trái/phải theo người theo GUIDE §4.4-2; với ảnh D##, kiểm tra trục mắt và rà để mỗi người không có hai tay cùng `side`.

## 3. Ghi chú về disagreement_log

Theo kết quả review, cả 35 dòng đều được chốt `mine`; không có dòng nào chốt `peer` đúng và nhãn của mình sai. Bài học từ review: khác biệt giữa hai bộ nhãn cần được đối chiếu theo guideline từng trường, không nên xem số dòng đồng thuận là bằng chứng tự thân rằng nhãn đúng.
