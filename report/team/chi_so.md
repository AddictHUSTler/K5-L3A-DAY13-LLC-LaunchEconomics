# Đặc tả chỉ số, event và rủi ro kinh tế · Nhiệm vụ E1, E2

## E1 · Đặc tả chỉ số

| Loại | Chỉ số | Công thức | Tính thử trên 1.200 yêu cầu |
| --- | --- | --- | --- |
| Chính (kết quả) | % yêu cầu đóng trong 24 giờ và không mở lại trong 7 ngày | `dong_trong_24h` bằng 1 và `mo_lai_trong_7_ngay` bằng 0, chia tổng số yêu cầu | 82,83% (994/1.200) |
| Dùng | Tỉ lệ bỏ qua gợi ý | `quyet_dinh_xem_lai` là `sua` hoặc `bo`, chia số yêu cầu được xem lại | 27,12% (48/177) |
| An toàn | Tỉ lệ lỗi lọt đến khách | `mo_lai_trong_7_ngay` bằng 1, chia tổng số yêu cầu | 4,25% (51/1.200) |
| Dùng | Nhóm tự đề xuất: % yêu cầu của nhân viên nhóm can thiệp được mở bằng trợ lý | số yêu cầu có `agent_suggestion_shown` chia số yêu cầu của nhân viên nhóm can thiệp, theo tuần | Không cần tính |
| An toàn | Nhóm tự đề xuất: % đơn hoàn sai tiền qua kiểm tra mẫu hằng tuần (bắt lỗi ngầm, ví dụ ca 5, 12, 17) | `so_tien_da_hoan` khác `so_tien_dung`, chia số đơn kiểm mẫu, 100 đơn/tuần; ngưỡng cảnh báo 1% | Không cần tính |

Cách tính ba số trên: pandas trực tiếp trên `logix_requests.csv` đọc với `keep_default_na=False`, theo đúng công thức ở cột 3 (chưa nằm trong `src/lab13.py`). Cả ba cột đều không phải cột `_simulated`, nên không có nhãn simulated.

Viết "chỉ số trong đợt chạy thử là 82,83%", không viết "trợ lý đã nâng chỉ số": đợt chạy thử không có nhóm đối chứng. Chỉ số an toàn "mở lại trong 7 ngày" không bắt được lỗi ngầm (ca 5, 12, 17), nên cần thêm chỉ số kiểm mẫu ở dòng cuối bảng.

Với phạm vi pilot (`noi_dia` + `hang_nang`), tỉ lệ mở lại trong 7 ngày là 3,97% (39/982) và tỉ lệ làm lại là 4,89% (48/982).

## Danh sách event

Ít nhất sáu event, mỗi event có `trace_id` để nối với trace của agent.

| Event | Ai tạo | Thuộc tính chính | Thời điểm |
| --- | --- | --- | --- |
| `refund_request_created` | Ứng dụng khách | request_id, loai, so_tien, arm, trace_id | Khi khách gửi yêu cầu |
| `agent_run_completed` | Agent | attempt, tokens_in, tokens_out, tool_calls, status, trace_id | Sau mỗi lần chạy, kể cả lần lỗi |
| `agent_suggestion_shown` | Giao diện nhân viên | staff_id, so_tien_de_xuat, trace_id | Khi gợi ý hiện ra |
| `staff_review_decision` | Nhân viên | quyet_dinh (giu/sua/bo), phut_xem_lai (đo thật), trace_id | Khi nhân viên bấm gửi, sửa hoặc bỏ |
| `refund_ledger_write` | Dịch vụ sổ cái | idempotency_key, so_tien, ket_qua, trace_id | Khi ghi sổ |
| `handoff_to_staff` | Agent | reason, tom_tat, trace_id | Khi chuyển cho nhân viên |
| `ticket_closed` | Hệ thống ticket | closed_at, trace_id | Khi đóng yêu cầu |
| `ticket_reopened` | Khách | reopened_at, reason, trace_id | Khi khách mở lại |
| `audit_sample_checked` | Kế toán | so_tien_da_hoan, so_tien_dung, trace_id | Hằng tuần, 100 đơn |
| `input_validation_failed` | Agent | truong_loi, loai, trace_id | Khi đầu vào của khách sai định dạng |

**Kiểm tra chéo:** với mỗi chỉ số ở bảng E1, event dùng để tính:

- Chỉ số chính: `ticket_closed` (đóng trong 24 giờ, so với thời điểm tạo ở `refund_request_created`) và `ticket_reopened` (mở lại trong 7 ngày).
- Chỉ số dùng (bỏ qua gợi ý): `staff_review_decision` (số `sua` + `bo` chia số được xem lại).
- Chỉ số an toàn (mở lại trong 7 ngày): `ticket_reopened`.
- Chỉ số dùng tự đề xuất: `agent_suggestion_shown` chia `refund_request_created` theo `staff_id` và `arm`.
- Chỉ số an toàn tự đề xuất: `audit_sample_checked`.
- Mọi chỉ số đều tính được từ danh sách event trên, nên chưa có chỉ số nào ở trạng thái chưa đo được.

## E2 · Rủi ro kinh tế

Số lấy từ bảng độ nhạy (`bang_chi_phi.md`). Mọi số tiền đều là số simulated.

| Rủi ro | Tác động đã tính | Dấu hiệu theo dõi | Hành động | Người phụ trách |
| --- | --- | --- | --- | --- |
| Số ca làm lại tăng gấp đôi | +51,8%, chi phí mỗi việc thành công từ 4.472 đ lên 6.787 đ [simulated] | Tỉ lệ làm lại theo tuần vượt 7% (đợt chạy thử: 4,89% trong phạm vi noi_dia + hang_nang; ngưỡng 7% là đề xuất) | Thu hẹp pilot về `noi_dia`, rà 20 trace làm lại | PM trợ lý hoàn phí |
| Phải xem lại 100% kéo dài | 11.743 đ = 0,98× so với 12.000 đ; 12.414 đ = 1,03× nếu dùng 15,3 phút làm lại như trong dữ liệu [simulated] | Tỉ lệ yêu cầu được xem lại còn trên 50% khi hết bước rollout 0,25 (đợt chạy thử: 13,0% trong phạm vi; ngưỡng 50% là đề xuất) | Giảm xem lại theo bậc khi tỉ lệ sửa + bỏ dưới 15% | Trưởng nhóm CSKH |
| Khối lượng thấp hơn dự kiến, chi phí cố định 40 triệu đ/tháng | Cố định thêm 1.185 đ/việc ở 45.000 yêu cầu/tháng (tổng 4.599 đ = 0,38×); thêm 2.370 đ/việc nếu còn một nửa (tổng 5.784 đ = 0,48×) [simulated] | Số việc thành công theo tuần dưới 50% kế hoạch | Không mở rộng pilot, xem lại hợp đồng chi phí cố định | PM trợ lý hoàn phí |
