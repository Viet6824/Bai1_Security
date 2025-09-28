# BÀI TẬP MÔN: An toàn và bảo mật thông tin #

## THÔNG TIN CÁ NHÂN
#### Họ và tên: Nguyễn Đức Việt
#### Mã sinh viên: K225480106075
#### Lớp: K58KTP

## BÀI TẬP 1: ##

### TÌM HIỂU CÁC PHƯƠNG PHÁP MÃ HOÁ CỔ ĐIỂN ###
1. Caesar
2. Affine
3. Hoán vị
4. Vigenère
5. Playfair

**Với mỗi phương pháp, hãy tìm hiểu:**
1. Tên gọi
2. Thuật toán mã hoá, thuật toán giải mã
3. Không gian khóa
4. Cách phá mã (mà không cần khoá)
5. Cài đặt thuật toán mã hoá và giải mã bằng code C++ và bằng html+css+javascript

### CHÚ Ý ###
1. ĐƯỢC THAM KHẢO AI
2. KO ĐƯỢC CLONE BÀI BẠN KHÁC VỚI BẤT KỂ LÝ DO GÌ
3. Thời gian trên github ko fake được, mọi thay đổi đều lưu vết thời gian và nội dung sửa đổi.
4. mọi project đều phải có dấu ấn cá nhân (tự do sáng tạo dấu ấn cá nhân, ko có bất kỳ khuôn mẫu nào!)
5. deadline: 2025-09-28 (dấu thời gian sau ngày này là dead), cuối kì thầy sẽ tổng hợp link các repository này để chấm điểm.
6. mọi hình thức vi phạm, chỉ cần 1 lần: đều bị cấm thi, miễn thi lại.
### Bài làm
#### 1. Caesar Cipher
##### Tên gọi
Caesar Cipher (hay còn gọi là Shift Cipher) là một phương pháp mã hóa thay thế đơn giản, được đặt tên theo Julius Caesar, người được cho là đã sử dụng nó để bảo vệ thông điệp quân sự.
##### Thuật toán mã hoá
Văn bản gốc (plaintext) chỉ bao gồm chữ cái (thường là bảng chữ cái tiếng Anh 26 chữ, không phân biệt hoa/thường).  
Mỗi chữ cái trong plaintext được dịch chuyển về phía trước trong bảng chữ cái một số vị trí cố định k (key, thường từ 0 đến 25).  
Công thức: Để mã hóa chữ cái x (vị trí từ 0=A đến 25=Z), ciphertext y = (x + k) mod 26.  
Các ký tự không phải chữ cái giữ nguyên.
##### Thuật toán giải mã
Dịch chuyển ngược lại: y = (x - k) mod 26 (nếu kết quả âm, cộng thêm 26).  
Tương đương với mã hóa bằng key (26 - k).
##### Không gian khóa
Không gian khóa là 26 (các giá trị k từ 0 đến 25), vì dịch chuyển 26 tương đương với 0.
##### Cách phá mã (mà không cần khoá)
Phá bằng brute force: Thử tất cả 26 khóa có thể và kiểm tra ciphertext để tìm văn bản có ý nghĩa (dễ dàng vì không gian khóa nhỏ).  
Phân tích tần suất: Chữ cái phổ biến nhất trong ciphertext có thể là 'E' dịch chuyển, nhưng brute force thường đủ.
#### 2. Affine Cipher
##### Tên gọi
Affine Cipher là một loại mã hóa thay thế tuyến tính, mở rộng từ Caesar, sử dụng công thức toán học để biến đổi chữ cái.
##### Thuật toán mã hoá
Sử dụng hai khóa a và b (a phải nguyên tố cùng nhau với 26, tức gcd(a,26)=1; b từ 0-25).  
Công thức: y = (a * x + b) mod 26, nơi x là vị trí chữ cái (A=0, ..., Z=25).  
Các ký tự không phải chữ cái giữ nguyên.  
##### Thuật toán giải mã
Tìm nghịch đảo modular của a modulo 26 (a_inv sao cho (a * a_inv) mod 26 = 1).  
Công thức: x = a_inv * (y - b) mod 26 (nếu âm, cộng 26).
##### Không gian khóa
a có 12 giá trị khả dụng (phi(26)=12, các số coprime với 26: 1,3,5,7,9,11,15,17,19,21,23,25).  
b có 26 giá trị.  
Tổng không gian khóa: 12 * 26 = 312.
##### Cách phá mã (mà không cần khoá)
Brute force: Thử tất cả 312 khóa và kiểm tra văn bản có ý nghĩa.  
Phân tích tần suất: Giải hệ phương trình từ các chữ cái phổ biến (ví dụ, giả sử chữ cái phổ biến nhất là 'E', thứ hai là 'T'), giải cho a và b.
