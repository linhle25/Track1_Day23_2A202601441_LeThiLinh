# Product Metrics Lab

- **Họ và tên:** Lê Thị Linh
- **Mã học viên:** 2A202601441
- **Dự án chọn làm:** P-005 — Ứng dụng y tế tra cứu tương tác thuốc và cảnh báo sử dụng thuốc an toàn
- **Metrics Pack:** _[Dán link tệp đã cấp quyền xem]_

## 00 — Phạm vi

- **Dự án:** P-005 — Ứng dụng y tế tra cứu tương tác thuốc và cảnh báo sử dụng thuốc an toàn.
- **Persona:** Người bệnh đang sử dụng đồng thời nhiều loại thuốc, bao gồm thuốc kê đơn, thuốc không kê đơn và thực phẩm chức năng; đôi khi tự mua thêm sản phẩm mà không hỏi ý kiến bác sĩ hoặc dược sĩ.
- **Core job:** “Khi muốn dùng thêm một loại thuốc hoặc thực phẩm chức năng, tôi cần biết sản phẩm đó có tương tác với những thứ mình đang sử dụng hay không, để tránh sử dụng kết hợp không an toàn.”

## 01 — Core Action

### Phân biệt bốn khái niệm

| Khái niệm        | Câu trả lời                                                                                                                                                         |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Core job         | Biết một loại thuốc hoặc thực phẩm chức năng mới có tương tác với những sản phẩm đang sử dụng hay không để tránh kết hợp không an toàn.                             |
| Core action      | Hoàn tất kiểm tra thuốc hoặc thực phẩm chức năng dự định dùng thêm với danh sách sản phẩm đang sử dụng và mở xem kết quả.                                           |
| Core value       | Người bệnh biết nguy cơ tương tác, có thông tin để đưa ra quyết định sử dụng an toàn hơn và có thể gửi câu hỏi cho bác sĩ để bác sĩ giải đáp trường hợp ảnh hưởng . |
| Core value event | `interaction_result_viewed`                                                                                                                                         |

### Core Action Card

| Thành phần        | Câu trả lời                                                                                                                                                                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Target user       | Người bệnh đang sử dụng đồng thời nhiều thuốc kê đơn, thuốc không kê đơn hoặc thực phẩm chức năng và muốn dùng thêm một sản phẩm.                                                                                                                                                                |
| Core job          | Biết sản phẩm dự định dùng thêm có tương tác với những sản phẩm đang sử dụng hay không để tránh kết hợp không an toàn.                                                                                                                                                                           |
| Core action       | Hoàn tất kiểm tra sản phẩm dự định dùng thêm với danh sách sản phẩm đang sử dụng và mở xem kết quả.                                                                                                                                                                                              |
| Object            | Một thuốc hoặc thực phẩm chức năng dự định dùng thêm và danh sách các sản phẩm người bệnh đang sử dụng.                                                                                                                                                                                          |
| Preconditions     | Có ít nhất một sản phẩm đang sử dụng và một sản phẩm dự định dùng thêm; các sản phẩm được nhận diện hợp lệ và hệ thống có đủ dữ liệu để thực hiện kiểm tra.                                                                                                                                      |
| Completion rule   | Kiểm tra hợp lệ đã hoàn tất và người dùng đã mở kết quả. Kết quả có thể là phát hiện tương tác, không phát hiện tương tác trong dữ liệu hiện có, hoặc chưa đủ dữ liệu kết luận nếu giới hạn được trình bày rõ. Không tính khi đầu vào không hợp lệ hoặc kết quả chỉ được tạo nhưng chưa được mở. |
| Core value        | Người bệnh nhận biết thông tin về tương tác và mức độ cảnh báo để chủ động trao đổi với bác sĩ hoặc dược sĩ.                                                                                                                                                                                     |
| Evidence of value | Người dùng mở kết quả thể hiện rõ trạng thái kiểm tra, nguồn thông tin và giới hạn sử dụng; áp dụng cả khi phát hiện, không phát hiện trong dữ liệu hiện có hoặc chưa đủ dữ liệu kết luận.                                                                                                       |
| Candidate event   | `interaction_result_viewed`                                                                                                                                                                                                                                                                      |

