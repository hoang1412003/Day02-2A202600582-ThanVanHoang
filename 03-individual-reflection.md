
# 03 — Individual Reflection

## Đóng góp của Hoàng trong nhóm

| Hoạt động | Hoàng đã làm gì? | Kết quả |
|---|---|---|
| Scan cá nhân | Đưa ra 5 vấn đề | Team có nhiều lựa chọn để thảo luận |
| pitch | Pitch bài toán "V-app không đăng nhập được", chỉ rõ bằng chứng | Giúp nhóm định hình rõ một bài toán có Actor rõ ràng và Pain point có bằng chứng thực tế để làm bàn đạp so sánh |
| Challenge | Chất vấn bài toán Education Support về dữ liệu hành chính mật và tính định lượng của trạng thái Burnout |
| Validation | Làm google form để khảo sát | Giúp nhóm có cái nhìn tổng quan về mức độ phổ biến của bài toán |
| Rule / Workflow / Agent | Lập luận loại bỏ bài toán V-app | Nhóm thống nhất decision chọn Canteen Supply |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
|---|---|---|---|---|
| Gợi ý mở rộng các problem quan sát được theo các lăng kính | Giúp cấu trúc hóa 5 vấn đề rành mạch, gọi tên đúng "nỗi đau" của từng Actor | gợi ý quá rộng | Bỏ các ý không có workflow thật |
| Workflow | Nhờ AI phát họa các bước phân loại lỗi tự động giữa AI và Coach | Liệt kê nhanh luồng dữ liệu từ khi học viên gửi code lỗi đến khi AI đưa ra phản hồi nháp | AI thiết kế luồng tự động hóa 100%: AI tự sửa code và trả kết quả thẳng cho học viên, bỏ qua vai trò giám sát của Coach | Thêm bước Coach review thông tin tóm tắt làm ranh giới con người, biến AI thành màng lọc vòng ngoài và xây dựng cơ chế Escalate/Fallback chuyển thẳng cho Coach nếu gặp lỗi logic khó |
| Research | Tra cứu giải pháp kỹ thuật phù hợp để AI hiểu ngữ cảnh bài Lab và cấu trúc code | Gợi ý sử dụng mô hình LLM kết hợp prompt-engineering để đọc hiểu log lỗi và cú pháp code | Chỉ gợi ý cài chatbot Q&A thông thường, khiến AI phản hồi chung chung mà không hiểu học viên đang làm đến bước nào của bài Lab | Định hình lại giải pháp theo hướng AI Context-Aware: Kết hợp RAG để AI quét trước đề bài Lab và bộ test-case của trường trước khi phân tích lỗi của học viên |
| Problem Statement | Nhờ AI đóng vai Hội đồng để phản biện bộ tiêu chí | Chỉ ra bài toán V-app bị yếu ở khâu làm lab và bài Burnout quá mơ hồ | Đề xuất giải pháp Agent quá phức tạp để can thiệp sâu vào hệ thống V-app | Lập luận loại bỏ bài V-app, cùng team đồng thuận chọn Canteen Supply để tối ưu vận hành |

## Bài học của Hoàng

- Problem tốt là problem có bằng chứng thực tế: Một nỗi đau có số liệu cụ thể luôn thuyết phục hơn các ý tưởng đao to búa lớn nhưng mang tính chủ quan, khó định lượng
- AI đưa ra những workflow rất tốt để tham khảo

Nếu làm lại: 
- Tôi sẽ không hỏi 1 cách mơ hồ để AI đưa ra các ý tưởng quá rộng, thay vào đó tôi sẽ hỏi AI 1 câu cụ thể hơn