# BÀI TẬP ĐÁNH GIÁ KẾT THÚC HỌC PHẦN CÔNG NGHỆ PHẦN MỀM


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

## Bài 2: Thiết kế và cài đặt:

1. Phát hiện vấn đề và đề xuất giải pháp:

- Vấn đề 1:  Lớp BankStatement có thuộc tính fileFormat và phương thức parseFile(). Điều này vi phạm nguyên tắc Single Responsibility Principle (SRP) vì lớp BankStatement vừa chịu trách nhiệm lưu trữ dữ liệu vừa chịu trách nhiệm phân tích file.

- Giải pháp: Tách logic phân tích file sang một lớp riêng biệt, ví dụ BankStatementParser. Lớp này sẽ nhận vào filePath và fileFormat để thực hiện phân tích và trả về danh sách Transaction.
- Vấn đề 2:  Lớp TransactionParser có thuộc tính parserType để xác định loại file. Việc này tạo ra sự phụ thuộc giữa lớp TransactionParser và các định dạng file cụ thể.

- Giải pháp: Sử dụng Strategy Pattern để tạo ra các lớp con của TransactionParser (ví dụ: CSVTransactionParser, XMLTransactionParser, ExcelTransactionParser) và để lớp StatementAnalyzer lựa chọn lớp con phù hợp dựa trên định dạng file.
- Vấn đề 3:  Lớp Report có phương thức generate() và display().  Tương tự như vấn đề 1, điều này vi phạm nguyên tắc SRP.

- Giải pháp: Tách logic hiển thị (display) sang một lớp riêng biệt, ví dụ ReportRenderer. Lớp này sẽ nhận vào đối tượng Report và hiển thị dữ liệu theo yêu cầu (console, GUI, file...).

2. Biểu đồ lớp sau khi điều chỉnh:
![Diagram](https://www.planttext.com/plantuml/png/l5FBJkGm4BpdArgSPbO4E5i8yTgLa412349SU-9ci73ioDr136Y_R0_xIVm2SkoP9ComfnN7BfUxgiljzpz_ZramI5lRehB83AVedcQ2GZKvWRS2e0IZ5Sma6BVeoWTZwPSFDSe6V8toE08be6Ein7Z72YuDo-5j3nqL003FQ8r6eSbKmRCtklXTP3C3QhOIUGhEKIYLn5KmJIICPB7shHC5vxwTsqILPKCh3kplWwQvaLse0caZ7QD2eOKFoq4dM87cjRSNOSDtqNN4vjvRGXTT6oSK7h2YeVDh34oXym_Gn6BoEQhfjcZMAPpDxZRRcRgntHlnVzMwlxhyDgtrcfqujClNtAjClSAMTKcAQMamtPdmgeaQh-vKmGqrFaYlb-ei8bxGNhZArpHUauZ_V6d8yVYWNmITZrd15JQ7QTJTp8tkIa3dQxGcKluHG39qGqvJM2Uf3JSMbvFG7Qwc67oDyGyjooFOETZR-x4pV9jYCzj8p0aeM92ZW4By1N7pcHMqJBn5_4jg5kjrruDcmZ4vtTRs0m00__y30000)


