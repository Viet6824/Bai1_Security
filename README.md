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
##### Demo
Hình ảnh giao diện  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/28d311da-fe7f-4416-9381-39c0806f7f2a" />
Demo  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/96615dd9-80d4-45d4-8491-f47b044cf9c3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5abc789b-1c78-499f-9ae6-6ae2d7730c34" />
Demo C++
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/48a6f314-5214-47bb-830c-b6a00e9828a1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/612ed985-8be1-40c2-be2f-2790a250f3ff" />  
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
##### Demo
Demo 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b11f3b42-fbce-4005-b89c-190f31bb85ad" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dcfeca26-8c29-4aca-a2a8-77d6f7af6f93" />
Demo c++
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b150d481-dccb-40cc-97e9-3443ac9d20b1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/858767b9-171f-4ee3-b6db-c15823060930" />
#### 3. Hoán vị
##### Tên gọi
Hoán vị Cipher (hay Transposition Cipher) là phương pháp mã hóa bằng cách sắp xếp lại thứ tự các chữ cái theo một quy tắc permutation (hoán vị), thường là columnar transposition để dễ triển khai.
##### Thuật toán mã hoá
Khóa là một từ hoặc số xác định thứ tự cột (ví dụ, khóa "KEY" → thứ tự cột dựa trên thứ tự chữ cái: K=11, E=5, Y=25 → cột 2,1,3).  
Viết plaintext vào lưới theo hàng (số cột = độ dài khóa), bỏ qua khoảng trắng hoặc thêm filler (như 'X').  
Đọc ciphertext theo thứ tự cột đã sắp xếp.
##### Thuật toán giải mã
Sắp xếp lại lưới theo thứ tự cột khóa, viết ciphertext vào theo cột đã sắp xếp, đọc theo hàng.
##### Không gian khóa
Đối với khóa độ dài n, không gian là n! (giai thừa của n), nhưng thực tế phụ thuộc vào cách tạo khóa (thường từ từ khóa, giảm không gian nếu từ ngắn lặp).
##### Cách phá mã (mà không cần khoá)
Anagramming: Sắp xếp lại các nhóm chữ để tìm từ có ý nghĩa (dùng cho văn bản ngắn).  
Phân tích mẫu: Ước lượng độ dài khóa bằng cách tìm khoảng cách lặp lại, sau đó thử các permutation.
##### Demo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d948526-d6a2-4299-a0d8-65af5b25bbc2" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2fbb0d48-fca9-4808-b51c-08ef5f600a9e" />
Demo C++
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/34856a8b-a944-406b-bc81-b097dab2481d" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a1666a3e-ba22-4fe0-8af7-71767a37a076" />

#### 4. Vigenere Cipher
##### Tên gọi
Vigenère Cipher là một phương pháp mã hóa đa bảng chữ cái (polyalphabetic), được phát triển bởi Blaise de Vigenère vào thế kỷ 16.
##### Thuật toán mã hoá
Khóa là một từ lặp lại (ví dụ, "KEY" lặp thành "KEYKEY..." để khớp độ dài plaintext).  
Mỗi chữ cái plaintext được mã hóa bằng Caesar shift tương ứng với chữ cái khóa (A=0, B=1, ..., Z=25).  
Công thức: y_i = (x_i + k_i) mod 26.
##### Thuật toán giải mã
y_i = (x_i - k_i) mod 26 (cộng 26 nếu âm).
##### Không gian khóa
Phụ thuộc độ dài khóa m: 26^m (rất lớn nếu m dài, nhưng thực tế khóa ngắn làm giảm an toàn).
##### Cách phá mã (mà không cần khoá)
Kasiski examination: Tìm độ dài khóa bằng cách tìm khoảng cách giữa các chuỗi lặp trong ciphertext.  
Friedman test: Ước lượng độ dài khóa qua chỉ số trùng hợp (Index of Coincidence).  
Sau khi có độ dài, phân tích tần suất từng nhóm để tìm shift.  
##### Demo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ad5bb56e-7b9e-44c2-a9d6-49f82022e6a8" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cba2bd6c-9907-4f76-ac83-c3a43b0766ae" />  
Demo C++
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/97901411-ffe5-49c0-a934-175c15bb5f05" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1eacdfa0-e9da-4268-8197-4ebfb3be00c6" /> 

#### 5. Playfair Cipher
##### Tên gọi
Playfair Cipher là một phương pháp mã hóa digram (cặp chữ cái), sử dụng lưới 5x5, được phát triển bởi Charles Wheatstone nhưng phổ biến nhờ Lord Playfair.
##### Thuật toán mã hoá
Tạo lưới 5x5 từ khóa (loại bỏ trùng lặp, kết hợp I/J, thêm chữ cái còn lại theo thứ tự).  
Plaintext được chia thành cặp (thêm 'X' nếu lẻ, thay 'J' bằng 'I', loại khoảng trắng).  
Quy tắc: Nếu cùng hàng → dịch phải; cùng cột → dịch xuống; khác → thay bằng góc chữ nhật (giữ thứ tự).
##### Thuật toán giải mã
Tương tự nhưng dịch ngược: trái cho hàng, lên cho cột; góc chữ nhật giữ nguyên.
##### Không gian khóa
Khoảng 25! / 2 (vì I/J kết hợp, nhưng thực tế nhỏ hơn vì khóa tạo lưới, khoảng 10^25 nhưng dễ đoán nếu khóa ngắn).
##### Cách phá mã (mà không cần khoá)
Phân tích tần suất digram: Các cặp phổ biến như 'TH', 'HE' giúp đoán lưới.  
Hill climbing hoặc genetic algorithms để thử lưới; brute force không khả thi nhưng với văn bản dài có thể.
##### Demo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/71157d5a-b08a-4b6c-b3f5-4ccd4acd24ca" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c645056e-6ec1-40a8-bde2-b5c0afa4a850" />
Demo C++
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7936edf5-f320-4f91-b0bf-3f75b718a00a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5dd7e6ee-fb99-4fd2-a8a3-41e4e7cb2641" />

