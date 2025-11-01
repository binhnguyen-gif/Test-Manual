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

## Bài Học Về Test Giá Trị, Không Chỉ Pass/Fail (Day 7/100)

### Vấn Đề: Test Pass Nhưng Tính Năng Vô Nghĩa
- **Test Tính Năng Bộ Lọc Tìm Đơn Theo Loại Dịch Vụ**: UI có, rule rõ, dữ liệu ngon, test kỹ từng dòng, ghi "Passed", team release.
- **Hậu Quả**: Chẳng ai dùng bộ lọc, PO hỏi: "Dev mất 2 ngày làm, test pass nhưng vô nghĩa."

### Bài Học Rút Ra
- **Chỉ Test Logic Đúng/Sai**: Chưa hỏi: "Logic đúng rồi… nhưng có ai dùng không?"
- **Test "Kết Quả" Nhưng Chưa Test "Giá Trị"**: Tính năng làm ra không ai dùng → dù pass, vẫn là code thừa.
- **Bỏ Sót Câu Hỏi**: Người dùng có thấy nó? Hiểu cách dùng? Có tracking? Nếu dùng ít, lý do từ đâu?

### Cách Thay Đổi
- **Thêm Vào Checklist**: Có tracking chưa? Có gắn chỉ số đo lường chưa?
- **Hỏi PO**: Mình cần người dùng dùng tính năng này bao nhiêu phần trăm?
- **Gợi Ý Dev**: Log event click/filter → kiểm tra sau 1 tuần.
- **Thêm Lớp Test Case Mới**: Tính năng có hiện đúng context không? (Context = bối cảnh sử dụng, xuất hiện đúng lúc – đúng chỗ không?)

### Kết Quả
- **Không Test Dư**: Test đúng thứ khách hàng muốn thấy.
- **PO Chủ Động Hỏi Về Đo Lường**: Dev đỡ nghe "làm mà chẳng ai dùng".
- **Tester Không Cảm Giác "Test Xong Mà Chẳng Để Làm Gì"**.

### Kết Luận
- **Câu Hỏi Phản Ánh**: Bạn có từng test một tính năng thật kỹ, test pass 100%… rồi thấy nó "chết lâm sàng" không?
- **Lời Khuyên**: Hãy nhớ test cả phần vô hình: Phần người ta cảm nhận được giá trị – chứ không chỉ pass-fail.
- **Checklist "Test Giá Trị & Đo Hiệu Quả"**: Comment "CHECK VALUE" để nhận bản checklist thật từng dùng.

## Bài Học Về Test Pass Vẫn Toang (Day 8/100)

### Vấn Đề: Chỉ Thấy Một Field, Không Thấy Cả Hệ Thống
- **Test Tính Năng Chỉnh Sửa Số Điện Thoại**: Test xong, ghi "Passed", team push lên môi trường thật.
- **Hậu Quả**: Ba ngày sau, hệ thống nghiêng ngả – call center gọi sai khách, đơn hàng giao nhầm, báo cáo thống kê sai, CRM không gửi mã giảm giá.
- **Ví Dụ Thực Tế**: Giống vụ đổi đầu số nhà mạng Việt Nam từ 11 số sang 10 số – hệ thống không chuẩn hóa, không mapping, dữ liệu tách biệt không đồng bộ.

### Bài Học Rút Ra
- **Bỏ Sót Câu Hỏi Quan Trọng**: "Dữ liệu này còn xuất hiện ở đâu?", "Có hệ thống nào dùng nó như định danh không?", "Nếu sửa, có gây xung đột dữ liệu không?"
- **Tester Không Chỉ Test Màn Hình**: Cần test cả những gì di chuyển bên dưới.

### Checklist Kiểm Thử Ảnh Hưởng Hệ Thống
- ✅ Trường này có phải định danh không?
- ✅ Có module nào khác đang dùng field này?
- ✅ Có cần log history khi dữ liệu bị sửa?
- ✅ Có hệ thống nào cần đồng bộ không?

### Cách Thay Đổi
- **Test Và Trace**: Không chỉ test xong là xong, mà hỏi thêm, kiểm tra thêm để tránh toang lần hai vì một cái field tưởng vô hại.

### Kết Luận
- **Câu Hỏi Phản Ánh**: Bạn từng test tính năng nào tưởng nhỏ mà hậu quả lại… không nhỏ?

## Bài Học Về Test Hệ Thống Không Tài Liệu (Day 9/100)

