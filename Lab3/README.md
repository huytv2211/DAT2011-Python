# tóm tắt nội dung lab 3

<!-- TÓM TẮT NỘI DUNG LAB 3: KIỂU DỮ LIỆU TẬP HỢP, CẤU TRÚC LẶP
MỤC TIÊU

Phân biệt và sử dụng các kiểu dữ liệu tập hợp
Sử dụng thành thạo các lệnh lặp và ngắt vòng lặp


PHẦN I: KIỂU DỮ LIỆU TẬP HỢP
Bài 1 (2 điểm): Thao tác với List

Nội dung: Làm việc với dãy số nguyên
Yêu cầu:

Sắp xếp tăng dần
Tìm phần tử nhỏ nhất
Tính trung bình các số chia hết cho 3


Kiến thức: sort(), vòng lặp for, toán tử %
Nâng cao: Sắp xếp giảm dần

Bài 2 (2 điểm): Thao tác với Dictionary

Nội dung: Quản lý thông tin sinh viên
Yêu cầu:

Nhập họ tên, điểm
Xuất thông tin kèm xếp loại học lực


Thang điểm: Yếu (<5), TB (5-6.9), Khá (7-7.9), Giỏi (8-8.9), Xuất sắc (≥9)
Nâng cao: Quản lý danh sách nhiều sinh viên


PHẦN II: CẤU TRÚC LẶP
Bài 3 (2 điểm): Kiểm tra số nguyên tố

Nội dung: Nhập số và kiểm tra tính nguyên tố
Thuật toán: Dùng vòng lặp while kiểm tra chia hết từ 2 đến n-1
Kỹ thuật: Sử dụng biến flag, lệnh break

Bài 4 (2 điểm): Bảng cửu chương

Nội dung: Xuất bảng cửu chương 1-9
Kỹ thuật: Vòng lặp for lồng nhau
Định dạng: Sử dụng print với format string
Nâng cao: Xuất theo dạng bảng ngang

Bài 5: Giảng viên bổ sung

KIẾN THỨC CHÍNH
1. Kiểu dữ liệu tập hợp:

List: sort(), indexing, slicing
Dictionary: key-value pairs, truy xuất theo key

2. Cấu trúc lặp:

Vòng lặp for: duyệt list, range
Vòng lặp while: điều kiện lặp
Lệnh điều khiển: break, continue

3. Các hàm/phương thức:

sort(), min(), max()
range(), len()
Toán tử % (chia lấy dư)

4. Kỹ thuật lập trình:

Vòng lặp lồng nhau
Biến đếm, biến tổng
Biến flag để kiểm tra điều kiện

Lab này tập trung vào việc thao tác với các cấu trúc dữ liệu cơ bản và làm quen với các thuật toán đơn giản sử dụng vòng lặp. -->

# Hướng dẫn mẫu
<!-- KIỂU DỮ LIỆU TẬP HỢP VÀ CẤU TRÚC LẶP
PHẦN I: KIỂU DỮ LIỆU TẬP HỢP
Bài 1: Thao tác với danh sách điểm số
Đề bài: Viết chương trình thực hiện các thao tác sau với danh sách điểm thi của một lớp:

Sắp xếp theo thứ tự giảm dần và xuất ra màn hình
Xuất điểm cao nhất ra màn hình
Tính và xuất trung bình cộng các điểm >= 8.0

Code mẫu:
python# Bài 1: Thao tác với danh sách điểm số
diem_thi = [8.5, 6.2, 9.1, 7.8, 5.5, 8.9, 6.7, 9.5, 7.2, 8.3]
print("Danh sách điểm ban đầu:", diem_thi)

# Sắp xếp theo thứ tự giảm dần
diem_sap_xep = diem_thi.copy()
diem_sap_xep.sort(reverse=True)
print("Điểm sắp xếp giảm dần:", diem_sap_xep)

# Tìm điểm cao nhất
diem_cao_nhat = max(diem_thi)
print("Điểm cao nhất:", diem_cao_nhat)

# Tính trung bình các điểm >= 8.0
tong_diem_cao = 0
so_luong_diem_cao = 0

