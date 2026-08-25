# Product Metrics Lab

- **Họ và tên:** Lê Thị Linh
- **Mã học viên:** 2A202601441
- **Dự án chọn làm:** P-005 — Ứng dụng y tế tra cứu tương tác thuốc và cảnh báo sử dụng thuốc an toàn
- **Metrics Pack:** [PowerPoint — Metrics Pack P-005](./Metrics_Pack_P005_LeThiLinh.pptx) _(cần kiểm tra quyền truy cập sau khi push hoặc thay bằng link Google Slides/Canva đã cấp quyền xem)_

## 00 — Phạm vi

- **Dự án:** P-005 — Ứng dụng y tế tra cứu tương tác thuốc và cảnh báo sử dụng thuốc an toàn.
- **Persona:** Người bệnh đang sử dụng đồng thời nhiều loại thuốc, bao gồm thuốc kê đơn, thuốc không kê đơn và thực phẩm chức năng; đôi khi tự mua thêm sản phẩm mà không hỏi ý kiến bác sĩ hoặc dược sĩ.
- **Core job:** “Khi muốn dùng thêm một loại thuốc hoặc thực phẩm chức năng, tôi cần biết sản phẩm đó có tương tác với những thứ mình đang sử dụng hay không, để tránh sử dụng kết hợp không an toàn.”

## 01 — Core Action

### Phân biệt bốn khái niệm

| Khái niệm        | Câu trả lời                                                                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Core job         | Biết một loại thuốc hoặc thực phẩm chức năng mới có tương tác với những sản phẩm đang sử dụng hay không để tránh kết hợp không an toàn.          |
| Core action      | Hoàn tất kiểm tra thuốc hoặc thực phẩm chức năng dự định dùng thêm với danh sách sản phẩm đang sử dụng và mở xem kết quả.                        |
| Core value       | Người bệnh nhận biết thông tin tương tác và mức độ cảnh báo để trao đổi với bác sĩ hoặc dược sĩ; ứng dụng không đưa ra quyết định sử dụng thuốc. |
| Core value event | `interaction_result_viewed`                                                                                                                      |

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

- [ ] **Gần core value:** Hành vi này giúp người dùng nhận biết thông tin tương tác và mức độ cảnh báo để trao đổi với bác sĩ hoặc dược sĩ.
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
  **Câu kết luận của học viên:** Đối với người bệnh đang sử dụng đồng thời nhiều thuốc kê đơn, thuốc không kê đơn và thực phẩm chức năng, core action hoàn tất một lượt kiểm tra tương tác hợp lệ và mở xem kết quả thường xuất hiện khi họ nhận đơn mới, đổi thuốc hoặc cân nhắc thêm một sản phẩm, vì chỉ những thay đổi này mới làm phát sinh nhu cầu kiểm tra tự nhiên. Do đó, nhịp đo phù hợp là theo từng lượt tra cứu tương tác hợp lệ ở cấp lượt tra cứu.

**Kết luận Gate 2:** Đạt — cadence xuất phát từ sự kiện thay đổi hoặc cân nhắc thuốc, không từ lịch daily/weekly hay notification.

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

**Lý do chọn frequency:** Cho biết người dùng có hoàn tất tra cứu khi nhu cầu mới xuất hiện hay không.

**Lý do chọn depth:** Việc mở nguồn và giới hạn sử dụng cho thấy người dùng không chỉ nhìn lướt qua cảnh báo.

### North Star Metric — ứng viên để học viên xác nhận

**NSM:** Tỷ lệ sự kiện phát sinh nhu cầu có ít nhất một kết quả tương tác đủ điều kiện được người dùng mở.

- **Unit of value:** Một sự kiện phát sinh nhu cầu kiểm tra có kết quả tương tác được người dùng mở xem.
- **Quality threshold:** Đầu vào được nhận diện hợp lệ; kết quả thể hiện rõ trạng thái, nguồn thông tin và giới hạn sử dụng. Trạng thái “chưa đủ dữ liệu” chỉ đạt ngưỡng khi lý do và giới hạn được hiển thị rõ.
- **Frequency:** Ít nhất một lượt kết quả đủ điều kiện được xem trong mỗi sự kiện phát sinh nhu cầu kiểm tra.

### Leading indicators — ứng viên để học viên xác nhận

| Leading indicator                                                               | Vì sao tin nó dự báo core action lặp lại?                                                        |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Tỷ lệ danh sách đầu vào được nhận diện và xác nhận hợp lệ                       | người dùng không nhận diện thông tin sẽ chặn người dùng trước khi có kết quả                     |
| Tỷ lệ lượt kiểm tra đi từ `interaction_check_started` đến khi có kết quả hợp lệ | xác nhận và xử lý kết quả                                                                        |
| Tỷ lệ kết quả hợp lệ được người dùng mở xem                                     | phản ánh mức độ người dùng xem kết quả kỹ hơn, nhưng cần dữ liệu nó có dự báo lần quay lại hay k |

