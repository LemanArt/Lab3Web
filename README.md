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
   Hasil<br>
   ![Gambar1](img/tambahData.png)

---

## Membuat Program CRUD

1. membuat file koneksi
   ```php
   <?php
       $host = "localhost";
       $user = "root";
       $pass = "";
       $db = "latihan1";
       $conn = mysqli_connect($host, $user, $pass, $db);
       if ($conn == false) {
           echo "Koneksi ke server gagal.";
           die();
       } else echo "Koneksi berhasil";
   ```
   Hasil<br>
   ![Gambar1](img/koneksi.png)<br>
2. Membuat file index untuk menampilkan data (Read)

   ```php
   <?php
   include("koneksi.php");
   // query untuk menampilkan data
   $sql = 'SELECT * FROM data_barang';
   $result = mysqli_query($conn, $sql);
   ?>
   <!DOCTYPE html>
   <html lang="en">

   <head>
       <meta charset="UTF-8">
       <link href="style.css" rel="stylesheet" type="text/css" />
       <title>Data Barang</title>
   </head>

   <body>
       <div class="container">
           <h1>Data Barang</h1>
           <div class="main">
               <a href='tambah.php?nama=".$row["nama"]."'>Tambah Data</a>
               <table border="1px">
                   <tr>
                       <th>Gambar</th>
                       <th>Nama Barang</th>
                       <th>Katagori</th>
                       <th>Harga Jual</th>
                       <th>Harga Beli</th>
                       <th>Stok</th>
                       <th>Aksi</th>
                   </tr>
                   <?php if ($result) : ?>
                       <?php while ($row = mysqli_fetch_array($result)) : ?>
                           <tr>
                               <td><img src="gambar/<?= $row['gambar']; ?>" alt="<?= $row['nama']; ?>"></td>
                               <td><?= $row['nama']; ?></td>
                               <td><?= $row['kategori']; ?></td>
                               <td><?= $row['harga_beli']; ?></td>
                               <td><?= $row['harga_jual']; ?></td>
                               <td><?= $row['stok']; ?></td>
                               <td><a href='edit.php?nama=".$row["nama"]."'>Edit</a> | <a href='delete.php?nama=".$row["nama"]."'>Delete</a></td>
                           </tr>
                       <?php endwhile;
                   else : ?>
                       <tr>
                           <td colspan="7">Belum ada data</td>
                       </tr>
                   <?php endif; ?>
               </table>
           </div>
       </div>
   </body>
   ```

   Hasil<br>
   ![Gambar1](img/tampildata.png)
