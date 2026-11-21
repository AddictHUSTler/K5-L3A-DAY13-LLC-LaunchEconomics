# Bảng chi phí · Nhiệm vụ A và B

Số tính bằng `src/lab13.py`. Mọi con số tính từ cột `_simulated` ghi nhãn `simulated`. Mỗi câu trả lời không quá ba dòng, có ít nhất một con số.

## A1 · Ba phép thử đáp án biết trước

| Phép thử (p = 0,8) | Kết quả của nhóm |
| --- | --- |
| Số lần chạy trung bình, tối đa 2 lần | 1,20 |
| Số lần chạy trung bình, chạy đến khi đúng | 1,25 |
| Hệ số chi phí mỗi việc thành công, tối đa 3 lần | 1,25 |

## A2 · Mô hình chi phí từ trace

| Khoản | Số tiền (đ) | Nguồn | Nhãn |
| --- | ---: | --- | --- |
| Token | 245.585 | `logix_runs.csv` | đo từ trace |
| Tool | 84.000 | `logix_runs.csv` | đo từ trace |
| Trong đó, phần của lần chạy thứ 2 và 3 | 93.804 | attempt lớn hơn 1 | đo từ trace |
| Xem lại | 1.780.000 | `phut_xem_lai_simulated` | simulated |
| Làm lại | 2.264.000 | `phut_lam_lai_simulated` | simulated |
| Tổng chi phí | 4.373.585 | | có phần simulated |
| Số việc thành công | 978 | `ket_qua` | |
| Chi phí mỗi việc thành công | 4.472 | | simulated |
| Hoá đơn token và tool chia cho số yêu cầu | 274,7 | | đo từ trace |

- Chi phí mỗi việc thành công gấp bao nhiêu lần "hoá đơn chia số yêu cầu"? Gấp 16,3 lần (4.472 ÷ 274,7) [simulated].
- Khoản nào chiếm tỉ trọng lớn nhất trong tổng chi phí, bao nhiêu phần trăm? Làm lại, 51,8% [simulated]; xem lại 40,7% [simulated].

## A3 · Tách theo loại yêu cầu

| Loại | Số yêu cầu | Tỉ lệ thành công | Số lần chạy mỗi yêu cầu | Chi phí mỗi việc thành công | So với 12.000 đ |
| --- | ---: | ---: | ---: | ---: | ---: |
| noi_dia | 824 | 95,0% | 1,11 | 2.696 đ | 0,22× |
| hang_nang | 158 | 74,1% | 1,47 | 8.221 đ | 0,69× |
| quoc_te | 150 | 27,3% | 2,32 | 22.515 đ | 1,88× |
| doi_tac | 68 | 54,4% | 1,88 | 10.215 đ | 0,85× |

- Loại nào không đáng để trợ lý xử lý? Với loại đó, cho chạy lại tới 3 lần có giúp không? `quoc_te`: 1,88× so với 12.000 đ, thành công 27,3%. Chạy lại không giúp: tỉ lệ ok theo lần chạy giảm 30% → 11,4% → 2,2%, lỗi lặp lại nên chỉ tốn thêm tiền. (Tất cả đều [simulated].)

## A4 · Chi phí cố định (phạm vi noi_dia + hang_nang)

Việc thành công mỗi tháng = 45.000 × 900 ÷ 1.200 = 33.750 (900 là số việc thành công của hai loại trong mẫu). Chi phí mỗi việc thành công trong phạm vi: 3.414 đ.

| Khối lượng | Việc thành công mỗi tháng | Chi phí cố định mỗi việc | Chi phí mỗi việc thành công + cố định | So với 12.000 đ |
| --- | ---: | ---: | ---: | ---: |
| 45.000 yêu cầu/tháng | 33.750 | 1.185 đ | 4.599 đ | 0,38× |
| Một nửa khối lượng | 16.875 | 2.370 đ | 5.784 đ | 0,48× |

- Chi phí cố định có đổi kết luận không? Ở khối lượng nào? Không: cả hai khối lượng vẫn dưới 12.000 đ (0,38× và 0,48×) [simulated]. Con số chưa tính phần nhân viên làm thay các ca chuyển nhân viên.

## B1 · Đổi từng yếu tố