### Vấn Đề: Hệ Thống Không Tài Liệu, Không Ai Chỉ
- **Tuần Đầu Vào Dự Án**: Hệ thống cũ từ thời tiền sử, không tài liệu, không ai từng test, dev bảo "test đại đi".
- **Khó Khăn**: Không biết dữ liệu chuẩn, xử lý ra sao, bắt đầu từ đâu, mỗi lần test cầu nguyện.

### Cách Thay Đổi: Không Hiểu Thì Mò Cho Hiểu
- **Không Hiểu API Trả Gì?**: Thử thao tác, so sánh dữ liệu hiển thị với API response.
- **Không Biết Đúng Sai?**: Dùng mẫu dữ liệu, nhập thử nhiều giá trị, ghi kết quả, xem cái nào được/từ chối.
- **Không Biết Rule Hệ Thống?**: Thử từng TH cụ thể, đối chiếu input-output, tìm điều kiện ngầm định.

### Ghi Chú Và Tạo Checklist
- **Ghi Chú Từng Điểm**: Nút A bấm hiển thị gì, form validate hay không, note tình huống mới.
- **Cuối Tuần**: Có checklist mô tả hành vi hệ thống.
- **Checklist Đơn Giản**:
  - ❓ Có validate khi nhập sai? → Thử nhập chuỗi, số âm, ký tự đặc biệt.
  - ❓ Sau khi bấm nút, điều gì xảy ra? → Theo dõi hiển thị dữ liệu mới.
  - ❓ Dữ liệu có trùng lặp không? → Thử thao tác 2 lần giống nhau.
  - ❓ Field này có bắt buộc không? → Để trống xem báo gì.
  - ❓ Có phản hồi từ hệ thống không? → Bật inspect, theo dõi response API/lỗi.

### Kết Quả
- **Hiểu Hệ Thống Tốt Hơn Dev Bảo Trì**: Checklist tránh quên case, team dùng cho regression.

### Kết Luận
- **Không Ai Sinh Ra Đã Biết Test Hệ Thống Mù Tịt**: Dám ngồi lại thử từng cái một, làm được nhiều.
- **Checklist Đầu Tay Không Cần Hoàn Hảo**: Miễn giúp không lặp lỗi.
- **Lời Khuyên**: Không hiểu thì hỏi. Không ai chỉ thì test. Không ai test thì tự viết ra.
- **Câu Hỏi Phản Ánh**: Nếu bạn cũng từng phải test hệ thống "mù tịt" như tôi – hãy để lại comment "Mò tới sáng".

## Bài Học Về Giới Hạn Môi Trường Test (Day 10/100)

### Vấn Đề: Test Pass Trên Dev Nhưng Prod Vẫn Lỗi
- **Dự Án Giáo Dục Trực Tuyến**: Chỉ có 2 môi trường Dev và Prod, không staging/UAT do giới hạn tài nguyên.
- **Test Module Báo Cáo Học Viên**: Test kỹ mọi logic trên Dev, pass, dữ liệu hiển thị mượt.
- **Hậu Quả**: Prod dựng xong, khách báo bộ lọc không load học viên mới. Dev ổn, Prod thiếu dữ liệu mới.

### Nguyên Nhân Phát Hiện
- **Prod Chưa Kích Hoạt Đồng Bộ Dữ Liệu Tự Động**: Dev có tác vụ đồng bộ định kỳ, Prod chưa bật.
- **Giới Hạn Bản Ghi Hiển Thị**: Prod cấu hình thấp hơn Dev.

### Bài Học Rút Ra
- **Dù Test Giỏi, Môi Trường Có Điểm Mù Tester Không Kiểm Soát Vẫn Toang**: Giới hạn môi trường dẫn đến lỗi.

### Cách Thay Đổi
- **Xây Dựng Checklist Go-Live Với Dev Lead và QA**:
  - Các tác vụ định kỳ chạy tự động đã được bật chưa?
  - Các tham số hệ thống có bị giới hạn khác Dev không?
  - Có chức năng nào yêu cầu cấp quyền riêng không?
  - Phân quyền/role có đồng nhất giữa các môi trường không?
  - Có tính năng, cấu hình nào yêu cầu can thiệp thủ công không? (Bật/tắt thủ công, nhập dữ liệu thủ công, điều chỉnh tham số đặc biệt...)
- **Quy Trình Go-Live**: Dev share màn hình, cùng đi qua checklist, capture bằng chứng, QA lưu log chứng minh.

### Kết Luận
- **Lỗi Không Do Tester Nhưng Không Thể Phủi Tay**: Nếu không góp phần cải thiện quy trình, vẫn bị hỏi đầu tiên khi hệ thống lỗi.
- **Câu Hỏi Phản Ánh**: Còn bạn thì sao? Đã từng rơi vào cảnh test pass mọi thứ, nhưng Prod vẫn gọi tên chưa? Comment chia sẻ để anh em không ai phải đi một mình.

