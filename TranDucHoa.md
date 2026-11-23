# Phiếu QC 1 — Road v1.0

**Lô được kiểm (học viên):** Trần Đức Hòa  
**Người kiểm (học viên):** Vũ Thị Thu Huyền  
**Ngày:** 22/11/2026  
**Phiên bản guideline:** Road v1.0  
**File được kiểm:** `TranDucHoa-front.zip`, `TranDucHoa-fisheye.zip` — revision 1  
**Số ảnh kiểm:** 6 ảnh đề xuất (A04, A05, A09, A13, A14, B04), cùng các cảnh báo lint ngoài mẫu  
**Số nhãn đã kiểm (shape + tag):** 42 shape trong 6 ảnh; số tag và số nhãn kiểm trực quan cần người kiểm xác nhận.

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi xác nhận | Mức |
|---|---|---:|---:|---|
| QC1-01 tag camera | Sai thuộc tính / bỏ sót | Chưa chốt | Chưa xác định | Nặng |
| QC1-02 đủ L1, R1 | Bỏ sót | 4 vị trí cảnh báo trong mẫu | 0 xác nhận; 4 chờ lead | Nặng |
| QC1-03 position | Sai thuộc tính / thừa | 11 lane trong mẫu | 1 (A13) | Nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | Sai phạm vi / bỏ sót | Chưa chốt | Chưa xác định | Chính |
| QC1-05 vạch đứt, che | Sai phạm vi / sai thuộc tính | 5 cảnh báo lint trên toàn lô | 0 — đã xác minh hợp lệ | Chính |
| QC1-06 style, color, kind | Sai thuộc tính | Chưa chốt | Chưa xác định | Chính |
| QC1-07 vùng lái | Sai phạm vi / bỏ sót / thừa | Chưa chốt | Chưa xác định | Chính |
| QC1-08 đèn, màu | Bỏ sót / sai phạm vi / sai thuộc tính | Chưa chốt | Chưa xác định | Nặng / chính |
| QC1-09 facing, type, group, biển phụ | Sai thuộc tính | Chưa chốt | Chưa xác định | Chính |
| QC1-10 hình in, đủ biển | Bỏ sót / sai phạm vi | Chưa chốt | Chưa xác định | Chính |
| QC1-11 fisheye | Sai phạm vi / sai thuộc tính | Chưa chốt | Chưa xác định | Chính |
| QC1-12 file | Lỗi file | 2 ZIP | 0 lỗi mở file; 1 cảnh báo điểm trùng cần xác minh | Nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
|---|---|---|---|---|---|
| 1 | QC1-03 | A13 | lane, ID chưa xác định | Nặng | Gán nhầm position từ R1 thành L1. Người gán đã xác định lỗi, cần sửa và xác nhận lại bản export. |

## Các cảnh báo đã xác minh hợp lệ

| Mã | Ảnh | Kết luận |
|---|---|---|
| QC1-05 | A04 | Hai polyline cùng L1 do vạch đôi, hợp lệ |
| QC1-05 | A09 | Hai polyline cùng L2 do vạch đôi, hợp lệ |
| QC1-05 | A11 | Hai polyline cùng L1 do vạch đôi, hợp lệ |
| QC1-05 | A13 | Hai polyline cùng L1 do vạch đôi, hợp lệ về cách biểu diễn vạch đôi; lỗi gán nhầm R1 vẫn cần sửa riêng |
| QC1-05 | A14 | Hai polyline cùng L1 do vạch đôi, hợp lệ |

**Giải trình QC1-05:** Các trường hợp hai polyline cùng thuộc tính `position` đã được đối chiếu trực tiếp với ảnh gốc. Đây là các vạch đôi, cần biểu diễn hai đường riêng biệt. Thầy hướng dẫn đã xác nhận cách gán này là hợp lệ. Vì vậy, cả 5 cảnh báo QC1-05 là false positive của công cụ lint, không phải lỗi annotation và không cần chỉnh sửa chỉ để loại bỏ cảnh báo.

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
|---|---|---|
| A05 | Không nhìn thấy L1 và R1, có được bỏ qua hai vạch này không? | Chờ lead xác nhận |
| A06 | Không nhìn thấy R1, có được bỏ qua không? | Chờ lead xác nhận |
| A07 | Không nhìn thấy L1, có được bỏ qua không? | Chờ lead xác nhận |
| A08 | Không nhìn thấy L1, có được bỏ qua không? | Chờ lead xác nhận |
| A09 | Không nhìn thấy R1, có được bỏ qua không? | Chờ lead xác nhận |
| A14 | Không nhìn thấy R1, có được bỏ qua không? | Chờ lead xác nhận |

**Ca đã được giải đáp:** A04, A09, A11, A13, A14 có hai polyline cùng position vì là vạch đôi. Thầy hướng dẫn đã xác nhận hợp lệ, không cần xin xác nhận lại về cách biểu diễn này.

**Cảnh báo nhẹ cần kiểm tra:** Một số bounding box của đèn/biển có chiều cao dưới 8 px; tại B04, crosswalk có điểm polygon trùng liên tiếp. Chưa kết luận đây là lỗi thực tế.

## Quyết định

**Lỗi nặng:** 1 lỗi đã xác nhận (A13 — QC1-03).  
**Lỗi chính:** 0 lỗi đã xác nhận / chưa chốt tổng số nhãn kiểm thủ công = chưa tính được tỷ lệ cuối cùng.  
**Lỗi nhẹ:** Chưa xác nhận lỗi thực tế.  
**Ca chờ lead:** 6 ảnh (7 vị trí L1/R1 chưa nhìn thấy).

**Quyết định: REWORK — revision 1**

**Lý do (theo luật của phiếu):**

- Phát hiện một lỗi nặng QC1-03 tại ảnh A13: gán nhầm thuộc tính R1 thành L1.
- Sáu ảnh A05, A06, A07, A08, A09 và A14 được người gán xác nhận không nhìn thấy vạch đường tương ứng. Chưa tính là lỗi bỏ sót, cần lead xác nhận.
- Cả 5 cảnh báo QC1-05 về polyline cùng position đã được kiểm tra, xác định là vạch đôi và được thầy hướng dẫn công nhận hợp lệ.
- Các cảnh báo nhẹ còn lại không tự động được tính là lỗi nếu chưa kiểm tra trực quan.

**Hướng xử lý:** Sửa thuộc tính position tại A13, export lại ZIP và chạy lint revision 2. Hoàn thành xác nhận của lead về các vạch L1/R1 không nhìn thấy. Người kiểm đối chiếu lại các mục chưa kiểm, tính tỷ lệ lỗi và chốt quyết định cuối cùng.

---

**Người kiểm:** Vũ Thị Thu Huyền  
**Trạng thái:** Dự thảo cập nhật theo kết quả kiểm tra và xác nhận của thầy; cần người kiểm hoàn tất xác nhận trước khi nộp.

*Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ hoặc tràn vùng. Sai thuộc tính và lỗi file là các nhóm bổ sung của khóa học.*