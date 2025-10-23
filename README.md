# Project about Transaction dashboard 

## Dashboard in Power BI
Đây là tổng quan dashboard, có 4 phần chính:
- Customer Dashboard
- Transaction Dashboard
- Fraud Detection
- Transaction details

<img width="1456" height="812" alt="image" src="https://github.com/user-attachments/assets/b5fb8c4f-dcdb-42fa-81d8-6b0e90435950" />

<img width="1434" height="806" alt="image" src="https://github.com/user-attachments/assets/599ea750-b2b6-4b7b-9dc9-663926001c83" />

<img width="1431" height="804" alt="image" src="https://github.com/user-attachments/assets/c5c58234-a9eb-40b2-aca7-4e7518e887b2" />

<img width="1428" height="799" alt="image" src="https://github.com/user-attachments/assets/c5ecefbf-ead4-4faf-9306-617fe398955a" />

Trước khi đến được bước làm dashboard, việc etl là việc không thể thiếu với bộ dữ liệu quá xấu này. Các mục chính mà tôi đã làm với dữ liệu gốc: (cụ thể trong file .ipynb)

- Customer:
  - Ngày sinh, Ngày đăng ký, Ngày kích hoạt lần đầu, Ngày đăng nhập cuối cùng (Các cột liên quan đến ngày) đang có định dạng lung tung như mm/dd/yyyy hoặc dd/mm/yyyy hoặc thậm chí yyyy/mm/dd,... =>> Tạo ra 1 code để biến đối tất cả về 1 định dạng mm/dd/yyyy sao cho có thể áp dụng cho đồng loạt tất cả các định dạng có thể xảy ra
  - Tạo thêm cột tuổi
  - Tạo thêm cột nhóm tuổi
  - Tạo thêm cột Thành phố đăng ký 
- Transaction:
  - Tương tự chỉnh lại cột Thời gian giao dịch về lại đúng định dạng
  - Thêm cột thời gian trong ngày (sáng trưa chiều tối)

 ## Dashboard in Looker Studio
 
 You can see Dashboard at Link: https://lookerstudio.google.com/reporting/9cf74dca-35fa-46bd-97b3-1b62c9b20e3c

## Customer_Segmentation
Đây là bài toán Phân khúc khách hàng bằng cách sử dụng RFM và KMeans,  các bước cụ thể:
- Thực hiện biến đổi dữ liệu để tạo ra dataframe với cột customer_id và 3 cột feature theo mô hình RFM
  - Recency: Ngày mua hàng gần nhất
  - Frequency: Tần suất mua hàng
  - MontaryValue: Giá trị mà khách hàng đã bỏ ra
- Chuẩn hóa dữ liệu để gần nhất với normal distribution bằng cách tối ưu điểm skewness về ~ 0 bằng 1 trong 4 phương pháp:
  - Log Transformation
  - Square Root Transformation
  - Box-Cox Transformation
  - Yeo-Johnson Transformation
- Scale dữ liệu bằng phương pháp Standard Scaling (phương pháp này tốt với dữ liệu được chuqẩn hoá)
- Đưa dữ liệu vào mô hình KMeans:
  - Chọn số cụm bằng Elbow
 

## Kết luận, so sánh 2 công cụ Power BI và Looker Studio 
Về khả năng xử lý dữ liệu
- Power BI thể hiện ưu thế rõ rệt ở khả năng xử lý dữ liệu thô (raw data). Các hàm DAX trong Power BI cho phép tính toán phức tạp trực tiếp trên dữ liệu gốc mà không cần tiền xử lý nhiều. Các thao tác như tạo line chart so sánh theo tháng của năm trước, hoặc các phép tính rolling average, cumulative, year-over-year,… đều có thể thực hiện dễ dàng.
- Ngược lại, trong Looker Studio, việc thực hiện các phép tính tương tự gần như rất khó hoặc bị giới hạn, do công cụ này phụ thuộc nhiều vào dữ liệu đã được xử lý và tổng hợp sẵn (grouped / pre-aggregated). → Vì vậy, Looker Studio phù hợp hơn khi dữ liệu đầu vào đã được chuẩn bị kỹ, chẳng hạn như đã group theo segment, date, hay metric cụ thể từ trước.

Về Khả năng chia sẻ và cộng tác: 
- Ở khía cạnh chia sẻ báo cáo, Looker Studio vượt trội hơn rõ rệt. Người dùng có thể public dashboard lên web, hoặc phân quyền theo email nhanh chóng, thuận tiện cho việc cộng tác.
- Trong khi đó, Power BI yêu cầu một khoản chi phí nhất định để chia sẻ dashboard cho người khác. Khi số lượng người truy cập tăng lên, chi phí cấp quyền và license cũng tăng tương ứng.
- Ngoài ra, Looker Studio hỗ trợ public và refresh dữ liệu linh hoạt hơn, giúp việc cập nhật dashboard diễn ra trơn tru hơn trong môi trường chia sẻ.

Về giao diện và trải nghiệm người dùng (phần này cần nhấn mạnh đây là cảm quan cá nhân):
- Looker Studio mang đến giao diện hiện đại, trực quan, với các biểu đồ (chart) có thiết kế đẹp sẵn, chỉ cần kéo – thả là có được dashboard bắt mắt.
- Power BI tuy mạnh về kỹ thuật, nhưng để có visual đẹp và chuẩn thẩm mỹ, người dùng cần đầu tư nhiều thời gian tinh chỉnh hơn (format chart, màu sắc, layout, theme,…).

Bảng so sánh tổng quan:
| Tiêu chí                       | **Power BI**                                        | **Looker Studio**                                   |
| ------------------------------ | --------------------------------------------------- | --------------------------------------------------- |
| **Xử lý dữ liệu**              | Xuất sắc – DAX mạnh mẽ, xử lý tốt dữ liệu raw       | Hạn chế – cần dữ liệu đã được group/prepare sẵn     |
| **Khả năng chia sẻ**           | Cần trả phí để chia sẻ, khó public web              | Miễn phí, chia sẻ qua email hoặc public dễ dàng     |
| **Tự động cập nhật (refresh)** | Có, nhưng phụ thuộc license Power BI Service        | Dễ dàng, tự động hơn khi dùng data source online    |
| **Giao diện và thẩm mỹ**       | Cần tùy chỉnh nhiều mới đẹp                         | Giao diện, chart mặc định đẹp, hiện đại             |
| **Phù hợp với**                | Doanh nghiệp cần xử lý dữ liệu phức tạp, có team BI | Người dùng cá nhân, team nhỏ, dữ liệu đã được xử lý |


**Kết luận**
- Power BI là công cụ mạnh mẽ về xử lý và phân tích dữ liệu, thích hợp với bài toán chuyên sâu, dữ liệu phức tạp.
- Ngược lại, Looker Studio nổi bật với tính chia sẻ, tốc độ triển khai và thẩm mỹ cao, phù hợp khi dữ liệu đã được chuẩn bị sẵn và mục tiêu là truyền tải nhanh, đẹp, và dễ tiếp cận.


















