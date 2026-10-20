# Cơ sở dữ liệu: QuanLyDiemThi

```sql
-- Tạo cơ sở dữ liệu
CREATE DATABASE QuanLyDiemThi;
USE QuanLyDiemThi;

-- Tạo bảng HocSinh
CREATE TABLE HocSinh(
    MaHS VARCHAR(20) PRIMARY KEY,
    TenHS VARCHAR(50),
    NgaySinh DATETIME,
    Lop VARCHAR(20),
    GT VARCHAR(20)
);

-- Tạo bảng MonHoc
CREATE TABLE MonHoc(
    MaMH VARCHAR(50) PRIMARY KEY,
    TenMH VARCHAR(50),
    MaGV VARCHAR(20)
);

-- Tạo bảng BangDiem (bảng trung gian)
CREATE TABLE BangDiem(
    MaHS VARCHAR(20),
    MaMH VARCHAR(50),
    DiemThi INT,
    NgayKT DATETIME,
    PRIMARY KEY (MaHS, MaMH),
    FOREIGN KEY (MaHS) REFERENCES HocSinh(MaHS),
    FOREIGN KEY (MaMH) REFERENCES MonHoc(MonHoc)
);

-- Tạo bảng GiaoVien
CREATE TABLE GiaoVien(
    MaGV VARCHAR(20) PRIMARY KEY,
    TenGV VARCHAR(50),
    SDT VARCHAR(10)
);

-- Bổ sung khóa ngoại cho bảng MonHoc liên kết với bảng GiaoVien
ALTER TABLE MonHoc ADD CONSTRAINT FK_MaGV FOREIGN KEY (MaGV) REFERENCES GiaoVien(MaGV);# QuanLyDiemThi.
