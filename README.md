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

<img width="1086" height="749" alt="image" src="https://github.com/user-attachments/assets/49812bd7-3b6c-4e0e-b467-72d930f83742" />

<img width="1090" height="827" alt="image" src="https://github.com/user-attachments/assets/a2fa48c1-5164-4026-b502-8965520d0501" />

<img width="1094" height="824" alt="image" src="https://github.com/user-attachments/assets/8a64e971-4dd7-49e4-8061-bae42f457463" />

<img width="1094" height="826" alt="image" src="https://github.com/user-attachments/assets/da73f554-ad5e-4b7a-b4bf-181872da74ef" />




 ## Dashboard in Tableau

 <img width="1509" height="804" alt="image" src="https://github.com/user-attachments/assets/b6d3075f-215e-4dd1-813d-70dc3a26febf" />

 <img width="1507" height="798" alt="image" src="https://github.com/user-attachments/assets/f083473c-cdca-4387-bdb9-b478bfadea7d" />

 <img width="1502" height="797" alt="image" src="https://github.com/user-attachments/assets/86a3dd3b-b2bc-4417-bbcc-34a524b7586b" />













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
 

## Kết luận, so sánh 3 công cụ Power BI, Looker Studio và Tableau
Về khả năng xử lý dữ liệu
- Power BI thể hiện ưu thế rõ rệt ở khả năng xử lý dữ liệu thô (raw data). Các hàm DAX trong Power BI cho phép tính toán phức tạp trực tiếp trên dữ liệu gốc mà không cần tiền xử lý nhiều. Các thao tác như tạo line chart so sánh theo tháng của năm trước, hoặc các phép tính rolling average, cumulative, year-over-year,… đều có thể thực hiện dễ dàng.
- Ngược lại, trong Looker Studio, việc thực hiện các phép tính tương tự gần như rất khó hoặc bị giới hạn, do công cụ này phụ thuộc nhiều vào dữ liệu đã được xử lý và tổng hợp sẵn (grouped / pre-aggregated). → Vì vậy, Looker Studio phù hợp hơn khi dữ liệu đầu vào đã được chuẩn bị kỹ, chẳng hạn như đã group theo segment, date, hay metric cụ thể từ trước.
- Tableau nằm ở giữa, cũng là 1 công cụ xử lý dữ liệu rất mạnh, làm việc với dữ liệu lớn tốt nhất trong 3 tool, tableau caculation khá linh hoạt và xử lý được đa dạng vấn đề 

Về Khả năng chia sẻ và cộng tác: 
- Ở khía cạnh chia sẻ báo cáo, Looker Studio vượt trội hơn rõ rệt. Người dùng có thể public dashboard lên web, hoặc phân quyền theo email nhanh chóng, thuận tiện cho việc cộng tác mà không tốn chi phí. 
- Trong khi đó, Power BI yêu cầu một khoản chi phí nhất định để chia sẻ dashboard cho người khác. Khi số lượng người truy cập tăng lên, chi phí cấp quyền và license cũng tăng tương ứng.
- Tableau tương tự Power BI chia sẻ qua Tableau Server hoặc Tableau Online → giá khá cao.

Về giao diện và trải nghiệm người dùng (phần này cần nhấn mạnh đây là cảm quan cá nhân):
- Looker Studio mang đến giao diện hiện đại, trực quan, với các biểu đồ (chart) có thiết kế đẹp sẵn, chỉ cần kéo – thả là có được dashboard bắt mắt.
- Power BI tuy mạnh về kỹ thuật, nhưng để có visual đẹp và chuẩn thẩm mỹ, người dùng cần đầu tư nhiều thời gian tinh chỉnh hơn (format chart, màu sắc, layout, theme,…).
- Mạnh nhất trong 3 công cụ vì tableau tinh chỉnh rất kĩ từng biểu đồ, vì vậy có thể làm nổi bật lên những điểm nổi bật (dễ ra insight) trên 1 biểu đồ -> Là công cụ phù hợp với story telling dữ liệu nhất, tuy nhiên công cụ này lại rất khó trong việc căn chỉnh layout dashboard tổng

Về hiệu năng & xử lý dữ liệu lớn: 
- Looker Studio: yếu nhất, phụ thuộc data source; yếu với dữ liệu quá lớn nếu không dùng BigQuery.
- Power BI: xử lý tốt dataset trung bình–lớn, hiệu năng cao khi import mode; DirectQuery cần tối ưu.
- Tableau: rất mạnh trong việc xử lý dữ liệu lớn, đặc biệt trong các bài toán cần tương tác nhanh, kéo thả real-time -> mạnh nhất trong 3 tool

Về chi phí: 
- Looker Studio: miễn phí gần như toàn bộ.
- Power BI: giá hợp lý hơn Tableau (Power BI Pro/ Premium).
- Tableau: đắt nhất. Đây gần như là nhược điểm lớn nhất khiến nhiều team dù thích visual của Tableau vẫn chọn Power BI.



| Tiêu chí                       | **Power BI**                                           | **Looker Studio**                 | **Tableau**                                                      |
| ------------------------------ | ------------------------------------------------------ | --------------------------------- | ---------------------------------------------------------------- |
| **Xử lý dữ liệu**              | Mạnh nhất với DAX & Power Query, xử lý tốt dữ liệu raw | Yếu, cần dữ liệu đã group/prepare | Mạnh, LOD Expressions & window calc tốt                          |
| **Khả năng chia sẻ**           | Trả phí, phụ thuộc license                             | Miễn phí, chia sẻ dễ              | Trả phí cao, phụ thuộc Tableau Server                            |
| **Tự động cập nhật (refresh)** | Tốt nhưng giới hạn theo license                        | Dễ, linh hoạt với online source   | Tốt, phụ thuộc Server                                            |
| **Visual & storytelling**      | Cần chỉnh nhiều, visual mặc định không đẹp             | Giao diện đẹp sẵn                 | Xuất sắc, tinh chỉnh sâu, tập trung insight                      |
| **Xử lý dữ liệu lớn**          | Tốt (Import mode)                                      | Phụ thuộc nguồn                   | Rất tốt, tương tác nhanh                                         |
| **Chi phí**                    | Trung bình                                             | Miễn phí                          | Đắt nhất                                                         |



**Kết luận**
- Đối với doanh nghiệp vừa, dữ liệu lớn -> Nên dùng Power BI (tool này cũng đang rất phổ biến tại Việt Nam)
- Đối với doanh nghiệp lớn, dữ liệu siêu lớn (big data), cần real-time -> Nên dùng Tableau (tool này rất phổ biến tại các công ty lớn ở nước ngoài)
- Đối với các doanh nghiệp nhỏ, đặc biệt là các studio game -> Nên dùng Looker Studio (Tool này tuy không xử lý dữ liệu lớn được nhưng nếu là dữ liệu lưu trên Google Bigquery - thường là cloud của dữ liệu game và app thì lại tương thích cực tốt)


















