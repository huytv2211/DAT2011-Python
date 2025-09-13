# Tóm tắc lab 6
<!-- MỤC TIÊU LAB 7

Xây dựng ứng dụng với nhiều lớp theo sự phân cấp thừa kế
Sử dụng lại những gì đã có ở lớp khác
Ghi đè phương thức ở lớp con

PHẦN I
Bài 1 (2 điểm): Hình học với kế thừa

Lớp ChuNhat:

Thuộc tính: rộng, dài
Phương thức: get_chu_vi(), get_dien_tich(), xuat()


Lớp Vuong: Kế thừa từ ChuNhat

Ghi đè phương thức xuat()
Constructor gọi constructor của ChuNhat với cạnh = dài = rộng


Nhập 2 hình chữ nhật và 1 hình vuông, xuất thông tin

Bài 2 (2 điểm): Lớp trừu tượng SinhVienPoly

Thuộc tính: họ tên, ngành
Phương thức trừu tượng: get_diem() (dùng pass)
Phương thức: get_hoc_luc(), xuat()
Phân loại học lực:

Yếu: < 5
Trung bình: 5-7
Khá: 7-8
Giỏi: 8-9
Xuất sắc: ≥ 9



PHẦN II
Bài 3 (2 điểm): Lớp con kế thừa

SinhVienIT: Kế thừa SinhVienPoly

Thuộc tính: điểm java, html, css
Ghi đè get_diem(): (2×java + html + css) / 4


SinhVienBiz: Kế thừa SinhVienPoly

Thuộc tính: điểm marketing, sales
Ghi đè get_diem(): (2×marketing + sales) / 3



Bài 4 (2 điểm): Chương trình quản lý sinh viên
Menu gồm:

Nhập danh sách sinh viên
Xuất thông tin danh sách sinh viên
Xuất danh sách sinh viên học lực giỏi
Sắp xếp theo điểm
Kết thúc

Bài 5: Chưa có nội dung
Lab này tập trung vào các khái niệm:

Inheritance (Kế thừa)
Method Overriding (Ghi đè phương thức)
Abstract Method (Phương thức trừu tượng)
Polymorphism (Đa hình) -->