### Ranh giới của sản phẩm

- Chỉ cung cấp thông tin tra cứu tương tác và cảnh báo an toàn trong phạm vi dữ liệu hiện có.
- Không chỉ định ngừng thuốc, tiếp tục dùng thuốc hoặc thay đổi liều dùng.
- Không thay thế bác sĩ hoặc dược sĩ và không biến kết quả thành chẩn đoán.
- Không khuyến khích người dùng tự mua hoặc tự sử dụng thuốc dựa trên kết quả.
- “Không phát hiện tương tác” không đồng nghĩa với khẳng định kết hợp chắc chắn an toàn.

### Tự kiểm 5 tiêu chí — học viên xác nhận

- [ ] **Gần core value:** Hành vi này đưa người dùng tiến gần rõ rệt tới quyết định sử dụng an toàn.
- [x] **Có thể lặp lại:** Hành vi có thể xuất hiện lại khi người dùng cân nhắc một thuốc hoặc thực phẩm chức năng khác.
- [x] **Có thể quan sát:** Có thể xác định action hoàn tất khi kết quả kiểm tra hợp lệ được người dùng mở.
- [x] **Có ý nghĩa:** Số lần action tăng phản ánh nhiều nhu cầu kiểm tra an toàn được hoàn tất hơn, không chỉ là tăng thao tác giao diện.
- [x] **Có thể tác động:** Team có thể cải thiện khả năng hoàn tất qua dữ liệu thuốc, nhập liệu, độ rõ ràng của kết quả và xử lý lỗi.

**Giải thích vì sao không phải “mở app” hoặc “hỏi AI”:** Mở ứng dụng hoặc gửi câu hỏi cho AI chỉ là thao tác khởi đầu, chưa chứng minh người dùng đã nhận được thông tin tương tác. Core action chỉ hoàn tất khi người dùng thực hiện một lượt kiểm tra hợp lệ và mở xem kết quả. Kết quả có thể có giới hạn hoặc sai lệch theo dữ liệu hiện có, chỉ mang tính tham khảo, không phải chỉ định y tế và không thay thế bác sĩ hoặc dược sĩ.

**Kết luận Gate 1:** _4/5_

## 02 — Nature & cadence

### Action Nature Card

| Thành phần       | Câu trả lời                                                                                                                                         |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Actor            | Người bệnh đang sử dụng đồng thời nhiều thuốc kê đơn, thuốc không kê đơn hoặc thực phẩm chức năng.                                                  |
| Intent           | Muốn biết một sản phẩm mới có tương tác với danh sách sản phẩm đang sử dụng hay không.                                                              |
| Trigger          | Sự kiện bên ngoài làm phát sinh nhu cầu: có đơn thuốc mới, thay đổi thuốc đang dùng, hoặc cân nhắc một thuốc không kê đơn/thực phẩm chức năng khác. |
| Effort           | Lần đầu cần nhập hoặc xác nhận danh sách đang sử dụng và sản phẩm muốn kiểm tra; những lần sau cần xác nhận lại danh sách trước khi kiểm tra.       |
| Value timing     | Value xuất hiện ngay sau khi lượt kiểm tra hợp lệ hoàn tất và người dùng mở kết quả tương tác.                                                      |
| State            | Danh sách sản phẩm đang sử dụng và lịch sử kiểm tra có thể được lưu khi người dùng đồng ý.                                                          |
| Dependency       | Phụ thuộc khả năng nhận diện sản phẩm, độ đầy đủ và cập nhật của nguồn dữ liệu, cùng khả năng hệ thống đưa ra trạng thái kết quả rõ ràng.           |
| Repeat condition | Có thuốc mới, danh sách đang sử dụng thay đổi, hoặc phát sinh nhu cầu kiểm tra một thuốc không kê đơn/thực phẩm chức năng khác.                     |

