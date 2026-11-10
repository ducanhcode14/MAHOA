# LAB 1 - MÃ HÓA ĐỐI XỨNG CỔ ĐIỂN

## 👤 Thông tin thực hiện
- **Họ và tên:** Bùi Đức Anh
- **Mã số sinh viên (MSSV):** 1150080126
- **Lớp:** 11_THMT
- **Học phần:** An toàn và Bảo mật Thông tin

---

## 🎯 Mục tiêu bài Lab
1. Nắm vững nguyên lý hoạt động, thuật toán mã hóa và giải mã của 6 kỹ thuật mã hóa đối xứng cổ điển:
   - **Caesar Cipher** (Dịch vòng ký tự)
   - **Vigenère Cipher** (Mã hóa đa bảng chữ cái lặp khóa)
   - **Rail Fence Cipher** (Mật mã hàng rào zig-zag)
   - **Playfair Cipher** (Mã hóa đa ký tự dùng ma trận 5x5)
   - **Transposition Cipher** (Mã hóa hoán vị cột)
   - **Autokey Cipher** (Mật mã tự sinh khóa từ bản rõ)
2. Xây dựng ứng dụng Desktop đồ họa trực quan bằng **Java Swing** với kiến trúc Maven trong package `week_01`.
3. Tích hợp đọc/ghi file văn bản `.txt` chuẩn UTF-8 qua lớp tiện ích `FileTextIO`.
4. Kết nối hệ quản trị cơ sở dữ liệu **Microsoft SQL Server** qua JDBC driver để quản lý lịch sử mã hóa/giải mã.
5. Triển khai các phương pháp thám mã / phân tích mật mã cổ điển:
   - **Vét cạn (Brute-force Attack):** Thử toàn bộ không gian khóa của Caesar và chấm điểm theo tần suất tiếng Anh.
   - **Phân tích tần suất chữ cái (Frequency Analysis):** Thống kê tần suất xuất hiện của các chữ cái trong bản mã.
   - **Tấn công biết trước bản rõ (Known Plaintext Attack):** Khôi phục khóa Vigenère khi biết một phần cặp bản rõ - bản mã.

---

## 📊 Bộ dữ liệu kiểm thử chuẩn (Test Cases)

| Bài | Thuật toán | Plaintext | Khóa (Key) | Ciphertext chuẩn |
| :---: | :--- | :--- | :--- | :--- |
| **1.1** | **Caesar** | `HELLO` | `3` | `KHOOR` |
| **1.2** | **Vigenère** | `HELLO` | `KEY` | `RIJVS` |
| **1.3** | **Rail Fence** | `HELLO WORLD` | `3` | `HOREL OLLWD` |
| **1.4** | **Playfair** | `HELLOWORLD` | `KEYWORD` | `GYIZSCOKCFBU` |
| **1.5** | **Transposition** | `BAOMAT` | `2,3,1` | `AAOTBM` |
| **1.6** | **Autokey** | `HELLO` | `KEY` | `RIJSS` |

---

## 🏗️ Cấu trúc dự án

```
LAB1/
├── pom.xml                               # Cấu hình dự án Maven, JDK 17 & MSSQL JDBC Driver
├── README.md                             # Tài liệu chi tiết hướng dẫn & báo cáo Lab 1
└── src/
    └── main/
        └── java/
            └── week_01/
                ├── FileTextIO.java              # Tiện ích đọc / ghi file .txt UTF-8
                ├── CaesarCipher.java            # Thuật toán Caesar
                ├── VigenereCipher.java          # Thuật toán Vigenère
                ├── RailFenceCipher.java         # Thuật toán Rail Fence
                ├── PlayfairCipher.java          # Thuật toán Playfair 5x5
                ├── TranspositionCipher.java     # Thuật toán Hoán vị cột
                ├── AutokeyCipher.java           # Thuật toán Autokey
                ├── AttackDemos.java             # Các kỹ thuật phân tích & thám mã
                ├── DbConfig.java                # Quản lý kết nối JDBC SQL Server
                ├── frm_Menu.java                # Giao diện chính (Main Menu)
                ├── frm_Caesar.java              # Giao diện Caesar
                ├── frm_Vigenere.java            # Giao diện Vigenère
                ├── frm_RailFence.java           # Giao diện Rail Fence
                ├── frm_Playfair.java            # Giao diện Playfair
                ├── frm_Transposition.java       # Giao diện Transposition
                ├── frm_Autokey.java             # Giao diện Autokey
                ├── frm_TongHop.java             # Form tổng hợp 6 thuật toán
                ├── frm_KetNoiSQL.java           # Form cấu hình kết nối SQL Server
                ├── frm_LichSu.java              # Form xem lịch sử thao tác
                └── frm_TanCong.java             # Form thực nghiệm thám mã
```

---

## 🚀 Hướng dẫn cài đặt & Khởi chạy

### 1. Yêu cầu môi trường
- **JDK:** Java 17 hoặc Java 21+.
- **IDE:** Apache NetBeans (khuyến nghị bản 20+), Eclipse hoặc IntelliJ IDEA.
- **SQL Server:** Microsoft SQL Server 2019/2022 hoặc SQL Server Express cấu hình cổng TCP/IP `14333`.

### 2. Mở dự án trong NetBeans
1. Mở Apache NetBeans -> Chọn **File** -> **Open Project...** (Ctrl+Shift+O).
2. Trỏ đến thư mục `D:\MaHoa\LAB1`.
3. Nhấp chuột phải vào tên dự án `LAB1_MaHoaCoDien` -> Chọn **Clean and Build** (Shift+F11) để tải các thư viện Maven.
4. Bấm **F6** (hoặc nút Run) để chạy màn hình Menu chính `frm_Menu`.
