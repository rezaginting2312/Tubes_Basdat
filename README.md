# Step By Step
Warkop-28


###1. Membuat Table Pelanggan
```sql
CREATE TABLE pelanggan (
    id_pelanggan INT AUTO_INCREMENT PRIMARY KEY,
    nama_pelanggan VARCHAR(100),
    alamat_pelanggan TEXT,
    no_telepon VARCHAR(15)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/f0b36880-8033-4841-8531-0680b931a8ac)


### 2. Membuat Table Karyawan
```sql
CREATE TABLE karyawan (
    id_karyawan INT AUTO_INCREMENT PRIMARY KEY,
    nama_karyawan VARCHAR(100),
    posisi VARCHAR(50)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/3f2d133c-26ac-410f-8cbe-4754c4066c35)
### 3. Membuat Table Menu
```sql
CREATE TABLE menu (
    id_menu INT AUTO_INCREMENT PRIMARY KEY,
    nama_menu VARCHAR(100),
    harga_menu DECIMAL(10, 2)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/7bd73e30-f2dd-47f0-a083-6f9881f8a965)
### 4. Membuat Table Meja
```sql
CREATE TABLE meja (
    id_meja INT AUTO_INCREMENT PRIMARY KEY,
    nomor_meja INT,
    status_meja ENUM('Kosong', 'Terisi') DEFAULT 'Kosong'
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/b35164c0-5651-46ad-881c-b2164f66b2f0)
### 5. Membuat Table Pesanan
```sql
CREATE TABLE pesanan (
    id_pesanan INT AUTO_INCREMENT PRIMARY KEY,
    tanggal_pesanan DATE,
    total_harga DECIMAL(10, 2),
    status_pesanan ENUM('Selesai', 'Dibatalkan') DEFAULT 'Selesai',
    id_pelanggan INT,
    id_karyawan INT,
    id_meja INT,
    FOREIGN KEY (id_pelanggan) REFERENCES pelanggan(id_pelanggan),
    FOREIGN KEY (id_karyawan) REFERENCES karyawan(id_karyawan),
    FOREIGN KEY (id_meja) REFERENCES meja(id_meja)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/e139cb11-5da3-425a-815c-4b808ba9d584)
### 6. Membuat Table Detail Pesanan
```sql
CREATE TABLE detail_pesanan (
    id_detail_pesanan INT AUTO_INCREMENT PRIMARY KEY,
    id_pesanan INT,
    id_menu INT,
    jumlah_pesanan INT,
    subtotal DECIMAL(10, 2),
    FOREIGN KEY (id_pesanan) REFERENCES pesanan(id_pesanan),
    FOREIGN KEY (id_menu) REFERENCES menu(id_menu)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
![image](https://github.com/user-attachments/assets/b63250fe-01db-4e73-94c9-ce4f8c2cded4)

### 7. Menambahkan Data Dummy Ke Table Pelanggan
```sql
INSERT INTO pelanggan (nama_pelanggan, alamat_pelanggan, no_telepon) VALUES
('Andi Wijaya', 'Jl. Merdeka No. 12', '081234567890'),
('Budi Santoso', 'Jl. Sudirman No. 45', '081234567891'),
('Citra Lestari', 'Jl. Gajah Mada No. 22', '081234567892'),
('Dewi Amalia', 'Jl. Pattimura No. 11', '081234567893'),
('Eko Susilo', 'Jl. Thamrin No. 20', '081234567894'),
('Fikri Maulana', 'Jl. Diponegoro No. 30', '081234567895'),
('Gina Maharani', 'Jl. Kartini No. 25', '081234567896'),
('Hendra Pratama', 'Jl. Sultan Agung No. 15', '081234567897'),
('Irma Kusuma', 'Jl. Ahmad Yani No. 50', '081234567898'),
('Joko Saputra', 'Jl. Jenderal Soedirman No. 78', '081234567899'),
('Kirana Putri', 'Jl. Cendrawasih No. 13', '081234567900'),
('Lina Sari', 'Jl. Letjen Suprapto No. 32', '081234567901'),
('Maya Wulan', 'Jl. Imam Bonjol No. 19', '081234567902'),
('Nadia Fitri', 'Jl. Gatot Subroto No. 77', '081234567903'),
('Oka Andika', 'Jl. Sisingamangaraja No. 23', '081234567904'),
('Putri Ramadhani', 'Jl. Veteran No. 31', '081234567905'),
('Qori Fadli', 'Jl. Hasanuddin No. 28', '081234567906'),
('Rama Hermawan', 'Jl. Pemuda No. 18', '081234567907'),
('Sari Ayu', 'Jl. Raden Saleh No. 17', '081234567908'),
('Taufik Hidayat', 'Jl. Melati No. 33', '081234567909');
```
![image](https://github.com/user-attachments/assets/6cf37f7c-96b6-43eb-9a4f-9af2ff44e074)
### 8. Menambahkan Data Dummy ke table Karyawan
```sql
INSERT INTO karyawan (nama_karyawan, posisi) VALUES
('Rina Ambarwati', 'Pelayan'),
('Agus Wijaya', 'Kasir'),
('Diana Puspa', 'Pelayan'),
('Siti Aisyah', 'Barista'),
('Bambang Sutrisno', 'Koki'),
('Indra Lesmana', 'Pelayan'),
('Teguh Prakoso', 'Barista'),
('Wulan Saputri', 'Pelayan'),
('Farid Nurcahyo', 'Pelayan'),
('Yuni Andriani', 'Kasir'),
('Nugroho Prasetyo', 'Koki'),
('Lisa Utami', 'Pelayan'),
('Yanto Susanto', 'Pelayan'),
('Rika Sari', 'Kasir'),
('Satria Utama', 'Pelayan'),
('Putri Damayanti', 'Barista'),
('Heri Purnomo', 'Pelayan'),
('Arif Budiman', 'Barista'),
('Ayu Setiawan', 'Kasir'),
('Dewi Anggraini', 'Pelayan');
```
![image](https://github.com/user-attachments/assets/cdb09172-47bb-48b4-87ca-e83b2b6bd0dc)

### 9. Menambahkan Data Dummy Ke Table Menu
```sql
INSERT INTO menu (nama_menu, harga_menu) VALUES
('Kopi Hitam', 10000),
('Teh Manis', 8000),
('Es Jeruk', 12000),
('Nasi Goreng', 20000),
('Mie Goreng', 18000),
('Roti Bakar', 15000),
('Soto Ayam', 22000),
('Bakso', 17000),
('Mie Ayam', 18000),
('Es Teh', 5000),
('Es Kopi Susu', 15000),
('Kopi Latte', 18000),
('Cappuccino', 20000),
('Es Coklat', 12000),
('Air Mineral', 3000),
('Nasi Ayam', 25000),
('Ayam Geprek', 22000),
('Nasi Uduk', 15000),
('Kentang Goreng', 12000),
('Burger', 25000);
```
![image](https://github.com/user-attachments/assets/af13464f-770e-48a1-962b-7b10f31bdcac)
### 10. Menambahkan Data Dummy Ke table Meja
```sql
INSERT INTO meja (nomor_meja, status_meja) VALUES
(1, 'Kosong'),
(2, 'Kosong'),
(3, 'Kosong'),
(4, 'Kosong'),
(5, 'Kosong'),
(6, 'Kosong'),
(7, 'Kosong'),
(8, 'Kosong'),
(9, 'Kosong'),
(10, 'Kosong'),
(11, 'Kosong'),
(12, 'Kosong'),
(13, 'Kosong'),
(14, 'Kosong'),
(15, 'Kosong'),
(16, 'Kosong'),
(17, 'Kosong'),
(18, 'Kosong'),
(19, 'Kosong'),
(20, 'Kosong');
```
![image](https://github.com/user-attachments/assets/6bef9926-89f2-4b84-a7fa-b2c26a4d9829)
### 11. Menambahkan Data Dummy Ke table Pesanan
```sql
INSERT INTO pesanan (tanggal_pesanan, total_harga, status_pesanan, id_pelanggan, id_karyawan, id_meja) VALUES
('2024-12-10', 50000, 'Selesai', 1, 2, 3),
('2024-12-11', 60000, 'Selesai', 2, 1, 5),
('2024-12-12', 75000, 'Selesai', 3, 3, 4),
('2024-12-13', 90000, 'Selesai', 4, 4, 7),
('2024-12-14', 80000, 'Selesai', 5, 5, 1),
('2024-12-15', 45000, 'Selesai', 6, 6, 6),
('2024-12-16', 70000, 'Selesai', 7, 7, 2),
('2024-12-17', 95000, 'Selesai', 8, 8, 10),
('2024-12-18', 100000, 'Selesai', 9, 9, 9),
('2024-12-19', 120000, 'Selesai', 10, 10, 11),
('2024-12-20', 55000, 'Selesai', 11, 11, 12),
('2024-12-21', 65000, 'Selesai', 12, 12, 13),
('2024-12-22', 50000, 'Selesai', 13, 13, 14),
('2024-12-23', 45000, 'Selesai', 14, 14, 15),
('2024-12-24', 80000, 'Selesai', 15, 15, 16),
('2024-12-25', 95000, 'Selesai', 16, 16, 17),
('2024-12-26', 50000, 'Selesai', 17, 17, 18),
('2024-12-27', 65000, 'Selesai', 18, 18, 19),
('2024-12-28', 75000, 'Selesai', 19, 19, 20),
('2024-12-29', 55000, 'Selesai', 20, 20, 1);
```
![image](https://github.com/user-attachments/assets/2a7b2a0c-fcfe-4646-aac1-b126eacd0842)
### 12. Menambahkan Data Dummy Ke Table Detail Pesanan
```sql
INSERT INTO detail_pesanan (id_pesanan, id_menu, jumlah_pesanan, subtotal) VALUES
(1, 1, 2, 20000),
(1, 3, 1, 12000),
(2, 4, 1, 20000),
(2, 6, 1, 15000),
(3, 5, 2, 36000),
(3, 7, 1, 22000),
(4, 9, 1, 18000),
(4, 2, 2, 16000),
(5, 8, 1, 17000),
(5, 10, 2, 10000),
(6, 11, 1, 15000),
(6, 12, 1, 18000),
(7, 13, 1, 12000),
(7, 14, 2, 24000),
(8, 15, 1, 3000),
(8, 16, 1, 25000),
(9, 17, 1, 22000),
(9, 18, 2, 30000),
(10, 19, 2, 50000),
(10, 20, 1, 25000);
```
![image](https://github.com/user-attachments/assets/a067d387-1078-4bd6-bb15-b7586dc0e9a7)
### 13. Relasi Antar Table 
```sql
ALTER TABLE pesanan
    ADD CONSTRAINT fk_pelanggan_pesanan
    FOREIGN KEY (id_pelanggan) REFERENCES pelanggan(id_pelanggan),
    
    ADD CONSTRAINT fk_karyawan_pesanan
    FOREIGN KEY (id_karyawan) REFERENCES karyawan(id_karyawan),
    
    ADD CONSTRAINT fk_meja_pesanan
    FOREIGN KEY (id_meja) REFERENCES meja(id_meja);

ALTER TABLE detail_pesanan
    ADD CONSTRAINT fk_pesanan_detail_pesanan
    FOREIGN KEY (id_pesanan) REFERENCES pesanan(id_pesanan),
    
    ADD CONSTRAINT fk_menu_detail_pesanan
    FOREIGN KEY (id_menu) REFERENCES menu(id_menu);
```

### 14. Transaksi
```sql
START TRANSACTION;
INSERT INTO pesanan (tanggal_pesanan, total_harga, status_pesanan, id_pelanggan, id_karyawan, id_meja) VALUES ('2024-12-30', 90000, 'Selesai', 5, 2, 3);
SET @id_pesanan = LAST_INSERT_ID();
INSERT INTO detail_pesanan (id_pesanan, id_menu, jumlah_pesanan, subtotal) VALUES (@id_pesanan, 4, 2, 40000), (@id_pesanan, 7, 1, 50000);
UPDATE meja SET status_meja = 'Terisi' WHERE id_meja = 3;
COMMIT;
```

### 15. Laporan Dan Transaksi 
```sql
SELECT 
    p.id_pesanan AS 'ID Pesanan',
    p.tanggal_pesanan AS 'Tanggal Pesanan',
    pl.nama_pelanggan AS 'Nama Pelanggan',
    k.nama_karyawan AS 'Nama Karyawan',
    m.nama_menu AS 'Nama Menu',
    dp.jumlah_pesanan AS 'Jumlah Pesanan',
    dp.subtotal AS 'Subtotal',
    p.total_harga AS 'Total Harga',
    me.nomor_meja AS 'Nomor Meja',
    me.status_meja AS 'Status Meja',
    p.status_pesanan AS 'Status Pesanan'
FROM 
    pesanan p
JOIN 
    pelanggan pl ON p.id_pelanggan = pl.id_pelanggan
JOIN 
    karyawan k ON p.id_karyawan = k.id_karyawan
JOIN 
    detail_pesanan dp ON p.id_pesanan = dp.id_pesanan
JOIN 
    menu m ON dp.id_menu = m.id_menu
JOIN 
    meja me ON p.id_meja = me.id_meja
ORDER BY 
    p.tanggal_pesanan DESC;
```
![image](https://github.com/user-attachments/assets/49ac7570-8b05-4580-8499-eceb67e275b2)
### 16. Update Data Pelanggan
```sql
UPDATE pelanggan
SET nama_pelanggan = 'Budi Raharjo', no_telepon = '081298765432'
WHERE id_pelanggan = 1;
```
![image](https://github.com/user-attachments/assets/1885eaed-5641-45fa-b995-ace5fe54d77f)
### 17. Delete Detail Pesanan
```sql
DELETE FROM detail_pesanan
WHERE id_detail_pesanan = 1;
```
![image](https://github.com/user-attachments/assets/5c0d17d8-f37b-494b-a935-bcb8db4eccf5)