### Kết luận cadence — học viên xác nhận

- **Dạng hành vi đã chọn:** Phản ứng theo sự kiện.
- **Kết luận theo template:** Đối với Người bệnh đang sử dụng đồng thời nhiều loại thuốc, bao gồm thuốc kê đơn, thuốc không kê đơn và thực phẩm chức năng; đôi khi tự mua thêm sản phẩm mà không hỏi ý kiến bác sĩ hoặc dược sĩ, core action Hoàn tất kiểm tra thuốc hoặc thực phẩm chức năng dự định dùng thêm với danh sách sản phẩm đang sử dụng và mở xem kết quả. thường xuất hiện khi người dùng muốn tìm hiểu thêm một thuốc như thuốc không kê đơn/thực phẩm chức năng có tương tác với thuốc mình đang sử dụng vì nhu cầu có phát sinh khi nhận đơn mới, đổi thuốc hoặc cân nhắc thêm thuốc/thực phẩm chức năng. Do đó, nhịp đo phù hợp là theo từng lượt tra cứu tương tác hợp lệ ở cấp lượt tra cứu.

**Câu kết luận của học viên:** Đối với người bệnh đang sử dụng đồng thời nhiều thuốc và thực phẩm chức năng, họ tra cứu tương tác và mở xem kết quả phân tích có thể gửi kết quả cho dược sĩ/bác sĩ.
**Kết luận Gate 2:** vì nhu cầu có phát sinh khi nhận đơn mới, đổi thuốc hoặc cân nhắc thêm thuốc/thực phẩm chức năng không biết có tương tác với thuốc đang sử dụng hay không?

## 03 — Metric System

### Activation metric

| Thành phần       | Định nghĩa                                                                                                                                                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Start event      | `interaction_check_started` — người dùng bắt đầu một lượt kiểm tra với danh sách sản phẩm đang sử dụng và sản phẩm cần tra cứu.                                                                                                 |
| Activation event | Lần đầu xảy ra `interaction_result_viewed` cho một lượt kiểm tra hợp lệ. Ba trạng thái đều được tính: phát hiện tương tác, không phát hiện trong dữ liệu hiện có, hoặc chưa đủ dữ liệu kết luận với giới hạn được trình bày rõ. |
| Time window      | Trong cùng phiên tính từ `interaction_check_started`.                                                                                                                                                                           |

### Engagement metric — ứng viên để học viên xác nhận

| Góc đo    | Metric ứng viên                                                                         |
| --------- | --------------------------------------------------------------------------------------- |
| Frequency | Số lượt `interaction_result_viewed` hợp lệ trên mỗi sự kiện phát sinh nhu cầu kiểm tra. |
| Depth     | Tỷ lệ kết quả được người dùng mở phần thông tin chi tiết, nguồn và giới hạn sử dụng.    |

**Lý do chọn frequency:** _[Học viên tự viết.]_

**Lý do chọn depth:** _[Học viên tự viết.]_

### North Star Metric — ứng viên để học viên xác nhận

**NSM:** Số lượt xem kết quả tương tác đủ điều kiện theo từng sự kiện phát sinh nhu cầu.

- **Unit of value:** Một kết quả tương tác được người dùng mở xem.
- **Quality threshold:** Đầu vào được nhận diện hợp lệ; kết quả thể hiện rõ trạng thái, nguồn thông tin và giới hạn sử dụng. Trạng thái “chưa đủ dữ liệu” chỉ đạt ngưỡng khi lý do và giới hạn được hiển thị rõ.
- **Frequency:** Ít nhất một lượt kết quả đủ điều kiện được xem trong mỗi sự kiện phát sinh nhu cầu kiểm tra.

### Leading indicators — ứng viên để học viên xác nhận

