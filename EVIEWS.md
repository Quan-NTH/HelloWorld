# HelloWorld
Dự án mới

-Hướng dẫn cách chạy EVIEWS

**CÂU HỎI: ĐIỀU TRA MẪU KÍCH THƯỚC N=10, NGƯỜI TA THU ĐƯỢC CÁCH SỐ LIỆU SAU ĐÂY**

  Xi: 20 18 17 17 16 15 13 12
  ---
  Yi: 8 7 8 8 6 6 5 5 4 3 
  ---
  Zi: 2 3 4 4 5 5 6 7 8 8 
  --- 
  Yi: Thu nhập hằng năm của một nhân viên (triệu đồng)
  
  Xi: Thâm niên công tác (năm)
  
  Zi: Thời gian đào tạo

 **1.Bằng phương pháp OLS xây dựng hàm hội quy mẫu Yi^ =B1^+B2^Xi+B3^Zi**

**Và nêu ý nghĩa các hệ số hồi quy B2^, B3^**

-Nhập lệnh 

    ls y c x z

-Ta có bảng sau

![image](https://github.com/user-attachments/assets/4dfbde22-117a-435f-8896-d60dde2acb3b)

Yi^=14.99215 + 0.761780Xi - 0.589005Zi

-B2^ = 0.761780: Khi thâm niên công tác tăng thêm 1 năm và thời gian đào tạo không đổi thì thu nhập hàng năm của một nhân viên trung bình tăng 0.761780 triệu đồng

-B3^ = 0.589005: Khi thâm niên công tác không đổi và thời gian đào tạo tăng thêm 1 đơn vị thì thu nhập hằng năm của một nhân viên trung bình giảm 0.589005 triệu đồng

**2.Với mức ý nghĩa alpha=1%, kiểm định giả thuyết: thời gian đào tạo không ảnh hưởng tới thu nhập tiền lương của nhân viên**

Kiểm định giả thuyết:

                      H0: B3 = 0: thời gian đào tạo không ảnh hưởng đến thu nhập
                      H1: B3 =! 0 : thời gian đào tạo có ảnh hưởng đến thu nhập

-Tiêu chuẩn kiểm định: T= (B3^-0)/se(b3^),H0 đúng

-Tìm Tqs tương ứng với t-statistics = -2.408105

![image](https://github.com/user-attachments/assets/b94c7e25-4568-4ac7-8cf0-d2f51b3bad3b)

-Ta có T^(n-k) (alpha/2) = T^(10-3) (0.01/2) = T7 0.005 = 3.499 (đề cho)

-Tìm miền bác bỏ W0.01 = {|Tqs|>T7 0.05} ( nếu Tqs>T7 0.005 thì Tqs thuộc miền bác bỏ, ta bác bỏ H0)

Mà Tqs < T7 0.005

-->Tqs không thuộc miền bác bỏ W0.01 

-->Chấp nhận H0

Vậy với mức ý nghĩa 1% thì thời gian đào tạo không ảnh hưởng đến tiền lương của nhân viên

**3.Xác định khoảng tin cậy 95% của B2**

-Nhấp trỏ chuột vào: Views --> Coefficient Diagnostics --> Confidence Intervals, ta được:

![image](https://github.com/user-attachments/assets/b3949c64-47cf-4c4e-ab81-cd0486e908a7)

Vậy khoảng tin cậy của B2 là (0.091555; 1.432005)

**4.Với mức ý nghĩa 1%, kiểm định giả thuyết cả 2 yếu tố thâm niên công tác và thời gian đào tạo đều không ảnh hưởng tới thu nhập tiền lương**

Kiểm định giả thuyết:

                      H0: B2 = B3 = 0: cả 2 yếu tố đều không ảnh hưởng đến thu nhập
                      H1: Tồn tại ít nhất 1 hệ số B =! 0

-Xây dựng tiêu chuẩn kiếm định: F=(R^2/(1-R^2))*((n-k)/(k-1)), H0 đúng F xấp xỉ F(2; 7) 

-Tìm miền bác bỏ: W0.01 = {ftn:ftn>F(k-1, n-k) alpha} 

_(nếu ftn>F(k-1, n-k) alpha thì bác bỏ H0, chấp nhận H1_
 
 _nếu ftn<F(k-1, n-k) alpha thì chấp nhận H0, bác bỏ H1)_

-Ta có F(k-1, n-k) alpha = F(2;7) 0.01 = 9.55 (tra trong bảng đề bài sẽ cho)

-Ta có ftn = F-statistics = 86.09278

![image](https://github.com/user-attachments/assets/b3d488de-e0e2-478e-bfc0-39c67d7fefa7)


Ta có ftn>F(k-1, n-k) alpha (86.09278 > 9.55)

--> Bác bỏ H0, chấp nhận H1

Vậy tồn tại ít nhất 1 trong 2 yếu tố ảnh hưởng đến thu nhập tiền lương

**5.Với độ tin cậy 98%, dự báo giá trị trung bình của Y khi X=6 và Z=4**

![image](https://github.com/user-attachments/assets/14fcbc18-0c19-4d9b-b128-47feec6a85c6)

-Nhấp đúp chuột trái vào range

-Thay đổi Observations từ 10 đổi thành 11

-Mở đồng thời 3 biến x,y,z và nhập số liệu X=6 và Z=4 (Nhấn phím shift chọn y, x, z --> Open --> As group --> Edit +/-)

![image](https://github.com/user-attachments/assets/ff98e0d3-227e-4dfc-af4c-443aa45404c3) ![image](https://github.com/user-attachments/assets/825992cd-7bdf-4bc2-9e7d-035f6a9e4754)

-Nhập lệnh: ls y c x z để chạy lại mô hình (sau khi chạy lại sẽ hiển thị dòng chữ 10 after adjustment)

![image](https://github.com/user-attachments/assets/d46503c6-67b0-43c1-9ca2-e9f212b16ca7)

-Ấn vào nhóm lệnh Forecast 

    Trong ô Forecast name: nhập ymu
    
    Trong ô S.E. (optional): nhập se

-Nhấn OK

![image](https://github.com/user-attachments/assets/77211241-ab3c-4eca-8a8d-cd06d3be0935)

-Chọn Quick --> Generate series

    Trong ô Enter equation, nhập: se0=sqr(se^2 - 0.571382^2)
    
    Chọn OK

    (0.571382 ta lấy ở phần S.E. of regression)

![image](https://github.com/user-attachments/assets/9b0e2ab4-a0ca-4b1b-85fb-99429f264a6f)

-Nhấp vào ô lệnh command:

    genr cabiettren=ymu+se0*2.998

    genr cabietduoi=ymu-se0*2.998
 
(T((n-k) alpha/2) = T(7 0.001) = 2.998)

-Nhấn enter để tạo cabiettren và cabietduoi

-Mở cả 2 phần cabiettren và cabietduoi, ta sẽ thu được giá trị trung bình của Y nằm trong khoảng (16.17349; 18.24012)

![image](https://github.com/user-attachments/assets/83c152aa-f154-44aa-8e96-56dafe8334f2)

Vậy với độ tin cậy 98%, thâm niên công tác là 6 năm và thời gian đào tạo là 4 đơn vị thời gian thì thu nhập trung bình của người lao động sẽ dao động trong khoảng từ 16.17349 triệu đồng đến 18.24012 triệu đồng











