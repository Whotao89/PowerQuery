# Ghi chú thực hành Power Query - Tuần 1

Tình huống: Cột "Doanh thu" trong file CSV bị dính ký tự lạ, ví dụ: `12.000.000 đ` hoặc `$ 500`.
Nhiệm vụ Power Query: Hãy tìm cách chuyển cột đó về dạng số (Number) sạch sẽ (`12000000` hoặc `500`) chỉ bằng chuột, sao cho lần sau dữ liệu mới vào vẫn tự động sửa được.

---

### Các bước clean data (chỉ sử dụng tool):

#### (1) Xử lí cột “Doanh thu”
- Như có thể thấy, data đang không có đồng bộ. Ở phần doanh thu thừa các kí tự như: `đ`, `$`, `VND`, `USD`, và các khoảng trắng.
- Sử dụng **“Replace Values”** để lần lượt loại bỏ các kí thừa trên.
- **Change Type** -> chọn **“Decimal Number”** hoặc **“Currency”** cho cột “Doanh_Thu” để đảm bảo kiểu dữ liệu sau khi được làm sạch (ban đầu đang là text).

#### (2) Định dạng lại cột “Ngay_Giao_Dich”
- Vì định dạng chuẩn của Date trong Power Query là “DD/MM/YY”. Nên đổi hết kí tự ‘-’ thành ‘/’. Sau đó chọn Data Type thành Date là ok. 
- Ê không phải, việc Data format bị error là do engine chọn 15 làm tháng à đề xuất: format tay :v, do dữ liệu cũng chưa chuẩn khu vực lắm.
- à Đổi **Data Type** thành **Date** || **Change Type** -> **Using Locale** -> Chọn **Vietnamese**.

**Xài tool cho một bài tập đơn giản nên khá dế.**