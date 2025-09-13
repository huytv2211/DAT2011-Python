# Tóm tắt nội dung lab 4
<!-- TÓM TẮT LAB 4: MÔ-ĐUN VÀ HÀMMỤC TIÊU

Tạo và gọi hàm với tham số
Sử dụng hàm lambda
Tạo và sử dụng mô-đun
Tổ chức chương trình với menu
Quản lý ngoại lệ
NỘI DUNG CHÍNHBài 1: Tính tiền nước theo phương pháp lũy tiến (4 bậc giá)
Bài 2: Tính nguyên liệu làm bánh (3 loại bánh, 2 nguyên liệu)
Bài 3: Lọc số chẵn bằng hàm lambda
Bài 4: Tổ chức menu gọi các chức năng -->

# bài tập mẫu
<!-- TÓM TẮT LAB 4: MÔ-ĐUN VÀ HÀM
MỤC TIÊU
Tạo và gọi hàm với tham số
Sử dụng hàm lambda
Tạo và sử dụng mô-đun
Tổ chức chương trình với menu
Quản lý ngoại lệ
NỘI DUNG CHÍNH
Bài 1: Tính tiền nước theo phương pháp lũy tiến (4 bậc giá) Bài 2: Tính nguyên liệu làm bánh (3 loại bánh, 2 nguyên liệu)
Bài 3: Lọc số chẵn bằng hàm lambda Bài 4: Tổ chức menu gọi các chức năng

BÀI TẬP TƯƠNG TỰ LAB 4
PHẦN I: HÀM VÀ THAM SỐ
Bài 1: Tính tiền điện theo bậc thang
Đề bài: Viết hàm tính tiền điện sinh hoạt theo 5 bậc giá lũy tiến.

Code mẫu:

python
# Bài 1: Tính tiền điện theo bậc thang
def tinh_tien_dien(so_kwh):
    """
    Tính tiền điện theo bậc thang
    Bậc 1: 0-50 kWh: 1.900đ/kWh
    Bậc 2: 51-100 kWh: 2.000đ/kWh  
    Bậc 3: 101-200 kWh: 2.400đ/kWh
    Bậc 4: 201-300 kWh: 2.900đ/kWh
    Bậc 5: >300 kWh: 3.200đ/kWh
    """
    gia_dien = (1900, 2000, 2400, 2900, 3200)
    moc = (50, 100, 200, 300)
    
    if so_kwh <= 0:
        return 0
    
    tien_dien = 0
    
    if so_kwh <= moc[0]:  # <= 50
        tien_dien = so_kwh * gia_dien[0]
    elif so_kwh <= moc[1]:  # 51-100
        tien_dien = moc[0] * gia_dien[0] + (so_kwh - moc[0]) * gia_dien[1]
    elif so_kwh <= moc[2]:  # 101-200
        tien_dien = (moc[0] * gia_dien[0] + 
                    (moc[1] - moc[0]) * gia_dien[1] + 
                    (so_kwh - moc[1]) * gia_dien[2])
    elif so_kwh <= moc[3]:  # 201-300
        tien_dien = (moc[0] * gia_dien[0] + 
                    (moc[1] - moc[0]) * gia_dien[1] + 
                    (moc[2] - moc[1]) * gia_dien[2] + 
                    (so_kwh - moc[2]) * gia_dien[3])
    else:  # > 300
        tien_dien = (moc[0] * gia_dien[0] + 
                    (moc[1] - moc[0]) * gia_dien[1] + 
                    (moc[2] - moc[1]) * gia_dien[2] + 
                    (moc[3] - moc[2]) * gia_dien[3] + 
                    (so_kwh - moc[3]) * gia_dien[4])
    
    return tien_dien

# Test hàm
if __name__ == "__main__":
    print("=== TÍNH TIỀN ĐIỆN ===")
    cac_truong_hop = [45, 75, 150, 250, 350]
    
    for kwh in cac_truong_hop:
        tien = tinh_tien_dien(kwh)
        print(f"Sử dụng {kwh} kWh: {tien:,.0f} VNĐ")
    
    # Nhập từ người dùng
    try:
        so_kwh = float(input("\nNhập số kWh sử dụng: "))
        tien = tinh_tien_dien(so_kwh)
        print(f"Tiền điện phải trả: {tien:,.0f} VNĐ")
    except ValueError:
        print("Vui lòng nhập số hợp lệ!")
