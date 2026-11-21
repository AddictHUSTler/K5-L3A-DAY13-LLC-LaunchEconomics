# Báo cáo cá nhân — Trần Thái Hưng · 2A202603557

## 1. Thông tin thành viên

- Họ tên: Trần Thái Hưng
- MSSV: 2A202603557
- Email: [điền email]
- Vai trong nhóm: người gắn nhãn 2, kiêm giữ hồ sơ launch v0

## 2. Phần việc phụ trách

- CP3: gắn nhãn 20 ca lỗi theo năm loại Google PAIR; bảng khắc phục 5 ca, mỗi loại một ca (`report/team/bang_loi.md`).
- CP5: `report/team/chi_so.md` và `report/team/ho_so_launch_v0.md`; phần `group_report.md` và `TEAM.md` của nhóm.
- Việc của người kia (viết code `src/lab13.py`, CP1, CP2, CP4, `bang_chi_phi.md`, `pilot_plan.yaml`) do Nguyễn Trọng Phương Bách làm; tôi không nhận phần đó.

## 3. Đóng góp cụ thể

- Gắn nhãn 20 ca độc lập theo nguyên nhân gốc (4 ca do người dùng, 5 hệ thống, 4 ngữ cảnh, 4 giới hạn hệ thống, 3 ngầm).
- Chọn 5 ca cho bảng khắc phục (ca 1, 20, 10, 13, 17), mỗi dòng có cách phát hiện đo được (event, ngưỡng, tần suất) và một vai trò phụ trách.
- Viết `chi_so.md`: ba chỉ số tính thử (82,83% · 27,12% · 4,25%), hai chỉ số tự đề xuất, mười event có `trace_id`, ba dòng rủi ro kinh tế lấy số từ bảng độ nhạy.
- Viết `ho_so_launch_v0.md`: bảy mục có con số chính, trạng thái, người phụ trách; đề xuất Go có điều kiện cùng năm điều kiện.
- Kiểm các số của người viết code: chạy lại `lab13.py`, đối chiếu bảng A2, A3, A4, B1–B4, D1 với đầu ra và với đáp án trên slide.

## 4. Bằng chứng

- Commit `474883e`, `e539ad4`, `e4f4eb8` trên nhánh `main` của repo nhóm.
- Các file: `report/team/bang_loi.md`, `chi_so.md`, `ho_so_launch_v0.md`, `TEAM.md`.
- Con số tự tính: chi phí cả hệ thống (4.373.585 + 222 × 12.000) ÷ 1.200 = 5.865 đ/yêu cầu = 0,49× so với 12.000 đ [simulated]; ba chỉ số E1 tính bằng pandas trên `logix_requests.csv`.

## 5. Công cụ AI đã dùng

Claude Code (trong VS Code), dùng vào các việc sau:

- Đọc repo, đề bài và slide; giải thích quy tắc, thứ tự công việc và cách chia vai cho hai người.
- Dựng khung và soạn nháp `chi_so.md`, `ho_so_launch_v0.md`, `group_report.md`; đề xuất cách sửa cột "phát hiện bằng gì" và "ai phụ trách" của bảng khắc phục để đạt tiêu chí "đo được" và "một vai trò".
- Chạy lệnh kiểm: `lab13.py`, `yaml.safe_load`, `grep` tìm từ "production" và dấu `?`, rà checklist `SUBMISSION.md`.

Cách tự kiểm tra: đối chiếu mọi số trong hồ sơ với đầu ra của `lab13.py` và với slide đáp án (lệch không quá 2%); tính tay con số chi phí cả hệ thống; đọc lại từng cột trạng thái (Giả lập, Xong, Chưa) và vai trò phụ trách.

Nhãn lỗi: [điền cho đúng thực tế: bạn tự gắn 20 ca như thế nào, đã xem bảng nhãn tham khảo trên slide trước hay sau khi gắn, và có trao đổi với người gắn nhãn 1 trước khi gắn hay không].

Các ngưỡng cảnh báo trong `chi_so.md` và bảng khắc phục (7%, 50%, 10%, 1%, 2%) là đề xuất do Claude gợi ý và tôi chấp nhận; chúng không có trong dữ liệu và cần chỉnh theo kết quả pilot.

## 6. Tự đánh giá

- Làm tốt: hồ sơ đủ bảy mục, mọi số simulated có nhãn, đề xuất nêu cả con số bất lợi (xem lại 100% = 0,98× đến 1,03×, mở lại 4,25%, power 0,64 ở mức chênh 5 điểm).
- Chưa tốt: tôi chưa tự viết code tính chi phí (chỉ kiểm lại số của người viết code và tính tay một con số). Nhãn lỗi của tôi đã nằm trong repo trước khi người gắn nhãn 1 điền nên độ độc lập khó chứng minh. Ba chỉ số E1 mới tính tay, chưa có trong `lab13.py`. Các ngưỡng cảnh báo là đề xuất, cần chỉnh theo dữ liệu pilot. Mục 5 của hồ sơ chưa khép lại vì đồng thuận nhãn phụ thuộc nhãn của người gắn nhãn 1.
- Điều tôi hiểu rõ nhất: vì sao tử số tính mọi lần chạy còn mẫu số chỉ đếm việc thành công, và vì sao 20 nhân viên mỗi nhóm không đủ mẫu cho mức chênh 5 điểm (tối đa 20 ÷ 0,02 = 1.000 < 1.251).
