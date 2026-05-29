## Shortlist và score

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Canteen Supply | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 35 |
| Education Support System | 4 | 5 | 4 | 3 | 4 | 4 | 3 | 27 |
| Vapp Attendance | 3 | 5 | 4 | 3 | 3 | 3 | 4 | 25 |


Nhóm chọn: Canteen Supply.

Vì sao chọn:
-Có workflow rõ nhất: Quy trình từ khâu đầu bếp ước lượng số lượng, nấu nướng cho đến khi học viên xếp hàng ăn diễn ra cố định hàng ngày, không bị biến động về mặt các bước xử lý.
-Có baseline thời gian: Đo lường được ngay thời gian lãng phí của học viên phải chờ đợi (15-20 phút) và khung giờ cao điểm gây nghẽn (12h45 - 13h30).
-Có thể validate nhanh với các bên liên quan: Dễ dàng phỏng vấn trực tiếp đầu bếp canteen về cách họ ước lượng nguyên liệu và khảo sát nhanh học viên về tần suất bị hết món.
-Có thể research các tool/pattern có sẵn: Bài toán dự đoán chuỗi thời gian (Time Series Forecasting) dựa trên các biến số (lịch học, lịch thi, thời tiết, dữ liệu điểm danh quá khứ) đã có rất nhiều mô hình mẫu chuẩn để áp dụng.
-Có thể vẽ before/after rất rõ: Sự khác biệt giữa việc "ước lượng bằng trực giác gây thiếu đồ/vừa thiếu vừa thừa" (Before) và "AI dự đoán chuẩn số lượng theo ngày giúp tối ưu khâu chuẩn bị" (After) thể hiện bằng số liệu cực kỳ trực quan.

Vì sao không chọn các bài khác:
-Education Assistant (Thủ tục nhập học & Điểm danh): Bài toán này thiên về xử lý quy trình hành chính và giải đáp thắc mắc (Q&A). Việc xây dựng một chatbot hay hệ thống quản lý thủ tục đòi hỏi phải can thiệp, kết nối sâu vào cơ sở dữ liệu nhân sự, phòng đào tạo và các quy định mật của trường; dữ liệu văn bản hành chính thường lộn xộn, khó chuẩn hóa cấu trúc để train model chuẩn trong thời gian ngắn.
-Education Support System (Học viên burnout/Sụt giảm phong độ): Mặc dù có impact rất nhân văn, nhưng "burnout" hay "sụt giảm phong độ" là trạng thái tâm lý mang tính chủ quan và cực kỳ khó định lượng. Dữ liệu hành vi trên LMS (tần suất đăng nhập, nộp muộn) chỉ là phần ngọn, không đủ để mô hình hóa chính xác tâm lý con người. Việc thiết lập các chỉ số đánh giá chất lượng (Quality Metric) cho giải pháp giảm burnout là quá mơ hồ và bất khả thi trong khuôn khổ một bài lab.

Canteen supply dùng mô hình AI dự đoán

# Quick validation
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Nguồn                | Số người | Tín hiệu xác nhận                  | Tín hiệu phản bác                  | Nhóm sửa problem thế nào           |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Quick interview      |    5     | 5/5 người xác nhận từng gap canh het mon    | Không có phản bác.                 | Giữ nguyên bài toán:               |
| (Bạn bè thân thiết)  |          | hoặc phải ăn mì gói vì xuống muộn  | Tất cả đều coi đây là nỗi đau      | Tập trung giải quyết việc thiếu hụt|
|                      |          | bị hết món sạch bách.              | lặp đi lặp lại hàng ngày.          | suất ăn vào cuối giờ cao điểm.     |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Mini poll            |    7     |  6/7 người thường xuyên đi ăn muộn  | 0/3 người nói đi ăn sớm (lúc       | Thu hẹp phạm vi:                   |
| (Những bạn ở gần)    |          | (sau 13h) gặp tình trạng hết món,  | 12h45) thì đồ ăn luôn đầy đủ,      | Bài toán không phải tối ưu cho cả  |
|                      |          | phải đợi nấu lại mất thời gian.    | không bị ảnh hưởng gì.             | buổi trưa, mà là dự đoán chính xác |
|                      |          |                                    |                                    | lượng đồ ăn cho nhóm đi muộn.      |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+


Insight sau validation:
Pain thật không nằm ở việc nhà ăn thiếu thốn thức ăn tổng thể. Pain nằm ở khâu phân phối và dự đoán dòng người theo thời gian thực, dẫn đến việc người đến sớm thì ê hề lựa chọn, còn người đến muộn (do vướng lịch học/lịch fix bug) thì phải chịu trận nhịn ăn hoặc mất thời gian chờ đợi vô lý.

# Research giải pháp:
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Nguồn                | Số người | Tín hiệu xác nhận                  | Tín hiệu phản bác                  | Nhóm sửa problem thế nào           |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Quick interview      |    5     | 5/5 người xác nhận từng gặp cảnh   | Không có phản bác.                 | Giữ nguyên bài toán:               |
| (Bạn bè thân thiết)  |          | hết món hoặc phải ăn mì gói vì     | Tất cả đều coi đây là nỗi đau      | Tập trung giải quyết việc thiếu hụt|
|                      |          | xuống muộn bị hết món sạch bách.   | lặp đi lặp lại hàng ngày.          | suất ăn vào cuối giờ cao điểm.     |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+
| Mini poll            |    3     | 3/3 người thường xuyên đi ăn muộn  | 0/3 người phản bác; tuy nhiên họ   | Thu hẹp phạm vi:                   |
| (Những bạn ở gần)    |          | (sau 13h) gặp tình trạng hết món,  | lưu ý nếu đi ăn sớm (trước 12h)    | Bài toán không phải tối ưu cho cả  |
|                      |          | phải đợi nấu lại mất thời gian.    | thì đồ ăn vẫn đầy đủ, không bị ảnh | buổi trưa, mà là dự đoán chính xác |
|                      |          |                                    | hưởng gì.                          | lượng đồ ăn cho nhóm đi muộn.      |
+----------------------+----------+------------------------------------+------------------------------------+------------------------------------+

Research takeaway:
Không nên ép học viên phải thay đổi hành vi bằng cách bắt buộc đặt trước món ăn (Non-AI/App thuần). Hướng hợp lý hơn là hệ thống chạy ngầm phía sau (Backend Workflow): tự động quét lịch học/lịch thi từ hệ thống, kết hợp dữ liệu lịch sử tiêu thụ qua mô hình dự đoán để xuất ra số lượng suất ăn khuyến nghị trên Dashboard cho đầu bếp trước 9h sáng mỗi ngày.

CURRENT STATE — 45 phút
+--------------------+     +--------------------+     +--------------------+     +--------------------+
| 1. Ước lượng suất  | --> | 2. Nấu ăn theo     | --> | 3. Học viên        | --> | 4. Đến muộn bị     |
|    ăn (5 phút)     |     |    ước lượng (20') |     |    xếp hàng (15')  |     |    hết món (5') [R]|
+--------------------+     +--------------------+     +--------------------+     +--------------------+
                                                                                            |
                                                                                            v
FUTURE STATE — 23 phút                                                                 [R] = Bottleneck
+--------------------+     +--------------------+     +--------------------+
| 1. AI dự đoán      | --> | 2. Đầu bếp review  | --> | 3. Nấu ăn theo     |
|    số lượng (1')   |     |    số lượng (2') [G|     |    AI đề xuất (20')|
+--------------------+     +--------------------+     +--------------------+
                                                               |
                                                               v
                                                      [G] = Human boundary
                                                      Fallback: AI lệch -> Nấu theo số cũ