Bài 2: Tính chi phí sản xuất pizza
Đề bài: Viết hàm tính nguyên liệu cần thiết để làm pizza với 3 loại: Margherita, Pepperoni, Hawaiian.

Code mẫu:

python
# Bài 2: Tính chi phí sản xuất pizza
def tinh_nguyen_lieu_pizza(*args, **kwargs):
    """
    Tính nguyên liệu cần thiết để làm pizza
    Args: margherita, pepperoni, hawaiian (số lượng từng loại)
    Hoặc kwargs: margherita=x, pepperoni=y, hawaiian=z
    """
    # Nguyên liệu cho mỗi loại pizza (kg)
    nguyen_lieu_pizza = {
        'margherita': {'bot': 0.2, 'pho_mai': 0.15, 'ca_chua': 0.1},
        'pepperoni': {'bot': 0.2, 'pho_mai': 0.2, 'thit': 0.1}, 
        'hawaiian': {'bot': 0.2, 'pho_mai': 0.15, 'dua_hau': 0.08}
    }
    
    # Xử lý tham số
    if args:
        margherita, pepperoni, hawaiian = args[0], args[1] if len(args) > 1 else 0, args[2] if len(args) > 2 else 0
    else:
        margherita = kwargs.get('margherita', 0)
        pepperoni = kwargs.get('pepperoni', 0) 
        hawaiian = kwargs.get('hawaiian', 0)
    
    # Tính tổng nguyên liệu
    tong_nguyen_lieu = {
        'bot': 0,
        'pho_mai': 0,
        'ca_chua': 0,
        'thit': 0,
        'dua_hau': 0
    }
    
    # Tính cho từng loại pizza
    pizza_count = {'margherita': margherita, 'pepperoni': pepperoni, 'hawaiian': hawaiian}
    
    for loai_pizza, so_luong in pizza_count.items():
        if so_luong > 0:
            for nguyen_lieu, luong in nguyen_lieu_pizza[loai_pizza].items():
                if nguyen_lieu in tong_nguyen_lieu:
                    tong_nguyen_lieu[nguyen_lieu] += luong * so_luong
    
    # Lọc bỏ nguyên liệu không sử dụng
    ket_qua = {k: v for k, v in tong_nguyen_lieu.items() if v > 0}
    
    return ket_qua

# Test hàm
if __name__ == "__main__":
    print("=== TÍNH NGUYÊN LIỆU PIZZA ===")
    
    # Test với args
    print("Đơn hàng 1: 5 Margherita, 3 Pepperoni, 2 Hawaiian")
    nguyen_lieu_1 = tinh_nguyen_lieu_pizza(5, 3, 2)
    print("Nguyên liệu cần:")
    for nl, luong in nguyen_lieu_1.items():
        print(f"  {nl.replace('_', ' ').title()}: {luong:.2f} kg")
    
    # Test với kwargs
    print("\nĐơn hàng 2:")
    nguyen_lieu_2 = tinh_nguyen_lieu_pizza(margherita=10, hawaiian=5)
    print("Nguyên liệu cần:")
    for nl, luong in nguyen_lieu_2.items():
        print(f"  {nl.replace('_', ' ').title()}: {luong:.2f} kg")
    
    # Nhập từ người dùng
    print("\n=== NHẬP ĐỐN HÀNG ===")
    try:
        m = int(input("Số pizza Margherita: "))
        p = int(input("Số pizza Pepperoni: "))
        h = int(input("Số pizza Hawaiian: "))
        
        ket_qua = tinh_nguyen_lieu_pizza(m, p, h)
        print(f"\nNguyên liệu cần cho {m+p+h} pizza:")
        for nl, luong in ket_qua.items():
            print(f"  {nl.replace('_', ' ').title()}: {luong:.2f} kg")
            
    except ValueError:
        print("Vui lòng nhập số nguyên hợp lệ!")
PHẦN II: LAMBDA VÀ MENU
Bài 3: Lọc và xử lý danh sách bằng lambda
Đề bài: Sử dụng lambda để lọc và xử lý danh sách số.