## Bài Học Về Test Thông Điệp (Day 11/100)

### Vấn Đề: Không Bug Nhưng Vẫn Trượt Vì Message "Tưởng Rõ"
- **Test Hệ Thống Thu Thập Thông Tin Đăng Ký Sự Kiện**: Người dùng nhập thông tin → submit → nhận email xác nhận.
- **Test Kỹ**: Bỏ trống/lỗi, sai định dạng/lỗi, đúng định dạng/hiện message, gửi mail/nhận mail/pass.
- **Hậu Quả**: Demo, người dùng hỏi: "Nhập xong thấy báo 'Thông tin của bạn đã được ghi nhận' là xong rồi à? Có cần làm gì nữa không?" và "Tưởng đăng ký thành công rồi, ai ngờ không thấy mail gì cả. Chắc bị lỗi?"

### Bài Học Rút Ra
- **Message Đúng Nhưng Không Đủ**: Với tester hiểu hệ thống, nhưng người dùng không biết, cần chỉ đường rõ ràng chứ không phải "chúng tôi ghi nhận".
- **Sai Lầm**: Test logic, flow, UI chuẩn nhưng chưa test cảm nhận người dùng khi đọc thông điệp.

### Cách Thay Đổi
- **1. Test Thông Điệp – Không Chỉ Test Chức Năng**
  - ❌ "Thông tin của bạn đã được ghi nhận."
  - ✅ "Yêu cầu của bạn đã được ghi nhận. Vui lòng kiểm tra email để xác nhận và hoàn tất đăng ký."
- **2. Ngồi Lại Với BA/UI – Xem Mỗi Message Có Rõ Ý Không**
  - Test bằng người chưa từng dùng hệ thống để xem có hiểu lầm không.
- **3. Đưa UX Message Vào Checklist Kiểm Thử**
  - Vì một dòng không rõ ràng có thể làm đổ trải nghiệm.

### Kết Luận
- **Không Phải Lỗi Nào Cũng Nằm Ở Dòng Code**: Có lỗi trong suy nghĩ chủ quan "chừng này là đủ rồi."
- **Tester Không Chỉ Test Hệ Thống Chạy**: Còn phải giúp người dùng hiểu họ đang ở đâu trong hành trình.
- **Câu Hỏi Phản Ánh**: Bạn từng gặp tình huống message "tưởng rõ" mà làm người dùng hiểu sai chưa? Comment một dòng "TÔI ĐÃ GẶP" để thấy bạn không cô đơn.

## Bài Học Về Log Bug Mơ Hồ (Day 12/100)

### Vấn Đề: Viết Bug Không Sai Nhưng Dev Không Hiểu
- **Log Bug**: "Không hiển thị dữ liệu ở bảng danh sách khi chọn filter theo tháng 2."
- **Feedback Từ Dev**: "Bạn mô tả rõ hơn được không? Filter nào? Điều kiện gì? Có record mẫu không?"
- **Bài Học**: Log bug để người khác phải suy luận, không phải để fix được.

### Đặt Mình Vào Vai Dev
- Không biết màn nào (dự án nhiều module).
- Không rõ thao tác: đã chọn option nào, apply chưa?
- Không biết data test hay account cụ thể.

### Checklist "Bug Không Cần Phiên Dịch"
- **📍 Vị Trí Cụ Thể**: Màn nào? Module nào? Ví dụ: "Màn Danh sách học viên → Tab Học phí → Filter theo tháng."
- **🔄 Điều Kiện Tái Hiện**:
  - Dữ liệu test (ID, tên mẫu).
  - Các bước thao tác.
  - Điều kiện hệ thống (role, quyền…).
- **🧾 Kết Quả Mong Đợi & Thực Tế**:
  - Kỳ vọng: "Danh sách học viên có học phí trong tháng 2 hiển thị đầy đủ."
  - Thực tế: "Trống hoàn toàn, mặc dù có học viên đã đóng."
- **📎 Evidence Rõ Ràng**:
  - Screenshot.
  - Log (nếu có).
  - URL, account test cụ thể.

### Kết Luận
- **Log Bug Để Fix Được, Không Phải Trút Bực Bội**: Bug log tốt tiết kiệm 3 lần trao đổi – 2 lần fix sai – 1 lần hiểu lầm.
- **Câu Hỏi Phản Ánh**: Bạn từng log bug kiểu "mình hiểu là được" chưa? Comment 1 lần bạn bị Dev hỏi tới tấp – để chúng ta cùng rút kinh nghiệm từ vết sẹo của nhau.

