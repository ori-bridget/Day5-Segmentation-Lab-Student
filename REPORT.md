# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Báo cáo được tổng hợp từ dữ liệu task, 9 ZIP trong `submissions/` và kết quả self-check local.** Giữ nguyên bốn mục và bảng để coach đọc nhanh. Các thông tin cá nhân hoặc thao tác không có trong file dữ liệu được ghi rõ là chưa cung cấp.

- Mã học viên theo lớp: 2A202602141
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | `cp1_holes.zip` | 1 / 1 | 3 |
| cp2_slice | `cp2_slice.zip` | 1 / 1 | 3 |
| cp5_occlusion | `cp5_occlusion.zip` | 1 / 1 | 3 |
| cp3_thin | `cp3_thin.zip` | 1 / 1 | 3 |
| cp4_curb | `cp4_curb.zip` | 1 / 1 | 3 |
| cp6_coverage | `cp6_coverage.zip` | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Kiểm tra cấu trúc export: **9/9 task OK**, đúng ảnh, class và dạng mask. Self-check với ground truth ba tier: `easy_semantic` **20.0/20**, `medium_instance` **4.4/32**, `hard_panoptic` **16.5/30**, tổng **40.9/82**. Sáu checkpoint chưa có ground truth nên chưa tính điểm.

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000181542.jpg`, người phụ nữ mặc áo dài ở trung tâm ảnh.
- Class và quy tắc tôi dùng để chọn biên: `person`; chỉ tô silhouette nhìn thấy, không vẽ phần cơ thể bị xe máy hoặc vật khác che.
- Nếu dùng gợi ý sau đó: chưa có dữ liệu xác nhận việc dùng gợi ý tự động; cần bổ sung nếu đã dùng.
- Nếu không dùng gợi ý: không dùng gợi ý tự động; mask được tạo và kiểm tra trong CVAT.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`, đặc biệt `000000373353.jpg` và `000000458325.jpg`, vùng ô tô đỗ hai bên và người đi bộ ở giữa/xa ảnh.
- Lỗi thuộc loại: thiếu vật.
- Bằng chứng tôi nhìn thấy: scorer đối chiếu 48 annotation đã nộp với 71 annotation ground truth; có `FN = 31`, recall `0.56`. Ở `000000373353.jpg`, ZIP có 5 car và 5 person trong khi reference có 13 car và 12 person; ở `000000458325.jpg`, ZIP có 11 car và 4 person trong khi reference có 13 car và 12 person.
- Quy tắc và hành động sửa: cần mở lại hai ảnh trong CVAT, quét lần lượt trái–phải để bổ sung từng ô tô/người nhìn thấy, giữ mỗi vật là một mask riêng, sau đó Save và export lại.
- Sau sửa đã Save và export lại chưa? Chưa có ZIP mới sau lượt self-check này; ZIP hiện tại vẫn là bản đã chấm ở trên.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `easy_semantic / 817bca71-00000000.jpg`, các căn nhà bị cây che | Tô toàn bộ một căn nhà hay chỉ phần nhìn thấy? | Semantic chỉ cần class `building`; quy tắc chung là không đoán phần bị che. | Chọn chỉ tô mái/tường/garage nhìn thấy; không tô cây, xe hoặc phần nhà phía sau cây. |
| `cp4_curb / 7d83710e-4697c3b2.jpg`, ranh bó vỉa bên đường | Một dải bê tông là `road` hay `sidewalk`? | Ranh dựa vào chức năng sử dụng và bó vỉa, không chỉ dựa vào màu xám. | Chọn `sidewalk` cho phần dành cho người đi bộ, `road` cho phần xe chạy; cần coach xác nhận nếu ranh bị mờ. |
| `cp5_occlusion / 000000336232.jpg`, xe bị xe khác che | Tách các mảng nhìn thấy thành nhiều object hay giữ một object? | Vật bị che vẫn là một instance; chỉ tô phần nhìn thấy, không vẽ xuyên vật che. | Giữ cùng một instance cho các mảng thuộc cùng xe; không nối qua vùng bị che bằng mask giả. |
