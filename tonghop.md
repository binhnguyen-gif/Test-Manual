# Tóm Tắt Nội Dung Chia Sẻ Từ File 1.md

## Bài Học Từ Lần Vấp Đầu Tiên (Day 1/100)

### Vấn Đề Ban Đầu
- **Sai Lầm Của Tester Mới**: Chỉ test theo thao tác trên UI (chọn sản phẩm → thêm vào giỏ → thanh toán), không kiểm tra các quy trình backend như gửi email xác nhận.
- **Hậu Quả**: Sau khi release, khách hàng phàn nàn vì thiếu email xác nhận đơn hàng. Tester không biết hệ thống có chức năng này vì không hỏi PO, BA hay Dev.

### Bài Học Rút Ra
- **Test Không Phải Chỉ "Click Cho Xong"**: Cần hiểu toàn bộ hệ thống và luồng nghiệp vụ, không chỉ dựa vào giao diện người dùng.
- **Thiếu Hiểu Biết Dẫn Đến Bỏ Sót**: Không hiểu luồng xử lý hoàn chỉnh → dễ bỏ qua các bước quan trọng "phía sau màn hình".
- **Không Xác Định Đầu Ra Cần Kiểm Chứng**: Tester chỉ là người "click" chứ không phải người "kiểm thử" thực sự.

### Cách Thay Đổi
- **Đọc Hiểu Yêu Cầu Kỹ Lưỡng**: Luôn bắt đầu bằng việc nghiên cứu tài liệu và hỏi han (PO, BA, Dev): "Tính năng này sau khi thực hiện xong thì hệ thống còn làm gì nữa không?"
- **Vẽ Luồng Xử Lý**: Tự vẽ flow từ đầu đến cuối, bao gồm cả backend không thấy được, để kiểm thử trọn vẹn.
- **Test Theo Mục Tiêu**: Không chỉ theo thao tác, mà hỏi: "Điều gì chứng minh được chức năng này hoạt động đúng?"

### Kết Quả Sau Khi Thay Đổi (Sau Khoảng 20 Ngày)
- ✅ Giảm rõ rệt tình huống thiếu kiểm thử backend.
- ✅ Được QA Lead tin tưởng giao nhiệm vụ phức tạp hơn.
- ✅ Dev phản hồi: Bug logic giảm đáng kể.

### Kết Luận
- **Kiểm Thử Là Bảo Vệ Chất Lượng**: Dựa trên hiểu biết, sự chủ động và tư duy hệ thống.
- **Lời Khuyên**: Không bao giờ test mà không hiểu rõ mình đang test cái gì và tại sao nó cần được test.
- **Câu Hỏi Phản Ánh**: Lần cuối cùng bạn hỏi: "Tính năng này sau khi chạy xong thì hệ thống còn làm gì nữa?" là khi nào?

*Trình bày dưới dạng bullet points và headings để dễ đọc và hiểu.*

## Bài Học Về Viết Test Case (Day 2/100)

### Vấn Đề Với Test Case Thiếu Context
- **Test Case Vô Dụng**: Viết đủ 50 test case nhưng không có context, dẫn đến không đọc nổi sau sprint sau, junior test sai flow, dev hỏi expected result.
- **Thiếu Context Nghĩa Là**:
  - Không nói rõ trạng thái hệ thống trước khi test.
  - Không có dữ liệu cụ thể để chạy test.
  - Không rõ kết quả mong đợi.
  - Không có mục tiêu kiểm thử.

### Ví Dụ Cá Nhân
- **Test Case Cho Đăng Ký Tài Khoản**: Checklist đầy đủ nhưng không mang lại giá trị cho team.
- **Vấn Đề Phát Sinh**:
  - Regression phải test lại từ đầu vì không hiểu.
  - QA mới test sai logic.
  - Không có dữ liệu để so sánh đúng/sai khi dev fix bug.

### Cách Thay Đổi
- **Tự Hỏi Trước Mỗi Test Case**:
  - Người test cần biết gì để xác định đúng/sai?
  - Nếu không ở đây, người khác có test được không?
  - Có thể dùng lại sau 3 tháng không?
- **Viết Test Case Theo Hướng**:
  - Điều kiện đầu vào rõ ràng.
  - Expected chi tiết.
  - Dữ liệu test minh họa.
  - Notes nếu bước nào dễ gây hiểu nhầm.

### Kết Quả Sau Khi Thay Đổi
- ✅ Junior tester test đúng ngay từ lần đầu.
- ✅ Dev đọc hiểu logic mà không cần QA giải thích.
- ✅ Regression tiết kiệm thời gian, dùng lại gần như nguyên trạng.
- ✅ Tester bớt stress vì không phải vác lại đống rối rắm mỗi sprint.

