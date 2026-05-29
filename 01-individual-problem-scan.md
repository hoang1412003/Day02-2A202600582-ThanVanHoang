## Phase 1: Individual Problem Scan
| # | Lăng kính | Problem quan sát được | Ai đang đau? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Lỗi V app không đăng nhập được | học viên | Học viên mất từ 10 - 15 phút loay hoay đầu giờ học chỉ để đăng nhập, làm trễ tiến độ giảng dạy | 
| 2 | Cạnh tranh | AI phát triển nhiều doanh nghiệp ít tuyển intern, fresher  | Sinh viên mới tốt nghiệp | Các tuyển dụng thực tập sinh giảm đáng kể |
| 3 | Mơ hồ | Hướng dẫn làm lab day 01 chưa ổn | Học viên | làm sai workflow |
| 4 | Delay | Khi làm bài tập lab các anh coach không kịp hỗ trợ kịp thời cho toàn bạn | học viên | các bạn phải chờ đợi để được hướng dẫn |
| 5 | Phân tán | Thông tin học tập, bài tập và thông báo bị chia nhỏ và rải rác trên quá nhiều nền tảng | Học viên | Sinh viên phải mở và kiểm tra liên tục nhiều ứng dụng khác nhau mỗi ngày |

## Top 3: 

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Khi làm bài tập lab các anh coach không kịp hỗ trợ kịp thời cho toàn bạn | Diễn ra liên tục trong mọi buổi thực hành | AI có hiểu được các bug "độc lạ" do học viên tự viết code sai logic phức tạp không, hay chỉ sửa được lỗi cú pháp |
| 2 | Thông tin học tập, bài tập và thông báo bị chia nhỏ và rải rác trên quá nhiều nền tảng | Sinh viên phải mở và kiểm tra liên tục nhiều ứng dụng khác nhau mỗi ngày | Rủi ro rò rỉ dữ liệu hoặc vi phạm quyền riêng tư khi AI quét tin nhắn trong group |
| 3 | Hướng dẫn làm lab day 01 chưa ổn | Đánh trúng tâm lý của học viên mới | Mất bao lâu để chuẩn hóa dữ liệu đầu vào để AI đọc không bị nhầm lẫn |

## Problem Card #1 — Weekly Report

Problem 1 câu: Học viên làm bài tập Lab gặp bug phải chờ trung bình 15-20 phút mới đến lượt Coach hỗ trợ, làm lãng phí thời gian thực hành và gây quá tải hệ thống hỗ trợ.

**Actor:**
 Học viên tại các lớp học công nghệ và Đội ngũ Lab Coach.

**Thời điểm / bối cảnh:** 
Trong các buổi thực hành Lab , đặc biệt vào khung giờ cao điểm khi cả lớp cùng code và nộp bài.

**Current workflow:**
1. Học viên làm bài tập Lab theo tài liệu hướng dẫn
2. Gặp lỗi bug hoặc kẹt logic code
3. Học viên giơ tay
4. Học viên ngồi xếp hàng chờ đợi, không thể code tiếp các phần sau
5. Lab Coach rà soát thủ công danh sách câu hỏi theo thứ tự
6. Coach đến trực tiếp hoặc chat để debug, giải thích lỗi cho từng bạn
7. Học viên hiểu vấn đề và cập nhật lại bài làm

**Bottleneck:** 
Bước 4 & Bước 5 — Học viên phải chờ đợi lâu do tỷ lệ học viên nhiều, Coach mất quá nhiều thời gian để phân loại lỗi thủ công và sửa đi sửa lại các lỗi cấu hình cơ bản giống nhau.

**Impact:** 
Học viên mất trung bình 15-20 phút ngồi chờ vô ích/mỗi lần kẹt bug

**Success metric:** 
Rút ngắn thời gian chờ phản hồi ban đầu của học viên từ 15-20 phút xuống dưới 3 phút. Giảm tỷ lệ câu hỏi lặp lại đổ về phía Coach xuống dưới 20%, không tăng tỷ lệ định hướng sai cho học viên.

