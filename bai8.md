

**Bài 8: Vá Lỗ Hổng Bảo Mật Cookie Bệnh Án Và Khắc Phục Lỗi Cache Thuốc Cũ** 

**1\. Tại sao mặc dù Server đã cập nhật file danh mục thuốc mới nhưng trình duyệt của bác sĩ vẫn hiển thị dữ liệu cũ? Giải thích cơ chế Browser Cache đang hoạt động trong tình huống này.**

Vì do cơ chế Browser Cache,  trình duyệt đã lưu file cũ, nên khi bấm F5 để tải lại, trình duyệt vẫn đọc lại file cũ từ máy thôi, không có lấy file mới, vì vậy mặc dù Server đã cập nhật file danh mục thuốc mới nhưng trình duyệt của bác sĩ vẫn hiển thị dữ liệu cũ.

**2\. Nếu một hacker nhúng được mã JavaScript độc hại vào trang web, hacker có thể đánh cắp chuỗi Token phiên đăng nhập carepulse\_doctor\_session bằng câu lệnh nào? Thiếu cờ HttpOnly và Secure sẽ gây ra hiểm họa Session Hijacking ra sao đối với hồ sơ bệnh án?**

- Lệnh hacker dùng: lệnh document.cookie.  
- Hậu quả khi thiếu cờ bảo mật:  
+ Thiếu HttpOnly: hacker dùng JavaScript độc hại đọc trực tiếp chuỗi Token phiên làm việc rồi gửi về máy chủ của chúng.  
+ Thiếu Secure: token truyền qua kết nối HTTP không mã hóa có thể bị kẻ gian nghe lén trên cùng mạng.  
+ Hậu quả (Session Hijacking): giả mạo phiên đăng nhập của bác sĩ để truy cập trái phép và sửa đổi đơn thuốc.

**3.Hướng dẫn bác sĩ thực hiện thao tác làm mới cưỡng bức (Hard Reload) bằng phím tắt để cập nhật danh mục thuốc ngay lập tức mà không cần xóa toàn bộ lịch sử duyệt web.**

- Nhấn Ctrl \+ Shift \+ R  hoặc Ctrl \+ F5 để buộc trình duyệt bỏ qua Cache cũ và tải lại phiên bản mới nhất trực tiếp từ Server.

**4\. Viết lại dòng lệnh phản hồi `Set-Cookie` chuẩn an ninh y tế, bổ sung đầy đủ các cờ bảo mật bắt buộc.**

- Set-Cookie: carepulse\_doctor\_session=TOKEN\_XYZ883921983; Domain=carepulse.vn; Path=/; Expires=Wed, 21 Oct 2026 07:00:00 GMT; HttpOnly; Secure; SameSite=Strict 

**5\. Nêu 3 bước kiểm tra Cookie và vô hiệu hóa Cache tạm thời trên Chrome DevTools F12 (Tab Application & Network).**

- B1: Nhấn F12 để mở DevTools trên trình duyệt.  
- B2: Kiểm tra Cookie: chuyển sang tab Application $\rightarrow$ chọn mục Cookies (bên trái) $\rightarrow$ chọn tên miền và kiểm tra xem hai cột HttpOnly và Secure đã có dấu tích chưa  
- B3: Vô hiệu hóa Cache: Chuyển sang tab Network $\rightarrow$ tích chọn ô Disable cache