### Kết Luận
- **Test Case Là Tài Sản Chất Lượng**: Không phải để đánh dấu "Đã test", mà để dẫn đường, bảo vệ và giữ hệ thống ổn định lâu dài.
- **Câu Hỏi Phản Ánh**: Nếu bạn nghỉ phép một tuần – Test case bạn viết có giúp người khác test tiếp được không?

## Bài Học Về Log Bug (Day 3/100)

### Vấn Đề Với Bug Bị Từ Chối
- **Bug Rõ Ràng Nhưng Bị Từ Chối**: Log bug kỹ nhưng dev trả lời "Not a bug", PM im lặng, bug bị close.
- **Ví Dụ Cá Nhân**: Log bug giao diện không hiển thị lỗi khi input sai định dạng, nhưng dev từ chối vì không bắt buộc validate theo specs, dẫn đến khách gặp lỗi thật sau.

### 3 Lỗi Phổ Biến Khiến Bug Bị Từ Chối
- **❌ Lỗi 1: Log Theo Cảm Tính – Không Có Tiêu Chí Rõ Ràng**
  - Ví dụ: "Tooltip hiển thị sai vị trí" mà không nói sai thế nào, không dẫn guideline, không có screenshot, không ghi browser/device.
  - Kết quả: Bug bị close, khách complain sau.
  - Cách khắc phục: Ghi rõ vị trí sai, dẫn guideline (e.g., file Figma), screenshot, browser/device.

- **❌ Lỗi 2: Không Đính Kèm Bằng Chứng – Không Dẫn Được Flow Tái Hiện**
  - Ví dụ: "Form crash khi nhập số âm" mà dev không tái hiện được.
  - Thiếu: Dữ liệu nhập, hệ điều hành, bước cụ thể.
  - Cách khắc phục: Ghi rõ version, đính kèm JSON test data, video quay thao tác.

- **❌ Lỗi 3: Không Link Bug Với Requirement – Dev Có Quyền Từ Chối**
  - Ví dụ: "Không hiển thị cảnh báo khi nhập sai định dạng email" mà specs không ghi bắt buộc.
  - Kết quả: Dev nói code đúng theo mô tả, bug biến mất.
  - Cách khắc phục: Check specs + flow, ghi requirement liên quan, tiêu chí validate.

### Bài Học Xương Máu
- **Bug Đúng Nhưng Log Sai → Thua**: Không đủ logic, bằng chứng, gắn requirement → bị từ chối hoặc bị xem không hiểu nghiệp vụ.

### Checklist "Log Bug Sống Sót Qua Mọi Vòng"
- ✅ Mô tả rõ hành vi sai vs hành vi đúng.
- ✅ Ghi rõ môi trường, browser, OS, version.
- ✅ Có screenshot/video.
- ✅ Đính data test nếu cần.
- ✅ Gắn với specs hoặc guideline cụ thể.
- ✅ Ghi chú nguồn tham chiếu (file thiết kế, ticket, doc...).

### Kết Luận
- **Tester Giỏi Là Người Log Bug Mà Cả Team Phải Gật Đầu**: Test không chỉ là tìm bug.
- **Câu Hỏi Phản Ánh**: Bạn đã từng log 1 bug rõ mười mươi mà vẫn bị từ chối chưa? (Comment chia sẻ tình huống để viết checklist cho bug "nhạy cảm").

## Bài Học Về Test Khi Không Có Tài Liệu (Day 4/100)

### Vấn Đề Khi Không Có Tài Liệu
- **Test Theo Những Gì Có**: Không sai, nhưng nếu không tự dựng bối cảnh, lỗi lọt qua vẫn tính về QA, team lệ thuộc cảm tính, đứng mũi chịu sào khi demo vỡ.

### 3 Kỹ Năng Giúp Tester Sống Sót
- **1. Vẽ Lại Luồng Người Dùng – Đừng Để UI Dắt Mũi**
  - **Dùng Khi**: Chỉ có giao diện, không flow, không document.
  - **❌ Sai**: Test từng màn hình rời rạc, report lỗi UI bỏ sót logic nghiệp vụ, không biết flow đúng sai.
  - **✅ Đúng**: Vẽ hành trình người dùng từ UI, xác định điểm bắt đầu/kết thúc, so sánh hệ thống cũ hoặc hỏi dev: "Luồng này xử lý xong thì hệ thống làm gì?"
  - **Ví Dụ**: Tính năng "đặt hàng" không có bước xác nhận → vẽ flow, hỏi dev → phát hiện thiếu logic check tồn kho → chặn bug nặng trước demo.

