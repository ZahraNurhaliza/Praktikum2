# Praktikum2

## Model Data
• Mahasiswa 
```python
create table Mahasiswa (nim char(11) primary key, nama varchar(50), jenis_kelamin enum('Laki-laki', 'Perempuan'), tgl_lahir date, jalan varchar(100), kota varchar(50), kodepos varchar(10), no_hp varchar(15), kd_ds char(10), foreign key (kd_ds) references Dosen(kd_ds));
```
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/mahasiswa.1.png)

• Dosen 
```python 
create table Dosen (kd_ds char(10) primary key, nama varchar(50));
```
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/dosen.1.png)

• Matakuliah 
```python
create table MataKuliah (kd_mk char(10) primary key, nama varchar(50), sks int);
```
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/matakuliah.1.png)


• JadwalMengajar 
```python
create table JadwalMengajar (kd_ds char(10), kd_mk char(10), hari enum('senin', 'selasa', 'rabu', 'kamis', 'jumat', 'sabtu', 'minggu'), jam time, ruang varchar(10), primary key (kd_ds, kd_mk), foreign key (kd_ds) references Dosen(kd_ds), foreign key (kd_mk) references MataKuliah(kd_mk));
```
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/jadwalmengajar.1.png)


• KRSMahasiswa 
```python
create table KRSMahasiswa (nim char(10), kd_mk char(5), kd_ds char(10), semester int, nilai decimal(5, 2), primary key (nim, kd_mk), foreign key (nim) references Mahasiswa(nim), foreign key(kd_mk) references MataKuliah(kd_mk), foreign key (kd_ds) references Dosen(kd_ds));
```
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/krsmahasiswa.1.png)


## Tabel Mahasiswa
```python
insert into Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)
value ('11223344', 'Ari Santoso', 'Laki-laki', '1998-10-12', NULL, 'Bekasi', NULL, NULL, NULL),
       ('11223345', 'Ario Talib', 'Laki-laki', '1999-11-16', NULL, 'Cikarang', NULL, NULL, NULL),
       ('11223346', 'Dina Marlina', 'Perempuan', '1997-12-01', NULL, 'Karawang', NULL, NULL, NULL),
       ('11223347', 'Lisa Ayu', 'Perempuan', '1996-01-02', NULL, 'Bekasi', NULL, NULL, NULL),
       ('11223348', 'Tiara Wahidah', 'Perempuan', '1908-02-05', NULL, 'Bekasi', NULL, NULL, NULL),
       ('11223349', 'Anton Sinaga', 'Laki-laki', '1988-03-10', NULL, 'Cikarang', NULL, NULL, NULL);
```
### OUTPUT
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.1.png)


## Tampilkan semua isi/record tabel!
1. Ubah data tanggal lahir mahasiswa yang bernama Ari menjadi: 1979-08-31!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.2.png)


2. Tampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.3.png)

3. Hapus Mahasiswa yang bernama Dina!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.4.png)


4. Tampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.5.png)

5. Tampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.6.png)

6. Tampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita!
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.7.png)

7. Tampilkan data nama dan alamat mahasiswa saja dari tabel tersebut
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.8.png)

8. Tampilkan data mahasiswa terurut berdasarkan nama
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/output%20praktikum2.9.png)


## Contoh Syntax 
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/praktikum2.1.png)
![image](https://github.com/ZahraNurhaliza/Praktikum2/blob/main/screenshot/praktikum2.2.png)


## Evaluasi dan Pertanyaan
1. Apa bedanya penggunaan BETWEEN dan penggunaan operator >= dan <= ?
    • (misal: tgl_lahir BETWEEN '1990-10-10' AND '1992-10-11')
        Penggunaan BETWEEN dalam suatu kondisi digunakan untuk memeriksa apakah suatu nilai berada dalam nilai tertentu, yang ditentukan dengan dua nilai batas, yaitu batas bawah (lower bound) dan batas atas (upper bound). Misalnya, dalam contoh yang diberikan, ``tgl_lahir BETWEEN '1990-10-10' AND '1992-10-11'`` akan menghasilkan nilai benar (true) jika tgl_lahir berada di antara tanggal '1990-10-10' dan '1992-10-11', termasuk kedua tanggal tersebut.

    • (misal: tgl_lahir >= '1990-10-10' AND tgl_lahir <= '1992-10-11')
        Penggunaan operator >= (lebih besar atau sama dengan) dan <= (kurang dari atau sama dengan) dalam suatu kondisi digunakan untuk memeriksa apakah suatu nilai berada di antara dua nilai tertentu atau sama dengan salah satu dari dua nilai tersebut. Misalnya, dalam contoh yang diberikan, ``tgl_lahir >= '1990-10-10' AND tgl_lahir <= '1992-10-11'`` akan menghasilkan nilai benar (true) jika tgl_lahir lebih besar atau sama dengan tanggal '1990-10-10' dan kurang dari atau sama dengan tanggal '1992-10-11'.

2. Kesimpulannya
    baik penggunaan BETWEEN maupun penggunaan operator >= dan <= dapat digunakan untuk memeriksa nilai dalam suatu kondisi.
    Penggunaan BETWEEN lebih sederhana karena hanya memerlukan dua nilai batas, sedangkan penggunaan operator >= dan <= memerlukan dua kondisi terpisah. Namun, keduanya dapat digunakan sesuai kebutuhan dan preferensi masing-masing dalam pemrograman atau dalam pengaksesan basis data

## Link Dokumentasi PDF
[Link Google Drive](https://drive.google.com/file/d/1CqF5YXqvQ7I2JOtf7gdjj2GFTu-nywyD/view?usp=share_link)