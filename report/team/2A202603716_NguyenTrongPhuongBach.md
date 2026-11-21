# Báo cáo cá nhân — Nguyễn Trọng Phương Bách · 2A202603716

## 1. Thông tin thành viên

- Họ tên: Nguyễn Trọng Phương Bách
- MSSV: 2A202603716
- Email: bachn2880@gmail.com
- Vai trong nhóm: người viết code, người kiểm số, người gắn nhãn 1

## 2. Phần việc phụ trách

- CP1: viết `src/lab13.py` (mô hình chi phí), điền A1, A2, A3, A4 trong `bang_chi_phi.md`.
- CP2: bảng độ nhạy B1–B4 trong `bang_chi_phi.md`.
- CP4: tính cỡ mẫu D1 và viết `pilot_plan.yaml` (năm câu D2, ba luật dừng, rollout, rollback).
- CP3 (gắn nhãn 20 ca) và CP5 (chỉ số, hồ sơ launch) do Trần Thái Hưng làm phần viết; xem báo cáo của bạn ấy.

## 3. Đóng góp cụ thể

- `lab13.py`: cộng token và tool trên mọi lần chạy, chia cho số việc thành công; ba phép thử A1 ĐẠT (1,20 · 1,25 · 1,25).
- A2/A3: chi phí mỗi việc thành công 4.472 đ [simulated], gấp 16,3 lần hoá đơn chia số yêu cầu (274,7 đ). `quoc_te` là 1,88× so với 12.000 đ nên không đáng để trợ lý xử lý; chạy lại không giúp vì tỉ lệ ok theo lần chạy giảm 30% → 11,4% → 2,2%.
- A4: thêm chi phí cố định 40 triệu đ/tháng cho phạm vi noi_dia + hang_nang: 0,38× ở 45.000 yêu cầu, 0,48× ở nửa khối lượng, kết luận không đổi.
- B1–B2: chín kịch bản đổi từng yếu tố, một kịch bản đổi cặp. Xếp hạng: số ca làm lại (+51,8%) > tỉ lệ xem lại (+40,7%) > lương (+23,1%); giá token chỉ +5,6%.
- B3: giới hạn 2 lần rẻ nhất cho cả hệ thống (6.901.220 đ) dù 1 lần có chi phí mỗi việc thành công thấp nhất (4.111 đ).
- B4: xem lại 100% = 0,98× đến 1,03×, gần như không tiết kiệm.
- D1: 1.251 yêu cầu mỗi nhóm cho mức chênh 5 điểm; chia theo nhân viên cần 84 người > 40; 20 người mỗi nhóm tối đa 1.000 < 1.251. Chọn chia theo nhân viên 20 + 20 với mức chênh 6 điểm (859 mỗi nhóm, mỗi người ≥ 299 yêu cầu).
- Luật dừng đặt ngưỡng mở lại là chênh +2 điểm so với đối chứng kèm trần 6%, vì mức hiện tại 4,25% đã vượt ngưỡng tuyệt đối 3%.
- Gắn nhãn 20 ca lỗi ở CP3 với tư cách người gắn nhãn 1; đồng thuận 19/20 với Hưng.

## 4. Bằng chứng

- Commit `c567509` (CP1, CP2), `b60a051` (CP4), `e4f4eb8` (cập nhật hồ sơ theo CP4) trên nhánh `main`.
- File: `src/lab13.py`, `report/team/bang_chi_phi.md`, `report/team/pilot_plan.yaml`.
- Chạy lại `cd src && python lab13.py`: ba phép thử A1 in ĐẠT.

## 5. Công cụ AI đã dùng

Claude Code (VS Code): hỗ trợ viết `lab13.py`, soạn bảng markdown và `pilot_plan.yaml`, chạy lại code. Tôi tự kiểm tra bằng ba phép thử A1, so các số A2, A3, B1–B4, D1 với đáp án trên slide (lệch không quá 2%), tính tay chi phí cả hệ thống, và đọc lại file bằng `yaml.safe_load`.

Các ngưỡng dừng cho chi phí (8.000 đ), làm lại (7%), bỏ qua gợi ý (50%) là đề xuất, không có trong dữ liệu.

## 6. Tự đánh giá

- Làm tốt: số có nhãn `simulated`; nêu rõ con số bất lợi (xem lại 100% gần 1×, power còn 0,64 nếu tác động thật chỉ 5 điểm).
- Chưa tốt: ba chỉ số E1 chưa nằm trong `lab13.py`; nhãn lỗi của tôi gửi muộn nên độ độc lập với nhãn của Hưng khó chứng minh; ngưỡng dừng cần chỉnh theo dữ liệu pilot.
- Hiểu rõ nhất: vì sao chi phí mỗi việc thành công lớn hơn nhiều hoá đơn token chia số yêu cầu (tử số tính mọi lần chạy, mẫu số chỉ đếm việc thành công), và vì sao 20 nhân viên mỗi nhóm không đủ cho mức chênh 5 điểm.