- **2. Tự Viết Đặc Tả Tạm Thời – Không Tài Liệu, Thì Tạo Tài Liệu**
  - **Dùng Khi**: Không có SRS, không có người giải thích, chỉ còn Jira.
  - **❌ Sai**: Test theo trí nhớ, không ghi chú → regression khổ, không confirm dev/PO.
  - **✅ Đúng**: Viết tiêu chí chấp nhận dựa trên UI & hiểu hệ thống, gửi recap: "Theo hiểu của em, flow đúng là A → B → C → xác nhận → tạo đơn. Đúng không anh/chị?", gắn vào bug/task.
  - **Ví Dụ**: Viết "mini spec" 4 dòng → PO reply chuẩn, cả team dùng cho regression.

- **3. Hỏi Đúng Người – Hỏi Đúng Lúc – Hỏi Đúng Thứ**
  - **Dùng Khi**: Loay hoay không biết hỏi ai để hiểu rõ hơn.
  - **❌ Sai**: Hỏi tất cả → loãng, hỏi quá muộn → trễ, hỏi sai thứ (hỏi PO về code, dev về KPI).
  - **✅ Đúng**: Hỏi PO về nghiệp vụ: "Luồng này nếu người dùng bỏ giữa chừng thì sao?", hỏi dev về xử lý: "Tạo đơn xong thì backend ghi nhận thế nào?", hỏi chính mình: "Nếu mình là khách hàng, mình có hiểu và làm được không?"
  - **Ví Dụ**: Hỏi PO: "Nếu người dùng đăng ký rồi thoát giữa chừng thì dữ liệu lưu đến đâu?" → phát hiện hệ thống không xử lý → bug logic lớn.

### Tổng Kết
- **Không Có BA Không Phải Lý Do Test Hời Hợt**: Tester giỏi dựng bối cảnh từ ít ỏi nhất, giữ chất lượng.
- **Câu Hỏi Phản Ánh**: Bạn từng test dự án không tài liệu chưa? Comment 1 cách "tự cứu mình" – biết đâu kinh nghiệm xịn cho QA khác.

## Bài Học Về Log Bug Bị Từ Chối (Day 5/100)

### Vấn Đề Với Bug Bị Từ Chối
- **Bug Rõ Ràng Nhưng Bị Từ Chối**: Log đầy đủ bước tái hiện, mô tả lỗi, screenshot, nhưng dev từ chối: "Cái này là design như vậy mà."
- **Thiếu Bằng Chứng**: Mở file thiết kế không có chi tiết cụ thể, hỏi BA/PO cũng mơ hồ, bug bị close dù logic hợp lý.

### Bài Học Rút Ra
- **Log Theo Cảm Tính**: Từng nghĩ dev cãi cố, nhưng nhận ra log bug theo cảm tính, không có expected result cụ thể để đối chiếu.

### Cách Thay Đổi
- ✅ Đính luôn ảnh thiết kế.
- ✅ Ghi rõ expected + lý do.
- ✅ Nếu bug logic, link specs/ticket.
- ✅ Test đa môi trường – có video nếu cần.

### Kết Quả
- **Không Còn Bị Từ Chối**: Vì bằng chứng rõ rành rành, không ai nói "nó không sai".

### Kết Luận
- **Bug Đúng Chưa Đủ**: Phải log đúng – và log đủ – thì mới thuyết phục cả team.
- **Câu Hỏi Phản Ánh**: Bạn từng log bug mà bị dev từ chối chưa?

## Bài Học Về Test Quá Cẩn Thận (Day 6/100)

### Vấn Đề: Một Cú Click Làm Môi Trường Đi Xa
- **Test Tính Năng "Xóa Người Dùng"**: Test kỹ các trường hợp bình thường, nhưng nghĩ "Nếu user là admin thì sao?" và "Nếu tự xóa chính mình thì sao?"
- **Hậu Quả**: Click xóa admin → màn hình đen, bị văng khỏi hệ thống, môi trường staging không truy cập được, Slack dev bùng nổ, mất quyền quản trị.

### Bài Học Rút Ra
- **Quá Đà Với "Test Toàn Diện"**: Test mọi góc nhưng không cân nhắc rủi ro, dẫn đến tạo bug gãy hệ thống.

### Cách Thay Đổi
- **Checklist Trước Khi Test Hành Vi "Nhạy Cảm"**:
  - ❓ Đây có phải hành động thay đổi dữ liệu thật không?
  - ⚠️ Có đang test ở môi trường an toàn để thử sai?
  - 👥 Cần hỏi dev/PM xác nhận không?
  - 🧍‍♂️ Có thể dùng account clone thay vì tài khoản chính thức?
- **Viết Test Case Rõ Ràng Cho Tình Huống "Phá"**:
  - Ghi chú rõ nguy cơ.
  - Nêu tài khoản, môi trường cụ thể.
  - Cảnh báo tester khác nếu có thể gây ảnh hưởng thật.

### Kết Luận
- **Test Là Tìm Bug, Không Phải Tạo Bug**: Tester giỏi không chỉ test kỹ, mà còn test có giới hạn – biết khi nào nên hỏi và khi nào nên dừng lại.