for diem in diem_thi:
    if diem >= 8.0:
        tong_diem_cao += diem
        so_luong_diem_cao += 1

if so_luong_diem_cao > 0:
    tb_diem_cao = tong_diem_cao / so_luong_diem_cao
    print(f"Các điểm >= 8.0: {[d for d in diem_thi if d >= 8.0]}")
    print(f"Trung bình các điểm >= 8.0: {tb_diem_cao:.2f}")
else:
    print("Không có điểm nào >= 8.0")

# YÊU CẦU NÂNG CAO: Đếm số học sinh theo từng loại
yeu = len([d for d in diem_thi if d < 5])
tb = len([d for d in diem_thi if 5 <= d < 7])
kha = len([d for d in diem_thi if 7 <= d < 8])
gioi = len([d for d in diem_thi if 8 <= d < 9])
xuat_sac = len([d for d in diem_thi if d >= 9])

print(f"\nThống kê học lực:")
print(f"Yếu (<5): {yeu} học sinh")
print(f"Trung bình (5-6.9): {tb} học sinh") 
print(f"Khá (7-7.9): {kha} học sinh")
print(f"Giỏi (8-8.9): {gioi} học sinh")
print(f"Xuất sắc (>=9): {xuat_sac} học sinh")
Bài 2: Quản lý thông tin sản phẩm
Đề bài: Viết chương trình nhập thông tin sản phẩm gồm: tên, giá, số lượng. Xuất thông tin kèm phân loại giá:

Rẻ: giá < 100,000
Trung bình: 100,000 <= giá < 500,000
Đắt: 500,000 <= giá < 1,000,000
Cao cấp: giá >= 1,000,000

Code mẫu:
python# Bài 2: Quản lý thông tin sản phẩm
def phan_loai_gia(gia):
    if gia < 100000:
        return "Rẻ"
    elif gia < 500000:
        return "Trung bình"
    elif gia < 1000000:
        return "Đắt"
    else:
        return "Cao cấp"

# Nhập thông tin một sản phẩm
print("=== NHẬP THÔNG TIN SẢN PHẨM ===")
ten_sp = input("Tên sản phẩm: ")
gia = float(input("Giá sản phẩm: "))
so_luong = int(input("Số lượng: "))

# Tạo dictionary lưu thông tin
san_pham = {
    "ten": ten_sp,
    "gia": gia,
    "so_luong": so_luong,
    "phan_loai": phan_loai_gia(gia),
    "tong_gia_tri": gia * so_luong
}

# Xuất thông tin
print("\n=== THÔNG TIN SẢN PHẨM ===")
print(f"Tên sản phẩm: {san_pham['ten']}")
print(f"Giá: {san_pham['gia']:,.0f} VNĐ")
print(f"Số lượng: {san_pham['so_luong']}")
print(f"Phân loại: {san_pham['phan_loai']}")
print(f"Tổng giá trị: {san_pham['tong_gia_tri']:,.0f} VNĐ")

# YÊU CẦU NÂNG CAO: Quản lý nhiều sản phẩm
print("\n=== QUẢN LÝ KHO HÀNG ===")
kho_hang = []
so_luong_sp = int(input("Số lượng sản phẩm muốn nhập: "))

for i in range(so_luong_sp):
    print(f"\nSản phẩm thứ {i+1}:")
    ten = input("Tên: ")
    gia = float(input("Giá: "))
    sl = int(input("Số lượng: "))
    
    sp = {
        "ten": ten,
        "gia": gia,
        "so_luong": sl,
        "phan_loai": phan_loai_gia(gia),
        "tong_gia_tri": gia * sl
    }
    kho_hang.append(sp)

# Xuất danh sách và thống kê
print("\n=== DANH SÁCH KHO HÀNG ===")
tong_gia_tri_kho = 0
for i, sp in enumerate(kho_hang, 1):
    print(f"{i}. {sp['ten']} - {sp['gia']:,.0f} VNĐ x{sp['so_luong']} - {sp['phan_loai']}")
    tong_gia_tri_kho += sp['tong_gia_tri']

