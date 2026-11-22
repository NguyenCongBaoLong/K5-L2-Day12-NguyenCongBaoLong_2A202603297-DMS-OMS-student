# Báo cáo kiểm tra bài Lab Ngày 12 — DMS & OMS

**Ngày lập:** 22/11/2026  
**Người làm:** Nguyen Cong Bao Long — 2A202603297  
**Hình thức:** Cá nhân  
**Người chấm chéo:** Nguyen Tien Dat — 2A202603289  
**Mã bộ ảnh Gxx:** G03

## Kết luận

**Các bằng chứng E1–E5 đã có trong thư mục.** Bạn xác nhận rằng cả 35 điểm khác biệt đều được phân xử là `mine` đúng; không cần sửa nhãn. Export chính và hai lượt kiểm tra theo phạm vi A/B đều có 0 lỗi, 0 cảnh báo. E4 có 4 quan sát; E5 có 8 mục DMS, 6 mục OMS và 2 câu hỏi leo thang, đã được bạn rà soát theo slide 54. Self-review và exit ticket cũng đã được tạo. Còn kiểm tra hồ sơ và đóng gói nộp.

## Kết quả đã xác minh

| Hạng mục | Kết quả |
|---|---|
| `export_final.zip` (E1) | Có `annotations.xml`, không thấy ảnh `.png`/`.jpg` trong ZIP. Checker đọc đủ 22 ảnh, đủ 22 `frame_meta`; có `person=10`, `face=6`, `face13=5`, `hand=12`, `phone=1`, `child_seat=6`, `infant_seat=2`, `object=12`. |
| Kiểm tra cuối (E2) | Đã chạy lại `python scripts/cabin_check.py check export_final.zip --expect 22 --out check_final.txt`: **0 lỗi, 0 cảnh báo**. Xem [check_final.txt](./check_final.txt). |
| Kiểm tra phạm vi A/B (E2) | Đã tạo [check_cpA.txt](./check_cpA.txt) cho S01–S02 (4 ảnh) và [check_cpB.txt](./check_cpB.txt) cho D01–D02 (2 ảnh), đều 0 lỗi/0 cảnh báo. Cả hai được chạy trên `export_final.zip`, không phải bản export lưu tại thời điểm checkpoint. |
| So sánh chéo (E3) | So sánh `export_final.zip` với `l12.zip`: 22 ảnh chung, **35 điểm khác biệt**. Đã điền `mine`, guideline và hành động cho cả 35 dòng trong [disagreement_log.csv](./disagreement_log.csv), theo xác nhận review của bạn. |
| Chỉnh sửa sau review | Review kết luận không cần sửa nhãn. Giữ `export_final.zip`; không cần `export_final_v2.zip` hoặc `check_final_v2.txt`. |

Lần kiểm ban đầu bạn cung cấp có một lỗi hai tay `driver` cùng `side=left` ở D03 và ba cảnh báo ở D01/D03. Lần kiểm sau đó và lần chạy lại hiện tại đều báo 0 lỗi/0 cảnh báo, nên lỗi/cảnh báo máy kiểm tra đã được xử lý. Điều này không thay thế việc xem lại các khác biệt trong diff.

## Tóm tắt kết quả review chéo

Theo xác nhận của bạn, kết luận cho toàn bộ 35 điểm là `mine`; không thay đổi export. Bảng dưới tóm tắt các điểm đã review; từng verdict, điều khoản guideline và hành động được ghi trong CSV.

