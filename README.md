# Lab3Web

---

## Membuat Database: Studi Kasus Data Barang

1. Membuat database
   ```sql
   CREATE DATABASE latihan1;
   ```
2. Membuat Tabel
   ```sql
   CREATE TABLE data_barang (
   id_barang int(10) auto_increment Primary Key,
   kategori varchar(30),
   nama varchar(30),
   gambar varchar(100),
   harga_beli decimal(10,0),
   harga_jual decimal(10,0),
   stok int(4)
   );
   ```
   Hasil<br>
   ![Gambar1](img/buatTabel.png)
3. Menambahkan Data
   ```sql
   INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual,
   stok)
   VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000,
   2400000, 5),
   ('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
   ('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
   ```
   ![Gambar1](img/tambahData.png)