print(f"\nTổng giá trị kho hàng: {tong_gia_tri_kho:,.0f} VNĐ")
PHẦN II: CẤU TRÚC LẶP
Bài 3: Kiểm tra số hoàn hảo
Đề bài: Viết chương trình kiểm tra một số có phải là số hoàn hảo hay không (số hoàn hảo là số bằng tổng các ước số thực sự của nó, ví dụ: 6 = 1+2+3).
Code mẫu:
python# Bài 3: Kiểm tra số hoàn hảo
def kiem_tra_so_hoan_hao(n):
    if n <= 1:
        return False
    
    tong_uoc = 0
    uoc_so = []
    
    # Tìm tất cả ước số từ 1 đến n//2
    for i in range(1, n//2 + 1):
        if n % i == 0:
            tong_uoc += i
            uoc_so.append(i)
    
    return tong_uoc == n, uoc_so, tong_uoc

# Chương trình chính
print("=== KIỂM TRA SỐ HOÀN HẢO ===")
n = int(input("Nhập một số nguyên dương: "))

la_so_hoan_hao, cac_uoc, tong = kiem_tra_so_hoan_hao(n)

print(f"Các ước số thực sự của {n}: {cac_uoc}")
print(f"Tổng các ước số: {tong}")

if la_so_hoan_hao:
    print(f"{n} là số hoàn hảo")
else:
    print(f"{n} không là số hoàn hảo")

# Tìm các số hoàn hảo từ 1 đến n
print(f"\nCác số hoàn hảo từ 1 đến {n}:")
for i in range(1, n + 1):
    if kiem_tra_so_hoan_hao(i)[0]:
        print(i, end=" ")
print()

# Thông tin: Các số hoàn hảo đầu tiên là: 6, 28, 496, 8128...
Bài 4: Bảng lũy thừa
Đề bài: Viết chương trình xuất bảng lũy thừa từ 1^1 đến 9^9.
Code mẫu:
python# Bài 4: Bảng lũy thừa
import math

print("=== BẢNG LŨY THỪA ===")

# Cách 1: Xuất từng bảng riêng biệt
for co_so in range(1, 10):
    print(f"\nBảng lũy thừa của {co_so}:")
    for mu in range(1, 10):
        ket_qua = co_so ** mu
        print(f"{co_so}^{mu} = {ket_qua}")

print("\n" + "="*80)

# Cách 2: Xuất bảng lũy thừa dạng ngang
print("BẢNG LŨY THỪA DẠNG NGANG:")
print("="*100)

# In header
print("Mũ\\Cơ số", end="")
for co_so in range(1, 10):
    print(f"{co_so:>8}", end="")
print()

print("-" * 80)

# In từng hàng
for mu in range(1, 10):
    print(f"{mu:>8}", end="")
    for co_so in range(1, 10):
        ket_qua = co_so ** mu
        print(f"{ket_qua:>8}", end="")
    print()

print("\n" + "="*80)

# Cách 3: Bảng căn bậc hai (NÂNG CAO)
print("BẢNG CĂN BẬC HAI:")
print("-" * 40)
for i in range(1, 101, 10):  # Từ 1 đến 100, cách 10
    for j in range(i, min(i+10, 101)):
        can_bac_hai = math.sqrt(j)
        print(f"√{j:2} = {can_bac_hai:5.2f}", end="  ")
    print()
Bài 5: Trò chơi đoán số
Đề bài: Viết chương trình trò chơi đoán số từ 1-100. Máy tính tạo số ngẫu nhiên, người dùng đoán, chương trình gợi ý "lớn hơn" hoặc "nhỏ hơn".
Code mẫu:
python# Bài 5: Trò chơi đoán số
import random

def choi_doan_so():
    print("=== TRÒ CHƠI ĐOÁN SỐ ===")
    print("Tôi đã nghĩ ra một số từ 1 đến 100. Hãy đoán xem!")
    
    so_bi_mat = random.randint(1, 100)
    so_lan_doan = 0
    max_lan_doan = 7  # Giới hạn số lần đoán
    
    while so_lan_doan < max_lan_doan:
        try:
            so_doan = int(input(f"\nLần đoán {so_lan_doan + 1}/{max_lan_doan}: "))
            so_lan_doan += 1
            
            if so_doan == so_bi_mat:
                print(f"🎉 Chúc mừng! Bạn đã đoán đúng số {so_bi_mat}")
                print(f"Bạn đã đoán đúng sau {so_lan_doan} lần!")
                return True
            elif so_doan < so_bi_mat:
                print("📈 Số bạn đoán nhỏ hơn số tôi nghĩ!")
            else:
                print("📉 Số bạn đoán lớn hơn số tôi nghĩ!")
                
        except ValueError:
            print("❌ Vui lòng nhập một số nguyên hợp lệ!")
            so_lan_doan -= 1  # Không tính lần nhập sai
    
    print(f"\n😞 Hết lượt đoán! Số tôi nghĩ là: {so_bi_mat}")
    return False

# Chương trình chính
diem_so = 0
tong_game = 0

while True:
    tong_game += 1
    print(f"\n🎮 GAME THỨ {tong_game}")
    
    if choi_doan_so():
        diem_so += 1
    
    print(f"\nTỷ số hiện tại: {diem_so}/{tong_game}")
    
    choi_tiep = input("\nBạn có muốn chơi tiếp không? (y/n): ").lower()
    if choi_tiep != 'y':
        break

print(f"\n🏆 KẾT QUẢ CUỐI GAME:")
print(f"Số game thắng: {diem_so}/{tong_game}")
if tong_game > 0:
    ty_le = (diem_so / tong_game) * 100
    print(f"Tỷ lệ thắng: {ty_le:.1f}%")
print("Cảm ơn bạn đã chơi!")
Bài 6: Tính dãy Fibonacci
Đề bài: Viết chương trình in ra n số đầu tiên của dãy Fibonacci và kiểm tra một số có thuộc dãy Fibonacci hay không.
Code mẫu:
python# Bài 6: Dãy Fibonacci
def tao_day_fibonacci(n):
    """Tạo danh sách n số Fibonacci đầu tiên"""
    if n <= 0:
        return []
    elif n == 1:
        return [0]
    elif n == 2:
        return [0, 1]
    
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i-1] + fib[i-2])
    
    return fib

