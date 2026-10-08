BÁO CÁO PHÂN TÍCH LỖI VÀ TEST CASES
1. Phân tích nguyên nhân kỹ thuật

- Dòng lệnh gây lỗi: `const basePrice = bookingReservation.priceKey;`
- Nguyên nhân: Dot Notation tìm kiếm trực tiếp thuộc tính có tên là "priceKey" trong đối tượng. Vì đối tượng không có thuộc tính này nên JavaScript trả về `undefined`.
- Hệ quả: Các phép tính tiếp theo lấy `undefined` nhân và cộng số dẫn đến kết quả phụ thu và tổng tiền đều bị lỗi `NaN`.
- Khắc phục: Sử dụng Bracket Notation `bookingReservation[priceKey]` để lấy giá trị theo biến động.

2. Bảng Test Cases đối chứng

| Trường hợp kiểm thử | Dữ liệu đầu vào | Kết quả sai thực tế | Kết quả đúng mong đợi |
| --- | --- | --- | --- |
| Check-in sớm (9h) có phụ thu | roomPrice: 1500000, checkInHour: 9 | Phụ thu: NaN, Tổng: NaN | Phụ thu: 450000, Tổng: 1950000 |
| Check-in đúng giờ (14h) không phụ thu | roomPrice: 2000000, checkInHour: 14 | Phụ thu: undefined, Tổng: NaN | Phụ thu: 0, Tổng: 2000000 |