### Counter-metric — chọn ít nhất một

- [ ] Tỷ lệ kết quả “chưa đủ dữ liệu kết luận”.
- [ ] Tỷ lệ thuốc hoặc thực phẩm chức năng không được nhận diện.
- [x] Tỷ lệ lỗi nghiêm trọng được phát hiện qua kiểm định chuyên môn.
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

- [x] Activation có start event, activation event và time window.
- [x] Engagement chọn tối đa hai góc đo.
- [x] Retention có đủ sáu thành phần và khớp cadence phản ứng theo sự kiện.
- [x] NSM có unit of value, quality threshold và frequency.
- [x] Đã chọn ít nhất một counter-metric.

**Kết luận Gate 3:** Đạt 5/5 — activation tính được, retention đủ sáu thành phần và khớp cadence, NSM có đủ ba thành phần, đồng thời đã chọn counter-metric về lỗi nghiêm trọng qua kiểm định chuyên môn.

## 05 — Product Loop

- **Loại loop chính:** Event-response.
- **Reason to return không phụ thuộc notification:** Một thuốc mới, thay đổi danh sách đang sử dụng hoặc nhu cầu cân nhắc một sản phẩm khác tạo ra lý do tự nhiên để kiểm tra lại. Danh sách đã lưu giúp giảm công sức nhập lại ở lần sau.

### Chu kỳ 1

**Có thuốc mới hoặc danh sách thay đổi** → xác nhận danh sách đang sử dụng → hoàn tất kiểm tra và mở kết quả → nhận biết trạng thái tương tác, nguồn và giới hạn → lưu danh sách đã xác nhận cùng lịch sử kiểm tra khi người dùng đồng ý.

### Chu kỳ 2

**Phát sinh nhu cầu kiểm tra tiếp theo** → dùng lại và cập nhật danh sách đã lưu → hoàn tất lượt kiểm tra hợp lệ mới và mở kết quả → tiếp tục nhận biết thông tin tương tác với ít thao tác nhập lại hơn → trạng thái đã lưu được cập nhật cho cơ hội tiếp theo.

### Metric hypothesis — học viên tự viết

> Nếu loop này hoạt động, metric _[một metric ở Phase 3]_ sẽ thay đổi theo hướng _[tăng/giảm]_ trong _[khung thời gian hoặc số cơ hội tiếp theo]_, vì _[cơ chế của loop do học viên giải thích]_.

**Metric hypothesis của học viên:** Nếu loop này hoạt động, tỷ lệ sự kiện phát sinh nhu cầu có ít nhất một kết quả tương tác đủ điều kiện được người dùng mở (NSM) sẽ tăng trong ba cơ hội kiểm tra tiếp theo, vì danh sách thuốc đã được lưu và xác nhận giúp người dùng giảm thao tác nhập lại, hoàn tất lượt kiểm tra mới nhanh hơn và duy trì thói quen mở kết quả khi có thay đổi về thuốc hoặc thực phẩm chức năng.

## 06 — Tracking nhanh

| Tên event                           | Ý nghĩa                                                                           | Thời điểm ghi nhận                                                                                                                          | Metric sử dụng                                                       |
| ----------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `medication_list_updated`           | Danh sách sản phẩm đang sử dụng đã thay đổi thực sự.                              | Sau khi thay đổi được lưu thành công và khác trạng thái trước đó.                                                                           | Xác định cơ hội mới cho opportunity-based retention.                 |
| `medication_list_confirmed`         | Người dùng đã xác nhận danh sách dùng cho lượt kiểm tra là đúng tại thời điểm đó. | Sau thao tác xác nhận thành công, trước khi gửi kiểm tra.                                                                                   | Leading indicator: tỷ lệ đầu vào được nhận diện và xác nhận hợp lệ.  |
| `interaction_check_started`         | Một lượt kiểm tra tương tác hợp lệ đã bắt đầu xử lý.                              | Khi hệ thống chấp nhận đầu vào hợp lệ và tạo `check_id`; không ghi ngay khi người dùng chỉ bấm nút.                                         | Start event của activation; mẫu số của tỷ lệ hoàn tất kiểm tra.      |
| `interaction_check_completed`       | Hệ thống đã hoàn tất xử lý và tạo một trạng thái kết quả.                         | Khi `check_id` chuyển sang trạng thái kết thúc: phát hiện, không phát hiện trong dữ liệu hiện có hoặc chưa đủ dữ liệu với giới hạn rõ ràng. | Leading indicator; phân tích trạng thái “chưa đủ dữ liệu”.           |
| `interaction_result_viewed`         | Người dùng đã mở một kết quả tương tác đủ điều kiện.                              | Lần đầu nội dung chính của kết quả được hiển thị thành công cho `user_id` và `check_id`.                                                    | Activation, frequency engagement, NSM và return event của retention. |
| `interaction_result_details_viewed` | Người dùng đã mở phần nguồn thông tin và giới hạn sử dụng.                        | Khi phần chi tiết được mở và hiển thị thành công.                                                                                           | Depth engagement.                                                    |
| `interaction_result_audited`        | Một kết quả đã được người có chuyên môn kiểm định và gắn kết luận đánh giá.       | Sau khi quy trình kiểm định hoàn tất và kết quả audit được lưu.                                                                             | Counter-metric: tỷ lệ lỗi nghiêm trọng qua kiểm định chuyên môn.     |