Code mẫu:

python
# Bài 3: Lọc và xử lý danh sách bằng lambda
def nhap_day_so():
    """Nhập dãy số từ bàn phím với xử lý lỗi"""
    day_so = []
    print("Nhập các số nguyên (nhập 's' hoặc 'S' để dừng):")
    
    while True:
        try:
            nhap = input(f"Số thứ {len(day_so) + 1}: ").strip()
            
            if nhap.lower() == 's':
                break
            
            so = int(nhap)
            day_so.append(so)
            
        except ValueError:
            print("Lỗi: Vui lòng nhập số nguyên hợp lệ hoặc 's' để dừng!")
    
    return day_so

def xu_ly_day_so_voi_lambda(day_so):
    """Xử lý dãy số với các hàm lambda"""
    if not day_so:
        print("Danh sách rỗng!")
        return
    
    print(f"Dãy số gốc: {day_so}")
    
    # Lọc số chẵn
    so_chan = list(filter(lambda x: x % 2 == 0, day_so))
    print(f"Các số chẵn: {so_chan}")
    
    # Lọc số lẻ  
    so_le = list(filter(lambda x: x % 2 != 0, day_so))
    print(f"Các số lẻ: {so_le}")
    
    # Lọc số dương
    so_duong = list(filter(lambda x: x > 0, day_so))
    print(f"Các số dương: {so_duong}")
    
    # Lọc số âm
    so_am = list(filter(lambda x: x < 0, day_so))
    print(f"Các số âm: {so_am}")
    
    # Bình phương các số
    binh_phuong = list(map(lambda x: x**2, day_so))
    print(f"Bình phương: {binh_phuong}")
    
    # Lọc số chia hết cho 3
    chia_het_3 = list(filter(lambda x: x % 3 == 0, day_so))
    print(f"Số chia hết cho 3: {chia_het_3}")
    
    # Lọc số nguyên tố (đơn giản)
    def la_so_nguyen_to(n):
        if n < 2:
            return False
        for i in range(2, int(n**0.5) + 1):
            if n % i == 0:
                return False
        return True
    
    so_nguyen_to = list(filter(lambda x: la_so_nguyen_to(x), day_so))
    print(f"Các số nguyên tố: {so_nguyen_to}")

# Test bài 3
if __name__ == "__main__":
    print("=== XỬ LÝ DÃY SỐ VỚI LAMBDA ===")
    day_so = nhap_day_so()
    if day_so:
        xu_ly_day_so_voi_lambda(day_so)
    else:
        print("Không có số nào được nhập!")
Bài 4: Menu tích hợp các chức năng
Đề bài: Tạo menu tích hợp tất cả các chức năng đã viết.

Code mẫu:

python
# Bài 4: Menu chính - file: menu.py
# Import các module đã tạo
import sys
from typing import Dict, List

