# nội dung lab 2
<!-- PHẦN I:

Bài 1: Làm việc với chuỗi - kiểm tra từ "con người", trích xuất chuỗi con, chuyển đổi chữ hoa
Bài 2: Thao tác với chuỗi - thay thế từ "bình an" thành "hạnh phúc", ghép thêm ký tự vào đầu và cuối

PHẦN II:

Bài 3: Giải phương trình bậc nhất (ax + b = 0) với hướng dẫn chi tiết về cách xử lý các trường hợp
Bài 4: Giải phương trình bậc hai (ax² + bx + c = 0) với hướng dẫn tính delta và biện luận nghiệm
Bài 5,6hưa có nội dung chi tiết (có ghi "Giảng viên cho thêm") -->

# hướng dẫn và code mẫu
<!-- PHẦN I: BÀI TÂP VỀ CHUỖI
Bài 1: Thao tác với chuỗi ký tự
Đề bài: Sử dụng 1 biến kiểu chuỗi để lưu câu thơ sau:
"Tình yêu là ánh sáng trong đêm tối
Là nguồn sức mạnh cho con tim
Tình yêu làm đời thêm ý nghĩa
Mang lại niềm vui cho tâm hồn"
Yêu cầu:

Kiểm tra từ "tình yêu" có trong chuỗi hay không
Trích xuất từ "con tim" từ chuỗi
Chuyển từ "tình yêu" thành chữ hoa

Code mẫu:
python# Bài 1: Thao tác với chuỗi
bai_tho = """Tình yêu là ánh sáng trong đêm tối
Là nguồn sức mạnh cho con tim
Tình yêu làm đời thêm ý nghĩa
Mang lại niềm vui cho tâm hồn"""

# Kiểm tra từ "tình yêu" có trong chuỗi
if "tình yêu" in bai_tho.lower():
    print("Từ 'tình yêu' có trong bài thơ")
else:
    print("Từ 'tình yêu' không có trong bài thơ")

# Trích xuất từ "con tim"
vi_tri_con_tim = bai_tho.find("con tim")
if vi_tri_con_tim != -1:
    tu_con_tim = bai_tho[vi_tri_con_tim:vi_tri_con_tim + 7]
    print(f"Từ được trích xuất: {tu_con_tim}")

# Chuyển từ "tình yêu" thành chữ hoa
bai_tho_chu_hoa = bai_tho.replace("tình yêu", "TÌNH YÊU")
bai_tho_chu_hoa = bai_tho_chu_hoa.replace("Tình yêu", "TÌNH YÊU")
print("Bài thơ sau khi chuyển chữ hoa:")
print(bai_tho_chu_hoa)
Bài 2: Thay thế và ghép chuỗi
Yêu cầu:

Thay thế từ "niềm vui" bằng từ "hạnh phúc"
Ghép thêm "★ " vào đầu và " ★" vào cuối
Xuất kết quả

Code mẫu:
python# Bài 2: Thay thế và ghép chuỗi
bai_tho_moi = bai_tho.replace("niềm vui", "hạnh phúc")
bai_tho_hoan_chinh = "★ " + bai_tho_moi + " ★"
print("Bài thơ sau khi chỉnh sửa:")
print(bai_tho_hoan_chinh)
PHẦN II: BÀI TẬP VỀ CẤU TRÚC ĐIỀU KHIỂN
Bài 3: Giải phương trình bậc nhất (ax + b = 0)
Code mẫu:
python# Bài 3: Giải phương trình bậc nhất
print("=== GIẢI PHƯƠNG TRÌNH BẬC NHẤT ax + b = 0 ===")
a = float(input("Nhập hệ số a: "))
b = float(input("Nhập hệ số b: "))

if a == 0:
    if b == 0:
        print("Phương trình có vô số nghiệm")
    else:
        print("Phương trình vô nghiệm")
else:
    x = -b / a
    print(f"Nghiệm của phương trình là: x = {x}")
Bài 4: Giải phương trình bậc hai (ax² + bx + c = 0)
Code mẫu:
pythonimport math

# Bài 4: Giải phương trình bậc hai
print("=== GIẢI PHƯƠNG TRÌNH BẬC HAI ax² + bx + c = 0 ===")
a = float(input("Nhập hệ số a: "))
b = float(input("Nhập hệ số b: "))
c = float(input("Nhập hệ số c: "))

if a == 0:
    # Trở thành phương trình bậc nhất
    if b == 0:
        if c == 0:
            print("Phương trình có vô số nghiệm")
        else:
            print("Phương trình vô nghiệm")
    else:
        x = -c / b
        print(f"Phương trình bậc nhất có nghiệm: x = {x}")
else:
    # Tính delta
    delta = b**2 - 4*a*c
    
    if delta < 0:
        print("Phương trình vô nghiệm")
    elif delta == 0:
        x = -b / (2*a)
        print(f"Phương trình có nghiệm kép: x = {x}")
    else:
        x1 = (-b + math.sqrt(delta)) / (2*a)
        x2 = (-b - math.sqrt(delta)) / (2*a)
        print(f"Phương trình có 2 nghiệm phân biệt:")
        print(f"x1 = {x1}")
        print(f"x2 = {x2}")
Bài 5: Tính điểm trung bình và xếp loại học lực
Đề bài: Nhập điểm 3 môn Toán, Lý, Hóa. Tính điểm trung bình và xếp loại học lực.
Code mẫu:
python# Bài 5: Tính điểm trung bình và xếp loại
print("=== TÍNH ĐIỂM TRUNG BÌNH VÀ XẾP LOẠI ===")
toan = float(input("Nhập điểm Toán: "))
ly = float(input("Nhập điểm Lý: "))
hoa = float(input("Nhập điểm Hóa: "))

diem_tb = (toan + ly + hoa) / 3
print(f"Điểm trung bình: {diem_tb:.2f}")

if diem_tb >= 9.0:
    xep_loai = "Xuất sắc"
elif diem_tb >= 8.0:
    xep_loai = "Giỏi"
elif diem_tb >= 6.5:
    xep_loai = "Khá"
elif diem_tb >= 5.0:
    xep_loai = "Trung bình"
else:
    xep_loai = "Yếu"

print(f"Xếp loại học lực: {xep_loai}")
Bài 6: Tìm số lớn nhất trong 3 số
Code mẫu:
python# Bài 6: Tìm số lớn nhất
print("=== TÌM SỐ LỚN NHẤT TRONG 3 SỐ ===")
a = float(input("Nhập số thứ nhất: "))
b = float(input("Nhập số thứ hai: "))
c = float(input("Nhập số thứ ba: "))

if a >= b and a >= c:
    max_num = a
elif b >= a and b >= c:
    max_num = b
else:
    max_num = c

print(f"Số lớn nhất là: {max_num}") -->