# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Một trang. Cột trạng thái chỉ nhận: **Xong, có bằng chứng · Chưa · Giả lập**. Mục nào dựa trên cột `_simulated` ghi Giả lập. Người phụ trách là một vai trò, không ghi "cả đội". Gate 2a chỉ duyệt kế hoạch pilot: không viết như thể trợ lý đã được duyệt chạy chính thức (xem quy tắc 5 trong `README.md`).

Nhóm: LLC · Lớp: L3A

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | 4.472 đ, gấp 16,3× hoá đơn token + tool chia số yêu cầu (274,7 đ). Làm lại chiếm 51,8% và xem lại 40,7% tổng chi phí [simulated] | Giả lập | PM trợ lý hoàn phí |
| 2 · Ba yếu tố nhạy nhất | 1. số ca làm lại (+51,8% nếu gấp đôi) · 2. tỉ lệ xem lại (+40,7%) · 3. lương nhân viên (+23,1% nếu tăng 25%). Giá token chỉ +5,6% [simulated] | Giả lập | PM trợ lý hoàn phí |
| 3 · So với nhân viên tự làm | Chi phí cả hệ thống: (4.373.585 + 222 × 12.000) ÷ 1.200 = 5.865 đ/yêu cầu = 0,49× so với 12.000 đ [simulated]. Phạm vi noi_dia + hang_nang cộng cố định 40 triệu đ/tháng: 4.599 đ = 0,38× (còn 5.784 đ = 0,48× nếu một nửa khối lượng) [simulated]. Xem lại 100%: 11.743 đ = 0,98× (1,03× nếu làm lại 15,3 phút) [simulated] | Giả lập | Giám đốc vận hành LogiX-VN |
| 4 · Chỉ số chính, chỉ số dùng, chỉ số an toàn | Trong đợt chạy thử: chính 82,83% (994/1.200) · dùng, bỏ qua gợi ý 27,12% (48/177) · an toàn, mở lại 7 ngày 4,25% (51/1.200). Không có nhóm đối chứng nên không kết luận trợ lý đã nâng chỉ số | Xong, có bằng chứng | PM trợ lý hoàn phí |
| 5 · Bảng lỗi và cách khắc phục | 20 ca gắn nhãn theo Google PAIR; bảng khắc phục 5 ca, mỗi loại một ca, mỗi dòng có cách phát hiện đo được và một vai trò. Tỉ lệ đồng thuận hai người gắn nhãn: chờ nhãn người 1 | Chưa | Trưởng nhóm CSKH |
| 6 · Pilot plan | Chờ CP4 (`pilot_plan.yaml`): cỡ mẫu, cách chia, luật dừng | Chưa | Giám đốc vận hành LogiX-VN |
| 7 · Rủi ro kinh tế | Làm lại gấp đôi: +51,8% (6.787 đ) · xem lại 100% kéo dài: 0,98× đến 1,03× · khối lượng giảm một nửa: cố định thêm 2.370 đ/việc [simulated] | Giả lập | PM trợ lý hoàn phí |

**Đề xuất:** Go có điều kiện cho pilot phạm vi noi_dia + hang_nang (bản nháp, chốt sau CP4). Phạm vi thu hẹp vì quoc_te đắt hơn nhân viên (1,88×, thành công 27,3%) và doi_tac sát ngưỡng (0,85×) [simulated].

- Con số bất lợi: xem lại 100% làm chi phí chạm 0,98× đến 1,03× nên gần như không tiết kiệm được; mở lại trong 7 ngày hiện là 4,25%, nên ngưỡng dừng tuyệt đối 3% sẽ dừng pilot ngay tuần đầu. Xử lý bằng cách giảm xem lại theo bậc và đặt ngưỡng dừng so với nhóm đối chứng.
- Điều kiện 1: sửa khoá chống trùng và đối soát sổ cái (ca 20, ca 7) trước ngày bắt đầu. Người phụ trách: Kỹ sư trưởng agent. Ngày kiểm tra: chờ chốt.
- Điều kiện 2: bật đủ event có `trace_id` và thay phút simulated bằng phút đo thật sau tuần 1. Người phụ trách: PM trợ lý hoàn phí. Ngày kiểm tra: chờ chốt.
- Điều kiện 3: kế hoạch giảm xem lại theo bậc khi tỉ lệ sửa + bỏ dưới 15%. Người phụ trách: Trưởng nhóm CSKH. Ngày kiểm tra: chờ chốt.
- Điều kiện 4: kiểm tra mẫu hằng tuần (100 đơn, ngưỡng 1%) để bắt lỗi ngầm như ca 5, 12, 17. Người phụ trách: Kế toán trưởng. Ngày kiểm tra: chờ chốt.
- Điều kiện 5 (chờ CP4): Giám đốc vận hành ký chấp nhận mức chênh đã chọn trong `pilot_plan.yaml`, kèm power thực tế của mức chênh đó. Người phụ trách: Giám đốc vận hành LogiX-VN.
