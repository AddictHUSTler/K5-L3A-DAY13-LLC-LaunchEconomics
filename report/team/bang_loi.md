# Bảng lỗi và cách khắc phục · Nhiệm vụ C

20 ca lỗi nằm trong `docs/Ngay13_Lab13_De_bai_hoc_vien.docx`. Năm loại theo Google PAIR: **Do người dùng · Hệ thống · Ngữ cảnh · Giới hạn hệ thống · Ngầm**. Gắn nhãn theo nguyên nhân gốc, không theo chỗ cần sửa.

## Định nghĩa năm loại lỗi

| Loại lỗi | Định nghĩa | Dấu hiệu nhận biết cốt lõi |
| :--- | :--- | :--- |
| **Do người dùng** | Người dùng nhập sai, chọn sai luồng hoặc cung cấp thông tin không khớp yêu cầu. | Đầu vào từ khách hàng không hợp lệ (sai định dạng, chọn nhầm nút/danh mục). |
| **Hệ thống** | Hệ thống trả lời sai, thực thi sai logic/công cụ hoặc vi phạm thiết kế và chính sách; sai đã lộ ra (có người thấy). | Lỗi kỹ thuật, gọi sai tham số, ảo giác chính sách, xử lý sai nghiệp vụ. |
| **Ngữ cảnh** | Hệ thống làm đúng thiết kế nhưng người dùng thấy sai do kỳ vọng hoặc hoàn cảnh thực tế khác biệt. | Trợ lý làm đúng quy trình, nhưng thông tin giao tiếp thiếu giải thích hoặc trải nghiệm gây hiểu lầm. |
| **Giới hạn hệ thống** | Hệ thống không thể xử lý do thiếu dữ liệu, ngoài phạm vi nghiệp vụ hoặc không hỗ trợ định dạng đầu vào. | Trợ lý chạm ranh giới năng lực (dữ liệu quá hạn, đối tác ngoài, file âm thanh). |
| **Ngầm** | Có sai sót xảy ra nhưng cả người dùng lẫn hệ thống đều không nhận ra ngay lúc đó. | Không có khiếu nại và không có cảnh báo tự động; chỉ phát hiện khi kiểm tra mẫu hoặc kiểm toán. |

## Hai bộ nhãn độc lập

Người gắn nhãn 1: Nguyễn Trọng Phương Bách · Người gắn nhãn 2: Trần Thái Hưng (gắn trong 8 phút, không trao đổi)

| Ca | Nhãn người 1 | Nhãn người 2 | Trùng? | Nhãn thống nhất |
| --: | --- | --- | --- | --- |
| 1 | ... | Do người dùng | ... | ... |
| 2 | ... | Hệ thống | ... | ... |
| 3 | ... | Ngữ cảnh | ... | ... |
| 4 | ... | Giới hạn hệ thống | ... | ... |
| 5 | ... | Ngầm | ... | ... |
| 6 | ... | Do người dùng | ... | ... |
| 7 | ... | Hệ thống | ... | ... |
| 8 | ... | Hệ thống | ... | ... |
| 9 | ... | Do người dùng | ... | ... |
| 10 | ... | Ngữ cảnh | ... | ... |
| 11 | ... | Giới hạn hệ thống | ... | ... |
| 12 | ... | Ngầm | ... | ... |
| 13 | ... | Giới hạn hệ thống | ... | ... |
| 14 | ... | Do người dùng | ... | ... |
| 15 | ... | Hệ thống | ... | ... |
| 16 | ... | Ngữ cảnh | ... | ... |
| 17 | ... | Ngầm | ... | ... |
| 18 | ... | Ngữ cảnh | ... | ... |
| 19 | ... | Giới hạn hệ thống | ... | ... |
| 20 | ... | Hệ thống | ... | ... |

**Tỉ lệ đồng thuận:** ... / 20 = ...% (chưa tính được: bộ nhãn của người gắn nhãn 1 chưa có vì người gắn nhãn 1 tạm dừng; sẽ bổ sung khi người gắn nhãn 1 quay lại và tự gắn 20 ca.)

## Quy tắc phân biệt cho các ca không trùng