### Acceptance criteria

1. Với mỗi cặp `user_id` và `check_id`, chỉ ghi `interaction_result_viewed` khi nội dung chính của kết quả đã hiển thị thành công. Việc bấm nút kiểm tra, kết quả còn tải hoặc xử lý thất bại không được tạo event này.
2. Reload, retry hoặc mở lại cùng kết quả trong lịch sử không được tạo thêm `interaction_result_viewed` dùng để tính activation, NSM hoặc retention cho cùng `check_id`.
3. Mỗi `check_id` chỉ có một `interaction_check_completed` cho trạng thái kết thúc đầu tiên. Retry kỹ thuật phải dùng lại idempotency key và không ghi trùng.
4. Chỉ ghi `medication_list_updated` khi danh sách đã lưu khác trạng thái trước đó; autosave không thay đổi dữ liệu không được tạo event mới.
5. Chỉ ghi `interaction_result_audited` sau khi người kiểm định có thẩm quyền hoàn tất đánh giá; event phải tham chiếu đúng `check_id` và phiên bản kết quả.

### Tự kiểm Gate 4 — học viên xác nhận

- [x] Loop có ít nhất hai chu kỳ.
- [x] Reason to return đến từ nhu cầu tự nhiên, không phải notification.
- [x] Metric hypothesis trỏ đến một metric ở Phase 3.
- [x] Có từ 4 đến 8 events.
- [x] Mọi event đều map về ít nhất một metric.
- [x] Có ít nhất hai acceptance criteria chống bắn sớm và ghi trùng.

**Kết luận Gate 4:** Đạt 6/6 tiêu chí. Product loop có hai chu kỳ, lý do quay lại xuất phát từ nhu cầu kiểm tra tự nhiên, metric hypothesis liên kết trực tiếp với NSM ở Phase 3; tracking gồm 7 events, mỗi event đều gắn với metric và có 5 acceptance criteria để hạn chế ghi nhận sớm hoặc trùng lặp.

## 07 — Revision

- Không thay đổi core action hoặc cadence đã chọn.
- Làm rõ ranh giới sản phẩm: kết quả chỉ cung cấp thông tin tham khảo, không chỉ định ngừng/tiếp tục dùng thuốc, thay đổi liều hoặc tự mua thuốc.
- Mở rộng completion rule theo quyết định của học viên: trạng thái “chưa đủ dữ liệu kết luận” vẫn được tính khi người dùng mở kết quả và giới hạn được trình bày rõ.
- Thống nhất NSM theo dạng tỷ lệ sự kiện phát sinh nhu cầu có ít nhất một kết quả tương tác đủ điều kiện được mở.

## Điều tôi mang về áp dụng cho dự án thật

Qua bài này, tôi hiểu rằng cần xác định rõ core action trước khi xây dựng tính năng và đo lường sản phẩm. Với ứng dụng tra cứu tương tác thuốc, giá trị không nằm ở việc người dùng mở ứng dụng hay gửi câu hỏi cho AI, mà ở việc họ hoàn tất một lượt kiểm tra hợp lệ và thực sự mở xem kết quả. Tôi sẽ áp dụng cách xây dựng hệ metric gắn với hành vi tạo giá trị, đo retention theo cơ hội phát sinh nhu cầu thay vì mặc định theo D7/D30, đồng thời thiết kế event và acceptance criteria rõ ràng để tránh ghi nhận quá sớm hoặc trùng lặp. Bên cạnh chỉ số tăng trưởng, tôi cũng sẽ theo dõi counter-metric về sai sót chuyên môn nhằm bảo đảm sản phẩm phát triển nhưng vẫn ưu tiên độ an toàn và không thay thế quyết định của bác sĩ hoặc dược sĩ.

## Checklist trước khi nộp

- [x ] Link Metrics Pack mở được ở chế độ xem.
- [x] Metrics Pack có đủ các phần từ 00 đến 07.
- [x] Core Action vượt qua ít nhất 4/5 tiêu chí tự kiểm.
- [x] Cadence xuất phát từ nature và có giải thích “vì”.
- [x] Retention có đủ 6 thành phần.
- [x] North Star Metric gồm unit of value, quality threshold và frequency.
- [x] Có counter-metric.
- [x] Product Loop có ít nhất 2 chu kỳ và metric hypothesis nối với metric.
- [x] Tracking có 4–8 events và ít nhất 2 acceptance criteria.
- [x] AI Support Log phản ánh đúng việc sử dụng AI.