class QuanLyTienIch:
    """Lớp quản lý các tiện ích tính toán"""
    
    def __init__(self):
        self.running = True
    
    def tinh_tien_dien(self, so_kwh):
        """Tính tiền điện theo bậc thang"""
        gia_dien = (1900, 2000, 2400, 2900, 3200)
        moc = (50, 100, 200, 300)
        
        if so_kwh <= 0:
            return 0
        
        tien_dien = 0
        
        if so_kwh <= moc[0]:
            tien_dien = so_kwh * gia_dien[0]
        elif so_kwh <= moc[1]:
            tien_dien = moc[0] * gia_dien[0] + (so_kwh - moc[0]) * gia_dien[1]
        elif so_kwh <= moc[2]:
            tien_dien = (moc[0] * gia_dien[0] + 
                        (moc[1] - moc[0]) * gia_dien[1] + 
                        (so_kwh - moc[1]) * gia_dien[2])
        elif so_kwh <= moc[3]:
            tien_dien = (moc[0] * gia_dien[0] + 
                        (moc[1] - moc[0]) * gia_dien[1] + 
                        (moc[2] - moc[1]) * gia_dien[2] + 
                        (so_kwh - moc[2]) * gia_dien[3])
        else:
            tien_dien = (moc[0] * gia_dien[0] + 
                        (moc[1] - moc[0]) * gia_dien[1] + 
                        (moc[2] - moc[1]) * gia_dien[2] + 
                        (moc[3] - moc[2]) * gia_dien[3] + 
                        (so_kwh - moc[3]) * gia_dien[4])
        
        return tien_dien
    
    def tinh_nguyen_lieu_pizza(self, margherita=0, pepperoni=0, hawaiian=0):
        """Tính nguyên liệu làm pizza"""
        nguyen_lieu_pizza = {
            'margherita': {'bot': 0.2, 'pho_mai': 0.15, 'ca_chua': 0.1},
            'pepperoni': {'bot': 0.2, 'pho_mai': 0.2, 'thit': 0.1}, 
            'hawaiian': {'bot': 0.2, 'pho_mai': 0.15, 'dua_hau': 0.08}
        }
        
        tong_nguyen_lieu = {'bot': 0, 'pho_mai': 0, 'ca_chua': 0, 'thit': 0, 'dua_hau': 0}
        
        pizza_count = {'margherita': margherita, 'pepperoni': pepperoni, 'hawaiian': hawaiian}
        
        for loai_pizza, so_luong in pizza_count.items():
            if so_luong > 0:
                for nguyen_lieu, luong in nguyen_lieu_pizza[loai_pizza].items():
                    if nguyen_lieu in tong_nguyen_lieu:
                        tong_nguyen_lieu[nguyen_lieu] += luong * so_luong
        
        return {k: v for k, v in tong_nguyen_lieu.items() if v > 0}
    
    def xu_ly_day_so_lambda(self):
        """Xử lý dãy số với lambda"""
        day_so = []
        print("Nhập các số nguyên (nhập 's' để dừng):")
        
        while True:
            try:
                nhap = input(f"Số thứ {len(day_so) + 1}: ").strip()
                if nhap.lower() == 's':
                    break
                so = int(nhap)
                day_so.append(so)
            except ValueError:
                print("❌ Vui lòng nhập số nguyên hợp lệ!")
        
        if day_so:
            print(f"Dãy số: {day_so}")
            so_chan = list(filter(lambda x: x % 2 == 0, day_so))
            so_le = list(filter(lambda x: x % 2 != 0, day_so))
            binh_phuong = list(map(lambda x: x**2, day_so))
            
            print(f"Số chẵn: {so_chan}")
            print(f"Số lẻ: {so_le}")
            print(f"Bình phương: {binh_phuong}")
    
    def hien_thi_menu(self):
        """Hiển thị menu chính"""
        print("\n" + "="*50)
        print("🏪 HỆ THỐNG QUẢN LÝ TIỆN ÍCH")
        print("="*50)
        print("1. 💡 Tính tiền điện theo bậc thang")
        print("2. 🍕 Tính nguyên liệu làm pizza") 
        print("3. 🔢 Xử lý dãy số với Lambda")
        print("4. 🚪 Thoát chương trình")
        print("="*50)
    
    def chuc_nang_1(self):
        """Tính tiền điện"""
        print("\n🔌 TÍNH TIỀN ĐIỆN")
        print("-" * 30)
        try:
            so_kwh = float(input("Nhập số kWh điện sử dụng: "))
            if so_kwh < 0:
                print("❌ Số kWh không thể âm!")
                return
            
            tien = self.tinh_tien_dien(so_kwh)
            print(f"💰 Tiền điện phải trả: {tien:,.0f} VNĐ")
            
            # Hiển thị chi tiết bậc thang
            print("\n📊 Chi tiết bậc giá:")
            print("  Bậc 1 (0-50 kWh): 1.900 đ/kWh")
            print("  Bậc 2 (51-100 kWh): 2.000 đ/kWh")
            print("  Bậc 3 (101-200 kWh): 2.400 đ/kWh")
            print("  Bậc 4 (201-300 kWh): 2.900 đ/kWh")
            print("  Bậc 5 (>300 kWh): 3.200 đ/kWh")
            
        except ValueError:
            print("❌ Vui lòng nhập số hợp lệ!")
    
    def chuc_nang_2(self):
        """Tính nguyên liệu pizza"""
        print("\n🍕 TÍNH NGUYÊN LIỆU PIZZA")
        print("-" * 30)
        try:
            print("Nhập số lượng từng loại pizza:")
            margherita = int(input("🟢 Margherita: "))
            pepperoni = int(input("🔴 Pepperoni: "))
            hawaiian = int(input("🟡 Hawaiian: "))
            
            if margherita < 0 or pepperoni < 0 or hawaiian < 0:
                print("❌ Số lượng không thể âm!")
                return
            
            nguyen_lieu = self.tinh_nguyen_lieu_pizza(margherita, pepperoni, hawaiian)
            
            if nguyen_lieu:
                print(f"\n📦 Nguyên liệu cần cho {margherita + pepperoni + hawaiian} pizza:")
                for nl, luong in nguyen_lieu.items():
                    print(f"   {nl.replace('_', ' ').title()}: {luong:.2f} kg")
            else:
                print("❌ Không có pizza nào được đặt!")
                
        except ValueError:
            print("❌ Vui lòng nhập số nguyên hợp lệ!")
    
    def chuc_nang_3(self):
        """Xử lý dãy số với lambda"""
        print("\n🔢 XỬ LÝ DÃY SỐ VỚI LAMBDA")
        print("-" * 30)
        self.xu_ly_day_so_lambda()
    
    def chon_chuc_nang(self, lua_chon):
        """Xử lý lựa chọn menu"""
        cac_chuc_nang = {
            1: self.chuc_nang_1,
            2: self.chuc_nang_2, 
            3: self.chuc_nang_3,
            4: self.thoat_chuong_trinh
        }
        
        if lua_chon in cac_chuc_nang:
            cac_chuc_nang[lua_chon]()
        else:
            print("❌ Lựa chọn không hợp lệ! Vui lòng chọn 1-4.")
    
    def thoat_chuong_trinh(self):
        """Thoát chương trình"""
        print("\n👋 Cảm ơn bạn đã sử dụng hệ thống!")
        print("🔄 Hẹn gặp lại!")
        self.running = False
    
    def chay_chuong_trinh(self):
        """Chạy chương trình chính"""
        print("🎉 Chào mừng đến với Hệ thống Quản lý Tiện ích!")
        
        while self.running:
            try:
                self.hien_thi_menu()
                lua_chon = int(input("👉 Nhập lựa chọn của bạn (1-4): "))
                self.chon_chuc_nang(lua_chon)
                
                if self.running:
                    input("\n⏯️  Nhấn Enter để tiếp tục...")
                    
            except ValueError:
                print("❌ Vui lòng nhập số từ 1 đến 4!")
                input("\n⏯️  Nhấn Enter để tiếp tục...")
            except KeyboardInterrupt:
                print("\n\n🛑 Chương trình bị ngắt!")
                self.thoat_chuong_trinh()
            except Exception as e:
                print(f"❌ Đã xảy ra lỗi: {e}")
                input("\n⏯️  Nhấn Enter để tiếp tục...")

