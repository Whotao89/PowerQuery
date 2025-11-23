# Ghi chú riel cho phần left outer join 
---
## File 1: Customers.csv (Danh sách khách hàng)
*Lưu ý: Khách số 4 và 5 chưa từng mua gì.*
```csv
CustomerID,CustomerName,City
1,Nguyen Van A,Ha Noi
2,Tran Thi B,TP HCM
3,Le Van C,Da Nang
4,Pham Thi D,Can Tho
5,Hoang Van E,Hai Phong

## File 2: Orders.csv (Danh sách đơn hàng)
- File này chứa các giao dịch. Lưu ý đơn hàng 1005 có CustomerID là 99

OrderID,CustomerID,Date,Amount
1001,1,2024-01-01,500000
1002,1,2024-01-05,200000
1003,2,2024-01-10,1500000
1004,3,2024-01-12,800000
1005,99,2024-01-20,100000

(1) LEFT OUTER JOIN 
Giữ toàn bộ dữ liệu từ bảng bên trái (trước), lấy thêm phần khớp từ các phần khớp với bảng bên phải (JOIN bên sql thì mặc định hai table () phải có cột attribute giống nhau còn gì).
- Join theo cột CustomerID, xong sẽ cho ra kết quả giống trong ảnh result.png
- Giờ expand một cách phù hợp là ok.
- Ý nghĩa trong trường hợp này là gì?  Là gộp 2 phần bảng riêng lại để tiện so sánh cho các bước khác, nhiều mà, hồi học databasse  có đầy thây.