**Non-AI alternative:** 
Tạo tài liệu FAQ  cố định hoặc tuyển thêm Coach. Tuy nhiên, học viên thường lười đọc FAQ dài khi đang cuống, còn tuyển thêm Coach thì làm tăng mạnh chi phí vận hành lớp học.

**AI hypothesis:** 
AI đóng vai trò làm màng lọc vòng ngoài. AI tự động đọc log lỗi, giải thích và gợi ý hướng sửa nhanh cho học viên đối với các lỗi basic. PM/Coach chỉ nhảy vào duyệt và xử lý các ca khó.

Quick gut: Workflow.

### Draft current workflow

CURRENT STATE — 120 phút (Buổi Lab)

[1 Học viên code bài Lab: 40']
→ [2 Gặp bug/Kẹt logic: 5']
→ [3 Gửi câu hỏi/Kêu cứu: 5']
→ [4 XẾP HÀNG CHỜ COACH: 20']  <-- bottleneck
→ [5 Coach tiếp nhận & debug thủ công: 15']
→ [6 Học viên sửa code & đi tiếp: 35']

### Draft future workflow

FUTURE STATE — 120 phút (Tối ưu số task hoàn thành)

[1 Học viên code bài Lab: 40']
→ [2 Gặp bug ➔ Gửi code/log vào AI: 1']
→ [3 AI tự động phân tích & phân loại: 10 giây]
      ├──> (Lỗi Basic) ──> AI draft hướng dẫn sửa: 1' ──> Học viên tự sửa & code tiếp
      └──> (Lỗi Logic khó) ──> AI tóm tắt ngữ cảnh ──> Chuyển tiếp (Escalate) cho Coach
→ [4 Coach review thông tin tóm tắt từ AI: 2']
→ [5 Coach phê duyệt định hướng & support sâu: 10']  <-- human boundary (HITL)
→ [6 Học viên cập nhật bài làm: 66'] (Tăng tối đa thời gian thực hành thực tế)

Fallback: AI định hướng sai hoặc không hiểu bug ➔ Chuyển thẳng về luồng chờ Coach xử lý thủ công.

## Problem Cards #2

**Problem 1 câu:** 
Sinh viên phải kiểm tra thủ công 4 nền tảng (Discord, Teams, Zalo, Email) mỗi ngày để gom thông báo, dẫn đến mất thời gian và dễ bỏ sót deadline quan trọng.

**Actor:** 
Sinh viên (đặc biệt là Ban cán sự lớp hoặc Trưởng nhóm chịu trách nhiệm điều phối công việc).

**Thời điểm / bối cảnh:** 
Diễn ra hằng ngày trong suốt học kỳ, đỉnh điểm là vào giai đoạn chạy Deadline bài tập lớn hoặc các kỳ thi.

**Current workflow:**
1. Giảng viên/BTC đăng thông báo rải rác (Email gửi lịch, Discord giao bài, Zalo nhắc bài nhóm)
2. Sinh viên chủ động mở thủ công lần lượt từng ứng dụng nhiều lần trong ngày
3. Lướt qua các luồng thảo luận (chat) để tìm tin nhắn bị trôi hoặc tag @All
4. Tự ghi nhớ, chụp màn hình hoặc note thủ công các deadline vào tập/app cá nhân
5. Chia sẻ lại cho các thành viên trong nhóm (nếu làm bài tập nhóm)
6. Theo dõi sát sao để không bị trễ hạn nộp bài

**Bottleneck:**
 Bước 2 & Bước 3 — Việc kiểm tra thủ công trên quá nhiều app đóng vai trò như các "Information Silos" (ốc đảo thông tin), tin nhắn quan trọng dễ dàng bị vùi lấp bởi các cuộc trò chuyện bên lề.

**Impact:**
 Sinh viên tiêu tốn từ 15-20 phút/ngày chỉ để quản lý và sàng lọc thông báo. Tỷ lệ cập nhật thông tin khẩn cấp bị chậm từ 4-5 tiếng, dẫn đến ít nhất 1-2 lần sót deadline hoặc đi sai phòng học trong mỗi học kỳ.

**Success metric:**
 Rút ngắn số lượng nền tảng cần kiểm tra hằng ngày từ 4 xuống còn 1 nguồn tập trung duy nhất. Tỷ lệ bỏ lỡ thông báo quan trọng hoặc muộn deadline do trôi tin giảm về 0%.

**Non-AI alternative:**
 Đặt quy định ép buộc giảng viên/BTC chỉ dùng duy nhất 1 kênh. Tuy nhiên phương án này bất khả thi vì mỗi nền tảng có một thế mạnh riêng (Teams để học online, Email để gửi thông báo chính thức, Zalo/Discord để thảo luận nhanh).

**AI hypothesis:** 
Hệ thống Automation (Webhook/API) tự động cào dữ liệu thô từ các nguồn về. AI đóng vai trò làm bộ lọc thông minh: đọc hiểu ngữ cảnh, phân loại (đâu là tin nhảm, đâu là deadline), tóm tắt ngắn gọn thành một "Bản tin sáng" và tự động đồng bộ ngày hạn vào Google Calendar/Notion.

**Quick gut:** 
Workflow.

### Draft current workflow

CURRENT STATE — 20 phút/ngày (Rải rác liên tục)

[1 Có thông báo mới ở 4 app: 1']
→ [2 Mở Discord check tin nhắn trôi: 5']
→ [3 Mở Teams check lịch học: 4']
→ [4 Mở Zalo lướt group chat tìm deadline: 5']  <-- bottleneck
→ [5 Mở Email đọc thông báo dài của trường: 4']
→ [6 Tự note lại deadline vào lịch cá nhân: 1']

### Draft future workflow

FUTURE STATE — 2 phút/ngày (Tập trung)

[1 Thông báo mới kích hoạt Webhook/API: 0']
→ [2 AI cào dữ liệu, lọc nhiễu & phân loại: 10 giây]
→ [3 AI draft bản tin tóm tắt + trích xuất Deadline: 10 giây]
→ [4 Ban cán sự / Người dùng review nhanh bản tin: 1'30"]  <-- human boundary (HITL)
      ├──> (AI tóm tắt chuẩn) ──> Duyệt đẩy lên Hub tập trung + Tự động sync Calendar
      └──> (AI quét sai/thiếu) ──> Điều chỉnh thủ công bằng tay trước khi publish
→ [5 Sinh viên chỉ cần đọc 1 Hub duy nhất vào đầu ngày: 20 giây]

Fallback: Group chat bảo mật không cho cào API ➔ Người dùng chụp màn hình paste vào AI để nó tự bóc tách lịch.

## Problem Cards #3

**Problem 1 câu:** 
Tài liệu hướng dẫn Lab Day 01 viết mơ hồ và chứa code mẫu lỗi thời khiến hơn 50% học viên mới bị kẹt ở bước setup môi trường, lãng phí 45 phút đầu giờ loay hoay sửa lỗi.

**Actor:** 
Học viên mới (Intern/Fresher) chưa có nhiều kinh nghiệm tự xử lý xung đột môi trường hệ điều hành.

**Thời điểm / bối cảnh:**
Đầu buổi học thực hành của Day 01, giai đoạn cài đặt công cụ và cấu hình dự án mẫu.

**Current workflow:**

1. Học viên mở file hướng dẫn Lab Day 01 (Readme/Markdown) trên kho lưu trữ bài tập
2. Đọc và copy-paste các câu lệnh cấu hình môi trường, cài đặt thư viện theo tài liệu
3. Hệ thống báo lỗi build đỏ màn hình do tài liệu thiếu bước hoặc thư viện bị xung đột phiên bản
4. Học viên loay hoay tự tìm cách sửa trên Google/StackOverflow hoặc thử sửa mò câu lệnh
5. Khi không tự fix được, học viên nhắn tin hỏi bạn xung quanh hoặc bật kênh hỗ trợ kêu cứu Coach
6. Chờ đợi Coach đến tận nơi teamview/remote sửa hộ file cấu hình
7. Setup xong môi trường và bắt đầu vào làm bài tập logic chính

**Bottleneck:**
Bước 3 & Bước 4 — Tài liệu hướng dẫn thiếu tính tường minh (Ambiguity), không cập nhật theo môi trường thực tế và thiếu một cẩm nang tự sửa lỗi (Troubleshooting Guide) chuẩn hóa đi kèm.

**Impact:**
Hơn 50% học viên trong lớp bị nghẽn ngay từ "vòng gửi xe", lãng phí từ 45-60 phút đầu giờ chỉ để setup. Thời gian làm bài tập logic bị bóp nghẹt, dẫn đến tỷ lệ hoàn thành bài Lab ngay tại lớp giảm xuống dưới 40%.

**Success metric:** 
Rút ngắn thời gian vượt qua bước cấu hình môi trường ban đầu xuống dưới 10 phút. Đẩy tỷ lệ học viên hoàn thành trọn vẹn bài Lab ngay tại lớp lên trên 85%.

**Non-AI alternative:** 
Viết lại và cập nhật tài liệu thủ công liên tục. Tuy nhiên phương án này tốn rất nhiều não lực của Content Team/Coach khi môi trường (Windows/Mac/Linux, phiên bản Node, Java, Docker...) của mỗi học viên là hoàn toàn khác nhau.

**AI hypothesis:** 
Sử dụng kiến trúc RAG (Retrieval-Augmented Generation) kết nối trực tiếp với kho dữ liệu bài Lab và các case study sửa lỗi thực tế. Khi học viên gặp lỗi, AI sẽ đối chiếu log lỗi với tài liệu để sinh ra câu lệnh giải quyết động (Dynamic Troubleshooting) chuẩn xác theo đúng hệ điều hành của học viên đó.

**Quick gut:** 
Workflow.

### Draft current workflow

CURRENT STATE — 45 phút loay hoay đầu giờ

[1 Mở tài liệu Lab Day 01: 2']
→ [2 Đọc và copy code mẫu chung chung: 3']
→ [3 Terminal báo lỗi Build fail đỏ lòm: 1']
→ [4 Tự tra Google, loay hoay thử sửa file config: 20']  <-- bottleneck
→ [5 Gọi Coach và ngồi đợi Coach qua fix hộ: 15']
→ [6 Môi trường chạy được, bắt đầu code bài chính: 4']

### Draft future workflow

FUTURE STATE — 7 phút mượt mà

[1 Mở tài liệu Lab ➔ Phát hiện bước cấu hình mơ hồ / Bị lỗi build: 1']
→ [2 Paste log lỗi hoặc gõ câu hỏi vào ô Chatbot RAG kế bên tài liệu: 10 giây]
→ [3 AI RAG đối chiếu dữ liệu gốc, phân tích lỗi và sinh hướng dẫn động: 20 giây]
→ [4 Học viên review giải pháp và tự áp dụng theo hướng dẫn của AI: 5']  <-- human boundary
      ├──> (AI hướng dẫn chuẩn) ──> Fix lỗi thành công ➔ Đi tiếp vào bài code chính
      └──> (Lỗi độc lạ AI chịu) ──> Kích hoạt Fallback chuyển thẳng case cho Coach
→ [5 Học viên vượt qua bước setup, bắt đầu code bài chính: 30 giây]

Fallback: Khi dữ liệu đầu vào chưa được chuẩn hóa hoặc AI sinh lỗi lạ, hệ thống tự động ghi nhận log lỗi này, chuyển cho Coach xử lý và nạp ngược lại vào cơ sở dữ liệu RAG (HITL) để AI thông minh hơn ở các Day Lab sau.