Mỗi ca không trùng một câu. Đồng thuận dưới 80% thì ghi định nghĩa đã viết lại. Hiện chưa có ca không trùng nào được xác định, vì chưa có bộ nhãn thứ hai. Các quy tắc phân biệt nhanh dưới đây dùng khi so nhãn:

- **Hệ thống và Giới hạn hệ thống:** nếu nằm ngoài phạm vi hoặc dữ liệu và trợ lý thừa nhận không làm được, chuyển nhân viên (ca 4, 11, 19) thì là **Giới hạn hệ thống**. Ngoài phạm vi là giới hạn kể cả khi trợ lý xử lý kém (ca 13). Nếu trợ lý làm sai logic, API hoặc chính sách (ca 2, 7, 8, 15, 20) thì là **Hệ thống**.
- **Do người dùng và Ngữ cảnh:** nếu khách nhập hoặc chọn sai (ca 1, 6, 9, 14) thì là **Do người dùng**; việc trợ lý không gợi ý lại là việc cần cải thiện, ghi ở cột khắc phục. Nếu khách thao tác đúng và trợ lý làm đúng thiết kế nhưng cách phản hồi, thời điểm hoặc thông tin xung quanh gây hiểu lầm (ca 3, 10, 16, 18) thì là **Ngữ cảnh**.
- **Hệ thống và Ngầm:** nếu sai đã lộ ra (có người thấy, ví dụ ca 8, 15) thì là **Hệ thống**; nếu sai trôi qua không khiếu nại, không cảnh báo và chỉ lộ ra khi kiểm tra mẫu (ca 5, 12, 17) thì là **Ngầm**, kể cả khi sai chỉ về chi phí như ca 12.

## Bảng khắc phục cho 5 ca, mỗi loại một ca

Cách phát hiện phải đo được (event, ngưỡng, tần suất). Người phụ trách là một vai trò, không ghi "cả đội".

| Ca | Loại lỗi | Phát hiện bằng gì | Khắc phục thế nào | Ai phụ trách |
| --: | --- | --- | --- | --- |
| 1 | Do người dùng | Event `input_validation_failed` (số tài khoản sai độ dài/định dạng) và lệnh hoàn bị ngân hàng trả lỗi; cảnh báo khi quá 2% yêu cầu/ngày | Kiểm tra độ dài/định dạng ngay khi nhập; hiển thị tên chủ tài khoản đã che một phần để khách xác nhận trước khi tạo lệnh; thông báo lỗi nêu rõ cách nhập lại | PM trợ lý hoàn phí |
| 20 | Hệ thống | Đối soát hằng ngày: đơn có hơn 1 lệnh hoàn; cảnh báo khi số lệnh hoàn/đơn > 1 | Thêm khoá chống trùng (idempotency key) cho mỗi lệnh hoàn; gửi lại cùng khoá thì trả kết quả cũ, không tạo lệnh mới. Hoàn lại 2 lần đã phát sinh | Kỹ sư trưởng agent |
| 10 | Ngữ cảnh | Event `ticket_reopened` sau từ chối vì bất khả kháng đúng chính sách; cảnh báo khi tỉ lệ mở lại nhóm này vượt 10% số ca từ chối theo tuần (ngưỡng đề xuất, chỉnh theo dữ liệu pilot) | Hiện lưu ý "cam kết không áp dụng khi bất khả kháng" khi có cảnh báo thời tiết; tin từ chối nêu rõ căn cứ và điều khoản | Trưởng nhóm CSKH |
| 13 | Giới hạn hệ thống | Event `handoff_to_staff` với `reason = ngoai_pham_vi`; rà soát 20 ca/tuần, ngưỡng 0 ca thiếu câu "không xử lý được" | Nhận diện ý định ngoài phạm vi; luôn nói rõ "tôi không xử lý được yêu cầu này" và hướng khách tới kênh của công ty bảo hiểm đối tác | PM trợ lý hoàn phí |
| 17 | Ngầm | Không tự phát hiện; kiểm mẫu 100 đơn/tuần, đối soát giá đã tính với bảng giá hiện hành, cảnh báo khi >1% đơn lệch | Gắn phiên bản bảng giá vào khoá cache; khi đổi bảng giá thì xoá cache; đặt TTL ngắn; cảnh báo khi phiên bản cache ≠ phiên bản hiện hành; hoàn bù 212 đơn | Kế toán trưởng |