## Bài Học Về Đánh Giá Ảnh Hưởng Bug (Day 13/100)

### Vấn Đề: Log Bug Tưởng Đủ Nhưng Hệ Thống Gãy Dây Chuyền
- **Log Bug Nhỏ**: Giao diện crash nếu trạng thái "Đã giao nhưng chưa thanh toán" – log chỉn chu, screenshot, bước tái hiện, dữ liệu test.
- **Dev Fix Trong 1 Ngày**: Test lại pass.
- **Hậu Quả**: Chiều hôm đó, dashboard không hiện doanh thu, mất sạch dữ liệu vì dùng chung logic lọc.

### Bài Học Rút Ra
- **Vấn Đề Không Nằm Ở Bug**: Mà ở chỗ không check hết phạm vi ảnh hưởng.
- **Tester Mới Join**: Nghĩ đánh giá impact là việc của Dev, chưa từng được dạy tester cũng cần đánh giá ảnh hưởng.

### Cách Thay Đổi
- **Đặt Câu Hỏi "Impact Ở Đâu?" Mỗi Khi Log Bug**.
- **Thêm Dòng Vào Mô tả Bug**: "🔍 Cần xác minh xem rule này có được dùng ở các màn khác như dashboard / báo cáo không."
- **Ngồi Lại Hỏi Dev**:
  - Rule này có dùng lại không?
  - Có màn nào gọi chung API?
  - Có ảnh hưởng đến logic flow khác?

### Kết Quả
- **Không Còn Bị Gọi Tên Vô Lý Vì Thiếu Impact**.
- **Hiểu Hệ Thống Nhanh Hơn**.
- **Trưởng Thành Hơn Như Một Tester Thực Thụ**.

### Kết Luận
- **Câu Hỏi Phản Ánh**: Nếu bạn từng log bug xong vẫn bị hỏi trách nhiệm, nhìn hệ thống gãy mà không biết mình đã bỏ sót gì – thì bạn không cô đơn đâu.
- **Comment Một Pha "Nghĩ Là Xong" Mà Hoá Ra Chưa**: Để người sau đỡ vướng lại như mình.

## Bài Học Về Viết Test Case Không Phân Biệt Ưu Tiên (Day 14/100)

### Vấn Đề: Viết Testcase Kỹ Từng Dòng Nhưng Test Lại Nhầm
- **Kế Thừa Bộ Testcase Cũ**: Đầy đủ nhưng không có cột Priority, không phân nhóm chức năng, không màu sắc phân biệt mức độ quan trọng.
- **Nghĩ**: "Test hết là chắc ăn", "Càng đầy đủ càng tốt", "Ở đâu cũng cần test 100%".
- **Hậu Quả**: Khi staging dựng xong, được yêu cầu test lại những case chính trong hôm nay. Mở file: 67 testcase, trình duyệt desktop/mobile trộn lẫn, luồng chính/phụ lẫn lộn, không đánh dấu, không nhóm, không định hướng → đứng hình, không biết bắt đầu từ đâu.

### Bài Học Rút Ra
- **Viết Đủ Testcase Không Có Nghĩa Là Test Hiệu Quả**.
- **Không Đánh Priority Là Tự Làm Khó Chính Mình Mỗi Lần Regression**.
- **Không Tư Duy Chiến Lược Là Cạn Sức Trước Khi Chạm Được Trọng Tâm**.

### Sau Này Biết
- **Có Những Thiết Bị Phụ → Có Thể Lùi**.
- **Có Những Trường Hợp Chỉ Xuất Hiện Ở Luồng Hiếm**.
- **Có Những Luồng Dù Test Pass Vẫn Không Phải Ưu Tiên Khi Lên Môi Trường Mới**.

### Cách Thay Đổi
- **Luôn Thêm**:
  - 🟢 Cột Priority (High – Medium – Low).
  - 🟦 Nhóm chức năng.
  - 🔶 Gợi ý môi trường/thiết bị ưu tiên kiểm thử.
- **Mỗi Lần Test Lại → Chỉ Cần Lọc Là Ra → Tiết Kiệm 70% Effort**.

### Kết Luận
- **Câu Hỏi Phản Ánh**: Còn bạn thì sao? Bạn từng ngợp khi test lại vì file testcase không phân rõ ưu tiên chưa? Chia sẻ để các bạn fresher khác đỡ rơi vào cảnh "test kỹ nhưng lạc đường".