| Kịch bản | Cách tính | Chi phí mỗi việc thành công | Thay đổi (%) |
| --- | --- | ---: | ---: |
| Giá token gấp đôi | 52 đ và 260 đ cho 1.000 token; giá tool giữ nguyên | 4.723 đ [simulated] | +5,6% |
| Giá token giảm một nửa | 13 đ và 65 đ | 4.346 đ [simulated] | -2,8% |
| Tỉ lệ xem lại gấp đôi | Tiền xem lại × 2 | 6.292 đ [simulated] | +40,7% |
| Tỉ lệ xem lại giảm một nửa | Tiền xem lại ÷ 2 | 3.562 đ [simulated] | -20,3% |
| Số ca làm lại gấp đôi | Tiền làm lại × 2 | 6.787 đ [simulated] | +51,8% |
| Số ca làm lại giảm một nửa | Tiền làm lại ÷ 2 | 3.315 đ [simulated] | -25,9% |
| Lương nhân viên tăng 25% | 2.500 đ mỗi phút | 5.506 đ [simulated] | +23,1% |
| Chỉ cho chạy tối đa 2 lần | Bỏ lần chạy có attempt > 2; yêu cầu có so_lan_chay > 2 coi là chuyen_nhan_vien | 4.237 đ [simulated] | -5,2% |
| Chỉ cho chạy 1 lần | Như trên với giới hạn 1 | 4.111 đ [simulated] | -8,1% |

Gốc (A2): 4.472 đ [simulated]. Mỗi kịch bản "giảm một nửa" bằng đúng nửa mức tăng của "gấp đôi" (xem lại 20,3 so với 40,7; làm lại 25,9 so với 51,8; token 2,8 so với 5,6): sai số chỉ do làm tròn.

## B2 · Đổi một cặp và xếp hạng

- Giá token gấp đôi cùng lúc tỉ lệ xem lại gấp đôi: 6.543 đ (+46,3%) [simulated], bằng tổng hai tác động riêng (5,6% + 40,7%) vì mô hình cộng tuyến tính.
- Xếp hạng ba yếu tố ảnh hưởng mạnh nhất: 1. số ca làm lại (±51,8% / 25,9%) · 2. tỉ lệ xem lại (±40,7% / 20,3%) · 3. lương nhân viên (+23,1%). Giá token chỉ +5,6%, không phải yếu tố chính.

## B3 · Giới hạn chạy lại có thật sự rẻ hơn

Chi phí cả hệ thống = tổng chi phí trợ lý + 12.000 đ × số yêu cầu không thành công.

| Giới hạn | Tổng chi phí trợ lý | Số yêu cầu không thành công | Chi phí cả hệ thống | Chi phí mỗi việc thành công |
| --- | ---: | ---: | ---: | ---: |
| 1 lần | 3.621.781 đ [simulated] | 319 | 7.449.781 đ [simulated] | 4.111 đ (thấp nhất) |
| 2 lần | 4.093.220 đ [simulated] | 234 | 6.901.220 đ (rẻ nhất) [simulated] | 4.237 đ |
| 3 lần | 4.373.585 đ [simulated] | 222 | 7.037.585 đ [simulated] | 4.472 đ |

- Giới hạn 2 lần rẻ nhất cho công ty (6.901.220 đ), nhưng không trùng giới hạn cho chi phí mỗi việc thành công thấp nhất (1 lần, 4.111 đ). Chọn 1 lần đẩy thêm 85 yêu cầu (319 − 234) sang nhân viên [simulated].

## B4 · Nếu phải xem lại tất cả

- Xem lại 100% (`noi_dia` + `hang_nang`, 982 yêu cầu): 948 yêu cầu có ít nhất một lần chạy ok × 5 phút = 9.480.000 đ; 48 ca làm lại × 9 phút = 864.000 đ; token + tool 224.513 đ. Tổng 10.568.513 đ ÷ 900 việc thành công = 11.743 đ = 0,98× so với 12.000 đ [simulated].
- Nếu dùng 15,3 phút làm lại trung bình trong dữ liệu (tham khảo, không chấm): 12.414 đ = 1,03× [simulated], tức đắt hơn nhân viên tự làm. Pilot cần học tỉ lệ xem lại có thể giảm an toàn đến đâu và mỗi lần xem lại có ngắn hơn 5 phút không.