| Ảnh | Số điểm | Đối tượng khác biệt | Quy tắc đã ghi | Kết quả |
|---|---:|---|---|---|
| D01.png | 10 | Hai trạng thái mắt; cờ `occluded` của 8 điểm quanh mắt | GUIDE §4.5, §4.6 | mine; export unchanged. |
| D02.png | 1 | Box `face` chỉ có ở mine hoặc IoU thấp | GUIDE §4.1, §4.5 | mine; export unchanged. |
| D03.png | 1 | `hand.on_wheel` (`unknown` / `yes`) | GUIDE §4.7 | mine; export unchanged. |
| D05.png | 1 | `face.gaze_zone` (`road` / `lap`) | GUIDE §4.5 | mine; export unchanged. |
| D06.png | 2 | `person.seatbelt`; `face.glasses` | GUIDE §4.5, §4.7 | mine; export unchanged. |
| S01_ir.png | 2 | `object.type`; box `child_seat` chỉ có ở peer | GUIDE §4.4-4, §4.8 | mine; export unchanged. |
| S01_rgb.png | 2 | Box `infant_seat` và `object` chỉ có ở mine | GUIDE §4.2, §4.8 | mine; export unchanged. |
| S02_ir.png | 1 | Box `face` chỉ có ở peer | GUIDE §4.2, §4.5 | mine; export unchanged. |
| S03_ir.png | 2 | `object.type`; box `child_seat` chỉ có ở peer | GUIDE §4.4-4, §4.8 | mine; export unchanged. |
| S03_rgb.png | 2 | Box `object` chỉ có ở mine; box `child_seat` chỉ có ở peer | GUIDE §4.2, §4.8 | mine; export unchanged. |
| S04_ir.png | 1 | Box `child_seat` chỉ có ở peer | GUIDE §4.8 | mine; export unchanged. |
| S04_rgb.png | 1 | Box `object` chỉ có ở mine | GUIDE §4.2, §4.8 | mine; export unchanged. |
| S05_ir.png | 2 | `object.type`; box `child_seat` chỉ có ở peer | GUIDE §4.4-4, §4.8 | mine; export unchanged. |
| S05_rgb.png | 2 | `object.type`; box `child_seat` chỉ có ở peer | GUIDE §4.8 | mine; export unchanged. |
| S06_ir.png | 1 | Box `child_seat` chỉ có ở peer | GUIDE §4.8 | mine; export unchanged. |
| S07_ir.png | 1 | Box `child_seat` chỉ có ở peer | GUIDE §4.8 | mine; export unchanged. |
| S07_rgb.png | 1 | Box `child_seat` chỉ có ở peer | GUIDE §4.8 | mine; export unchanged. |
| S08_ir.png | 1 | Box `face` chỉ có ở peer | GUIDE §4.2, §4.5 | mine; export unchanged. |
| S08_rgb.png | 1 | Box `face` chỉ có ở peer | GUIDE §4.2, §4.5 | mine; export unchanged. |
| **Tổng** | **35** |  |  |  |

CSV đã ghi `verdict=mine` cho cả 35 dòng, kèm quy tắc và hành động “giữ nhãn mine; không sửa export”, theo xác nhận review của bạn.

## Việc còn phải làm trước khi nộp

1. Review chéo E3 đã hoàn tất: 35/35 dòng có verdict, guideline và action trong `disagreement_log.csv`.
2. Không cần tạo `export_final_v2.zip` hoặc `check_final_v2.txt` vì review kết luận không sửa nhãn.
3. Hai file CP A/B hiện là kiểm tra lại các phạm vi S01–S02 và D01–D02 từ export cuối. Nếu coach yêu cầu bằng chứng lịch sử tại checkpoint, cần dùng log/export checkpoint gốc; không thể khôi phục từ `export_final.zip`.
4. E4 đã có trong [ir_log.csv](./ir_log.csv): 4 quan sát, gồm 2 `IR_sim` và 2 `real_IR`.
5. [class_list_v0.md](./class_list_v0.md) đã được bạn rà soát theo slide 54; có 8 mục DMS, 6 mục OMS và 2 câu hỏi leo thang.
6. [self_review.md](./self_review.md) và [exit_ticket.md](./exit_ticket.md) đã được tạo.
7. `TEAM.md` đã ghi mã G03; `prompts.md` cũng đã có. Kiểm tra cấu trúc cuối rồi đóng gói theo `SUBMISSION.md`.
8. Chỉ đưa các minh chứng/annotation vào gói nộp, không kèm ảnh hoặc `manifest.csv`; đặt tên gói nộp đúng mẫu trong `SUBMISSION.md`.

## Hồ sơ hiện có trong repo

- Đã có: `export_final.zip`, `l12.zip`, `check_final.txt`, `check_cpA.txt`, `check_cpB.txt`, `disagreement_log.csv`, `ir_log.csv`, `self_review.md`, `exit_ticket.md`, `class_list_v0.md`, `TEAM.md`, `prompts.md`.
- Còn cần hoàn tất: kiểm tra gói đủ file/đúng tên, lưu ý CP A/B hiện là kiểm tra lại trên `export_final.zip` chứ không phải snapshot thời điểm checkpoint, rồi tạo ZIP nộp LMS.