def kiem_tra_fibonacci(so):
    """Kiểm tra một số có thuộc dãy Fibonacci không"""
    if so < 0:
        return False
    
    a, b = 0, 1
    if so == a or so == b:
        return True
    
    while b < so:
        a, b = b, a + b
    
    return b == so

# Chương trình chính
print("=== DÃY FIBONACCI ===")

# In ra n số Fibonacci đầu tiên
n = int(input("Nhập số lượng số Fibonacci muốn in: "))
day_fib = tao_day_fibonacci(n)
print(f"{n} số Fibonacci đầu tiên:")
print(day_fib)

# Tính tổng các số Fibonacci
tong_fib = sum(day_fib)
print(f"Tổng {n} số Fibonacci đầu tiên: {tong_fib}")

# Kiểm tra số có thuộc dãy Fibonacci không
print("\n=== KIỂM TRA SỐ FIBONACCI ===")
while True:
    try:
        so_kiem_tra = int(input("Nhập số muốn kiểm tra (0 để thoát): "))
        if so_kiem_tra == 0:
            break
            
        if kiem_tra_fibonacci(so_kiem_tra):
            print(f"{so_kiem_tra} thuộc dãy Fibonacci ✓")
        else:
            print(f"{so_kiem_tra} không thuộc dãy Fibonacci ✗")
            
    except ValueError:
        print("Vui lòng nhập số nguyên hợp lệ!")

print("Cảm ơn bạn đã sử dụng chương trình!")
Các bài tập này bao phủ đầy đủ các kiến thức trong Lab 3:

List: sort, min/max, filtering
Dictionary: lưu trữ thông tin có cấu trúc
Vòng lặp: for, while, nested loops
Thuật toán: tìm kiếm, kiểm tra điều kiện
Xử lý ngoại lệ: try-except
Random: tạo số ngẫu nhiên -->