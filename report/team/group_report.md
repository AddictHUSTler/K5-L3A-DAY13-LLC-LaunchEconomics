# Báo cáo nhóm

Báo cáo ngắn, tối đa 2 trang. Số liệu chi tiết nằm trong các file hồ sơ; ở đây chỉ dẫn lại con số chính.

## 1. Thông tin nhóm

- Tên nhóm: LLC
- Lớp: L3A
- Thành viên: xem `TEAM.md`

## 2. Mục tiêu và cách tiếp cận

Nhóm dựng hồ sơ launch v0 cho trợ lý hoàn phí của LogiX-VN và trả lời bốn câu hỏi: có đáng chạy không, nhân viên có dùng không, khi hỏng thì sao, pilot thiết kế thế nào để ra được quyết định. Nhóm có hai người nên gộp bốn vai: một người viết code và kiểm số (CP1, 2, 4), một người gắn nhãn kiêm giữ hồ sơ (CP3, 5). Mỗi file hồ sơ có một người chủ.

## 3. Giải pháp

- **A · Chi phí** (`src/lab13.py`, `bang_chi_phi.md`): ba phép thử A1 đạt; `mo_hinh` cộng token và tool trên mọi lần chạy, chia cho số việc thành công; tách theo loại yêu cầu; cộng chi phí cố định 40 triệu đ/tháng cho phạm vi noi_dia + hang_nang.
- **B · Độ nhạy** (`bang_chi_phi.md`): chín kịch bản gọi lại `mo_hinh`, một kịch bản đổi cặp, giới hạn chạy 1/2/3 lần tính chi phí cả hệ thống, kịch bản xem lại 100%.
- **C · Bảng lỗi** (`bang_loi.md`): hai người gắn nhãn 20 ca theo năm loại Google PAIR; bảng khắc phục 5 ca, mỗi loại một ca, mỗi dòng có cách phát hiện đo được và một vai trò.
- **D · Pilot** (`pilot_plan.yaml`): tính cỡ mẫu theo ba cách chia, chọn chia theo nhân viên 20 + 20, có ba luật dừng đủ bốn vế.
- **E · Chỉ số và hồ sơ** (`chi_so.md`, `ho_so_launch_v0.md`): ba chỉ số tính thử, hai chỉ số tự đề xuất, mười event có `trace_id`, ba dòng rủi ro kinh tế, hồ sơ bảy mục.

## 4. Kết quả

Các số tiền dưới đây đều là simulated (tính từ cột `_simulated`).

- Chi phí mỗi việc thành công: 4.472 đ, gấp 16,3 lần hoá đơn token + tool chia số yêu cầu (274,7 đ).
- Theo loại yêu cầu so với 12.000 đ: noi_dia 0,22×, hang_nang 0,69×, doi_tac 0,85×, quoc_te 1,88× (không đáng để trợ lý xử lý).
- Ba yếu tố nhạy nhất: số ca làm lại (+51,8% nếu gấp đôi), tỉ lệ xem lại (+40,7%), lương nhân viên (+23,1%). Giá token chỉ +5,6%.
- Chi phí cả hệ thống: 5.865 đ/yêu cầu = 0,49×. Giới hạn 2 lần chạy rẻ nhất cho công ty (6.901.220 đ). Xem lại 100%: 0,98× đến 1,03×, gần như không tiết kiệm.
- Chỉ số trong đợt chạy thử (không có nhóm đối chứng): chính 82,83%, dùng (bỏ qua gợi ý) 27,12%, an toàn (mở lại 7 ngày) 4,25%.
- Cỡ mẫu: 1.251 yêu cầu mỗi nhóm cho mức chênh 5 điểm; 20 nhân viên mỗi nhóm chỉ đạt tối đa 1.000, nên nhóm chọn mức chênh 6 điểm (859 mỗi nhóm, mỗi người ≥ 299 yêu cầu). Nếu tác động thật chỉ 5 điểm thì power còn 0,64.
- Đề xuất trong `ho_so_launch_v0.md`: **Go có điều kiện** cho pilot noi_dia + hang_nang, kèm năm điều kiện có người phụ trách và ngày kiểm tra.
- Đồng thuận nhãn lỗi giữa hai người gắn nhãn: 19 / 20 = 95% (lệch ca 13: người gắn nhãn 1 ghi Hệ thống, người gắn nhãn 2 ghi Giới hạn hệ thống; thống nhất Giới hạn hệ thống vì ngoài phạm vi là giới hạn).
- Kết quả duyệt chéo từ hội đồng: [điền sau buổi duyệt chéo].

## 5. Khó khăn và cách xử lý
- Chỉ số an toàn "mở lại 7 ngày" không bắt được lỗi ngầm (ca 5, 12, 17). Cách xử lý: thêm chỉ số kiểm mẫu hằng tuần (100 đơn, ngưỡng 1%).
- Ngưỡng dừng tuyệt đối 3% cho mở lại 7 ngày sẽ dừng pilot ngay tuần đầu vì tỉ lệ hiện tại là 4,25%. Cách xử lý: dùng chênh so với đối chứng +2 điểm kèm trần tuyệt đối 6%.
- Người gắn nhãn 1 gửi bộ nhãn muộn vì tạm dừng việc riêng; nhóm so nhãn sau đó. Hai bộ nhãn gần như trùng hoàn toàn, nên độ độc lập khó chứng minh (xem báo cáo cá nhân).
- [Điền thêm nếu có: lỗi kỹ thuật khi cài đặt hoặc chạy, kèm bằng chứng.]

## 6. Tổng hợp đóng góp

Chi tiết đóng góp của từng thành viên nằm trong `TEAM.md` và các báo cáo cá nhân `report/team/MSSV_HoTen.md`.

## 7. Hạn chế và hướng cải thiện

- Mọi số tiền liên quan đến xem lại và làm lại dựa trên cột phút simulated; cần thay bằng phút đo thật sau tuần 1 của pilot.
- Pilot chỉ đủ mẫu cho mức chênh 6 điểm, không phải 5 điểm; cần Giám đốc vận hành chấp nhận đánh đổi này.
- Các ngưỡng dừng cho chi phí (8.000 đ), làm lại (7%), mở lại, bỏ qua gợi ý (50%) là đề xuất của nhóm, cần chỉnh theo dữ liệu thật của pilot.
- Ba chỉ số E1 chưa nằm trong `src/lab13.py`; nên thêm một đoạn in chúng vào code.

## 8. Tài liệu tham khảo

- Erol và cộng sự, *Cost-of-Pass: An Economic Framework for Evaluating Language Models*, arxiv.org/abs/2504.13359
- Google PAIR, *People + AI Guidebook*, chương "Errors + Graceful Failure"
- Tài liệu statsmodels, lớp `NormalIndPower`
- `docs/Lab13_Huong_dan_chi_tiet_buoi_chieu.md` và slide `Day 13 Instructor Deck` của buổi học
