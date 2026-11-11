# Báo cáo thực hành Day 3

- Mã học viên theo lớp: 2A202603215
- Ngày / CVAT local: 12/11/2026
- Công cụ đã dùng: CVat local
- Tài liệu tham khảo: README.md, guideline-mini-sheet.md và hướng dẫn/ảnh gợi ý từ Codex. Em tự vẽ lại toàn bộ trên CVAT.

## 1. Bài đã nộp

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

## 2. Một quyết định trước khi dùng gợi ý

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000181542.jpg`, người phụ nữ mặc áo dài trắng ở giữa ảnh.
- Class và quy tắc chọn biên: `person`. Em vẽ theo phần người nhìn thấy, gồm áo, tay và chân; không lấy xe máy hoặc mặt đường vào mask. Người và xe máy là hai object riêng.
- Gợi ý tham khảo sau đó: em tham khảo cách phân biệt người với xe máy rồi tự vẽ riêng từng object, không dùng trực tiếp mask có sẵn. Cách này tránh gộp người ngồi trên xe vào nhãn `motorcycle`.

## 3. Một lỗi tôi tìm thấy và sửa

- Task/ảnh/vùng: `cp6_coverage`, ảnh `7daa6479-67988f3f.jpg`, bó vỉa chạy chéo ở nửa dưới bên phải.
- Loại lỗi: biên.
- Bằng chứng: biên trong bản tham khảo lệch vào mặt vỉa hè, có nhiều điểm thừa làm đường viền gãy dù mép bó vỉa khá rõ.
- Quy tắc và cách sửa: em tự vẽ lại theo mép bó vỉa tiếp giáp mặt đường, giữ phần vỉa hè thuộc `sidewalk` và mặt đường thuộc `road`. Chỉ đặt thêm điểm ở chỗ đường viền đổi hướng.
- Sau sửa: đã Save và export lại `cp6_coverage.zip` theo định dạng Segmentation mask 1.1.
- Tự kiểm: đã kiểm tra cấu trúc ZIP; chưa có điểm tự đánh giá với reference.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `cp5_occlusion` — `000000336232.jpg`, hai taxi vàng ở tiền cảnh | Một xe bị che thành nhiều mảng hay hai xe khác nhau? | Hai xe có phần thân, kính và đường viền riêng. Cùng class không có nghĩa là cùng instance. | Giữ hai object `car` riêng; chỉ vẽ phần nhìn thấy của từng xe. |
| `cp6_coverage` — `7daa6479-67988f3f.jpg`, nền tối bên phải | `road` hay `sidewalk` vì màu khá giống nhau? | Dựa vào bó vỉa và vùng dành cho người đi bộ, không dựa riêng vào màu hoặc bóng đổ. | Phần phía trong bó vỉa là `sidewalk`, phần lòng đường là `road`. |
| `cp6_coverage` — `7daa6479-67988f3f.jpg`, xe buýt giữa ảnh và xe tải bên trái | Gán `car` hay để ngoài bộ nhãn? | Đây là xe buýt và xe tải, nhưng bộ nhãn của task không có `bus` và `truck`. | Để ngoài bộ nhãn, không ép thành `car` để tăng diện tích phủ. |
