# Lab7Web

Nama  : Bangkit Akbar Anggara<br>
NIM   : 312010148<br>
Kelas : TI.20.B.1<br>

Instruksi Praktikum

Persiapkan text editor misalnya VSCode.

Buat folder baru dengan nama lab7_php_dasar pada docroot webserver (htdocs)

Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya. Langkah-langkah Praktikum Persiapan Untuk memulai membuat kode php, perlu disiapkan web server dan interpreter PHP terlebih dahulu. Web servar yang kita gunakan adalah Apache 2 dan interpreter PHP 7. Untuk memudahkan proses praktikum, kita gunakan aplikasi bundle web server yaitu XAMPP.

Install XAMPP

Unduh XAMPP dari https://www.apachefriends.org/download.html dan pilih versi portable untuk memudahkan proses installasi. Kemudian extract file tersebut, seusikan direktorinya.

Menjalankan Web Server

Untuk menjalankan web server dari menu XAMPP Control.

Gambar1

• Uji coba apakah server sudah berkerja dengan baik http://127.0.0.1 atau http://localhost Tampil halaman utama XAMPP jika server sudah berkerja dengan baik.

• Dokumen Website Semua file website tempatkan di direktori: \xampp\htdocs

• Database MySQL Direktori: \xampp\mysql Manajemen database: http://localhost/phpmyadmin

Memulai PHP

Buat folder lab7_php_dasar pada root directory web server (C:\xampp\htdocs)

Gambar1

Kemudian untuk mengakses direktory tersebut pada web server dengan mengakses URL: http://localhost/lab7_php_dasar/

Gambar1

PHP Dasar Buat file baru dengan nama php_dasar.php pada directory tersebut. Kemudian buat kode seperti berikut.

<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>PHP Dasar</title>
</head>
<body>
 <h1>Belajar PHP Dasar</h1>
 <?php
 echo "Hello World";
 ?>
</body>
</html>
Gambar1

Kemudian untuk mengakses hasilnya melalui URL:

Gambar1

Variable PHP

Menambahkan variable pada program.

<?php
$nim = "0411500400";
$nama = 'Abdullah';
echo "NIM : " . $nim . "<br>";
echo "Nama : $nama";
?>
Gambar1

Kemudian untuk mengakses hasilnya melalui URL:

Gambar1

<?php
echo 'Selamat Datang ' . $_GET['nama'];
?>
Gambar1

Gambar1

Membuat Form Input
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>PHP Dasar</title>
</head>
<body>
<h2>Form Input</h2>
<form method="post">
 <label>Nama: </label>
 <input type="text" name="nama">
 <input type="submit" value="Kirim">
</form>
<?php
echo 'Selamat Datang ' . $_POST['nama'];
?>
</body>
</html>
Gambar1

Gambar1

<?php
$gaji = 1000000;
$pajak = 0.1;
$thp = $gaji - ($gaji*$pajak);
echo "Gaji sebelum pajak = Rp. $gaji <br>";
echo "Gaji yang dibawa pulang = Rp. $thp";
?>
Gambar1

Gambar1

KONDISI IF
<?php
$nama_hari = date("l");
if ($nama_hari == "Sunday") {
 echo "Minggu";
} elseif ($nama_hari == "Monday") {
 echo "Senin";
} else {
 echo "Selasa";
}
?>
Gambar1

Kondisi Switch
<?php
$nama_hari = date("l");
switch ($nama_hari) {
 case "Sunday":
 echo "Minggu";
 break;
 case "Monday":
 echo "Senin";
 break;
case "Tuesday":
 echo "Selasa";
 break;
 default:
 echo "Sabtu";
?>
Gambar1

Perulangan for
<?php
echo "Perulangan 1 sampai 10 <br />";
for ($i=1; $i<=10; $i++) {
 echo "Perulangan ke: " . $i . '<br />';
}
echo "Perulangan Menurun dari 10 ke 1 <br />";
for ($i=10; $i>=1; $i--) {
 echo "Perulangan ke: " . $i . '<br />';
}
?>
Gambar1

Perulangan while
<?php
echo "Perulangan 1 sampai 10 <br />";
$i=1;
while ($i<=10) {
 echo "Perulangan ke: " . $i . '<br />';
 $i++;
}
?>
Gambar1

Perulangan dowhile
<?php
echo "Perulangan 1 sampai 10 <br />";
$i=1;
do {
 echo "Perulangan ke: " . $i . '<br />';
 $i++;
} while ($i<=10);
?>
Pertanyaan dan Tugas
Buatlah program PHP sederhana dengan menggunakan form input yang menampilkan nama, tanggal lahir dan pekerjaan. Kemudian tampilkan outputnya dengan menghitung umur berdasarkan inputan tanggal lahir. Dan pilihan pekerjaan dengan gaji yang berbeda-beda sesuai pilihan pekerjaan

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>PHP Dasar</title>
</head>
<body>
<h2>Tugas</h2>
 <form method="post">
   <label>Nama: </label>
   <input type="text" name="nama">
   <br>
   <label>Tanggal Lahir: </label>
   <input type="text" name="tgl_lahir">
   <br>
   <label>Pekerjaan:
     <select name='pekerjaan'>
               <option value='Direktur'>Direktur</option>
               <option value='Manager'>Manager</option>
               <option value='Staff'>Staff</option>
               <option value='Operator'>Operator</option>
     </select>
   </label>
   <br>
   <input type="submit" value="Kirim">
 </form>
 <?php
       # Memanggil Nama
       echo 'Nama: ' . $_POST['nama'];
       # Merubah Tanggal Lahir menjadi Umur (Tahun)
       $tgl_lahir = @$_POST['tgl_lahir'];
       $lahir = new DateTime($tgl_lahir);
       $hari_ini = new DateTime();
       $diff = $hari_ini->diff($lahir);
       # Memanggil fungsi umur yg sudah dibuat diatas
       echo "<br> Umur: ". $diff->y ." Tahun";

       # Memanggil pekerjaan
       echo "<br> Pekerjaan: ". $_POST['pekerjaan'];

       # Kondisi if pekerjaan untuk menentukan gaji
       $pekerjaan = @$_POST['pekerjaan'];

       if($pekerjaan == "Direktur"){
           echo '<br> Gaji: Rp. 10.000.000,-';
       }elseif($pekerjaan == "Manager"){
           echo '<br> Gaji: Rp. 7.000.000,-';
       }elseif($pekerjaan == "Staff"){
           echo '<br> Gaji: Rp. 5.000.000,-';
       }elseif($pekerjaan == "Operator"){
           echo '<br> Gaji: Rp. 4.000.000,-';
       }
   ?>
</body>
</html>
#### By: Bangkit Akbar Anggara - 312010148 - TI.20.B.1