# Chạy chương trình
if __name__ == "__main__":
    app = QuanLyTienIch()
    app.chay_chuong_trinh()
Bài 5: Module riêng biệt
Code mẫu tạo module:

python
# File: utils.py - Module tiện ích
"""
Module chứa các hàm tiện ích cho Lab 4
"""

def tinh_tien_dien_theo_bac(so_kwh):
    """Hàm tính tiền điện theo bậc thang"""
    # Implementation như trên
    pass

def tinh_nguyen_lieu(*args, **kwargs):
    """Hàm tính nguyên liệu"""
    # Implementation như trên  
    pass

def loc_so_chan(danh_sach):
    """Lọc số chẵn bằng lambda"""
    return list(filter(lambda x: x % 2 == 0, danh_sach))

def loc_so_le(danh_sach):
    """Lọc số lẻ bằng lambda"""
    return list(filter(lambda x: x % 2 != 0, danh_sach))

# File sử dụng module
# import utils
# ket_qua = utils.tinh_tien_dien_theo_bac(150)
Các bài tập này bao phủ đầy đủ kiến thức Lab 4:

Hàm với tham số: args, kwargs, default values
Lambda functions: với filter, map
Module: tạo và import
Menu: tổ chức chương trình
Exception handling: try-except
Class: tổ chức code OOP -->




