# Project about Transaction dashboard 
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


