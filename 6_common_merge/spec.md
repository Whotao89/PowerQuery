# Ghi chú riel cho phần left outer join 
---
## File 1: Customers.csv (Danh sách khách hàng)
```csv
CustomerID,CustomerName,City
1,Nguyen Van A,Ha Noi
2,Tran Thi B,TP HCM
3,Le Van C,Da Nang
4,Pham Thi D,Can Tho
5,Hoang Van E,Hai Phong
```
## File 2: Orders.csv (Danh sách đơn hàng)
- File này chứa các giao dịch. Lưu ý đơn hàng 1005 có CustomerID là 99
```csv
OrderID,CustomerID,Date,Amount
1001,1,2024-01-01,500000
1002,1,2024-01-05,200000
1003,2,2024-01-10,1500000
1004,3,2024-01-12,800000
1005,99,2024-01-20,100000
```
# 1. LEFT OUTER JOIN 
Giữ toàn bộ dữ liệu từ bảng bên trái (trước), lấy thêm phần khớp từ các phần khớp với bảng bên phải (JOIN bên sql thì mặc định hai table () phải có cột attribute giống nhau còn gì).
- Join theo cột CustomerID, xong sẽ cho ra kết quả giống trong ảnh result.png (chê).
- Giờ expand một cách phù hợp là ok.
- Ý nghĩa trong trường hợp này là gì?  Là gộp 2 phần bảng riêng lại để tiện so sánh cho các bước khác, nhiều mà, hồi học databasse  có đầy thây.

# 2. RIGHT OUTER JOIN
Ngược lại với cái trên. Giữ toàn bộ bảng bên phải (Orders), chỉ lấy phần khớp từ bảng bên trái (Customers).
- Kết quả: Mấy ông khách D, E (không mua gì) sẽ bay màu. Ngược lại, cái đơn hàng 1005 (ID 99) sẽ hiện ra, nhưng cột tên khách hàng sẽ dính `null`.
- Ý nghĩa: Dùng khi sếp bảo "Tao chỉ quan tâm đến doanh thu thôi, có tên khách hay không kệ xác nó", miễn là bảng Orders đủ là được.

# 3. FULL OUTER JOIN
Lấy tất, không chừa ai. Bên trái có cũng lấy, bên phải có cũng lấy.
- Kết quả: Ra cái bảng dài nhất. Ông D, E (không mua) vẫn hiện. Cái đơn lỗi 1005 (không có tên) cũng hiện nốt.
- Ý nghĩa: Bức tranh toàn cảnh. Kiểu sợ mất dữ liệu nên cứ gom hết vào rồi tính sau.

# 4. INNER JOIN (hàng tuyển)
Hàng tuyển. Chỉ lấy những dòng khớp ở CẢ HAI bảng.
- Kết quả: Sạch bong kin kít. Chỉ hiện khách A, B, C và đơn của họ. Ông D, E lượn. Đơn 99 lượn.
- Ý nghĩa: Dùng để báo cáo doanh thu thực tế chuẩn chỉnh, loại bỏ mấy cái data rác hoặc khách hàng ảo. (Trong SQL cái này dùng nhiều nhất).

# 5. LEFT ANTI JOIN
Chỉ lấy những dòng ở bảng trái (Customers) mà KHÔNG tìm thấy bên bảng phải.
- Kết quả: Lọc ra đúng 2 ông: Pham Thi D và Hoang Van E.
- Ý nghĩa: Tìm mấy ông "khách ngắm". Data này ném cho Marketing gửi mail dụ dỗ mua hàng.

# 6. RIGHT ANTI JOIN
Chỉ lấy những dòng ở bảng phải (Orders) mà KHÔNG tìm thấy bên bảng trái.
- Kết quả: Lòi ra ông đơn hàng 1005 (ID 99).
- Ý nghĩa: Debug lỗi hệ thống. Tự nhiên có đơn hàng mà check ID khách lại không tồn tại -> Lỗi phần mềm hoặc nhập liệu sai -> Báo IT sửa gấp.

----> Rất là nhiều NULLLLLLL, lỗi khi data type chưa phải là text (phần này thì nhìn chung sẽ không có vấn đề gì)