| Leading indicator                                                               | Vì sao tin nó dự báo core action lặp lại? |
| ------------------------------------------------------------------------------- | ----------------------------------------- |
| Tỷ lệ danh sách đầu vào được nhận diện và xác nhận hợp lệ                       | _[Học viên tự viết.]_                     |
| Tỷ lệ lượt kiểm tra đi từ `interaction_check_started` đến khi có kết quả hợp lệ | _[Học viên tự viết.]_                     |
| Tỷ lệ kết quả hợp lệ được người dùng mở xem                                     | _[Học viên tự viết.]_                     |

### Counter-metric — chọn ít nhất một

- [ ] Tỷ lệ kết quả “chưa đủ dữ liệu kết luận”.
- [ ] Tỷ lệ thuốc hoặc thực phẩm chức năng không được nhận diện.
- [ ] Tỷ lệ lỗi nghiêm trọng được phát hiện qua kiểm định chuyên môn.
- [ ] Tỷ lệ người dùng đóng kết quả trước khi xem nội dung chính.

## 04 — Retention Definition

| Thành phần   | Định nghĩa                                                                                                                                                       |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unit         | Người bệnh.                                                                                                                                                      |
| Cohort entry | Lần đầu người bệnh có `interaction_result_viewed` cho một lượt kiểm tra hợp lệ.                                                                                  |
| Return event | `interaction_result_viewed` cho một lượt kiểm tra hợp lệ khác trong một sự kiện phát sinh nhu cầu mới.                                                           |
| Window       | Opportunity-based: cơ hội tiếp theo khi có thuốc mới, danh sách đang sử dụng thay đổi hoặc người bệnh cân nhắc một sản phẩm khác. Không dùng D7/weekly mặc định. |
| Threshold    | Ít nhất một kết quả đủ điều kiện được mở xem trong cơ hội phát sinh nhu cầu mới.                                                                                 |
| Segment      | Người bệnh đang sử dụng đồng thời nhiều thuốc kê đơn, thuốc không kê đơn hoặc thực phẩm chức năng.                                                               |

**Cách đọc:** Trong số người bệnh thuộc cohort có ghi nhận một cơ hội kiểm tra mới, tỷ lệ bao nhiêu người mở ít nhất một kết quả tương tác đủ điều kiện trong cơ hội đó.

**Giới hạn đo lường:** Nếu sự kiện thay đổi/cân nhắc thuốc xảy ra ngoài sản phẩm và không được ghi nhận, không thể biết chắc người dùng có một cơ hội quay lại. Không được tự động xem người không quay lại theo D7/D30 là churn.

### Tự kiểm Gate 3 — học viên xác nhận

- [ ] Activation có start event, activation event và time window.
- [ ] Engagement chọn tối đa hai góc đo.
- [ ] Retention có đủ sáu thành phần và khớp cadence phản ứng theo sự kiện.
- [ ] NSM có unit of value, quality threshold và frequency.
- [ ] Đã chọn ít nhất một counter-metric.

**Kết luận Gate 3:** _[Học viên tự xác nhận sau khi chọn metric và viết rationale.]_

## Điều tôi mang về áp dụng cho dự án thật

_[Học viên tự viết sau khi hoàn thành bài]_

## Checklist trước khi nộp

- [ ] Link Metrics Pack mở được ở chế độ xem.
- [ ] Metrics Pack có đủ các phần từ 00 đến 07.
- [ ] Core Action vượt qua ít nhất 4/5 tiêu chí tự kiểm.
- [ ] Cadence xuất phát từ nature và có giải thích “vì”.
- [ ] Retention có đủ 6 thành phần.
- [ ] North Star Metric gồm unit of value, quality threshold và frequency.
- [ ] Có counter-metric.
- [ ] Product Loop có ít nhất 2 chu kỳ và metric hypothesis nối với metric.
- [ ] Tracking có 4–8 events và ít nhất 2 acceptance criteria.
- [ ] AI Support Log phản ánh đúng việc sử dụng AI.
