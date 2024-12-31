## Bài 1: Yêu cầu phần mềm.

### 1. Phân tích bài toán:
a)	Chức năng chính của hệ thống:
- Nhận file dữ liệu sao kê ngân hàng từ người dùng.
- Phân tích dữ liệu giao dịch trong file.
- Thống kê các thông tin từ dữ liệu giao dịch (ví dụ: tổng thu nhập, tổng chi tiêu, chi tiêu theo danh mục, các giao dịch bất thường...).
- Hiển thị kết quả thống kê cho người dùng.
- Lưu kết quả thống kê.

b) Các tác nhân liên quan:
- Người dùng (khách hàng)
- Hệ thống phân tích

### 2. Biểu đồ ca sử dụng:
![Diagram](https://www.planttext.com/plantuml/png/bCun2i8m6CNnFQTuTDB1EmWk3Y8E3gwXZMamJJNzCecpimTmKLm4qTLcS2XuZvp0AuWTL0G5zz__yMx-qYw8MtAPPbgC2PJ3AfaI4cL5J2etZCUKMqHzUJq5lrP8ghEH4NW1LmZB7emRgGMYRl1BK1hyoaXCqsfZGDKXJYFC6MgDLWkDZZCISIXtKuoL5YXuZacrRxwRaSWm2UM5C7EXt3vNFrtlUdA_O6Fmke4a-2Eq2dxfcdNzxN1T3bzB_vGBrXOcSPc-0m00__y30000)

### 3. Đặc tả ca sử dụng "Thống kê giao dịch ngân hàng":
- Tên ca sử dụng: Thống kê giao dịch ngân hàng
- Tác nhân tham gia: Người dùng
- Mô tả tóm tắt: Ca sử dụng này cho phép người dùng phân tích file sao kê ngân hàng và thống kê các thông tin giao dịch.
- Tiền điều kiện:
  - Người dùng đã cung cấp file sao kê ngân hàng hợp lệ.
  - Hệ thống đã phân tích thành công dữ liệu từ file.
- Luồng sự kiện chính:
  - Người dùng chọn chức năng "Thống kê giao dịch".
  - Hệ thống hiển thị các tùy chọn thống kê (ví dụ: tổng thu nhập, tổng chi tiêu, chi tiêu theo danh mục...).
  - Người dùng lựa chọn các tùy chọn thống kê mong muốn.
  - Hệ thống tính toán và hiển thị kết quả thống kê.
- Luồng sự kiện phụ:
  - Người dùng có thể chọn lưu kết quả thống kê.
  - Hệ thống hiển thị hộp thoại cho phép người dùng chọn vị trí lưu và định dạng file.
  - Người dùng chọn vị trí lưu và định dạng file.
  - Hệ thống lưu kết quả thống kê.
- Kết quả mong muốn:
  - Kết quả thống kê được hiển thị cho người dùng.
  - (Nếu người dùng chọn lưu) Kết quả thống kê được lưu vào vị trí do người dùng chỉ định.
 
### 4. Yêu cầu phi chức năng:
- Hiệu năng: Hệ thống cần phải phân tích và thống kê dữ liệu trong một khoảng thời gian hợp lý, không gây ra hiện tượng "treo" hoặc "lag". Ví dụ, hệ thống cần phải xử lý được file sao kê có chứa 10,000 giao dịch trong vòng 1 phút.

## Bài 2: Thiết kế và cài đặt
