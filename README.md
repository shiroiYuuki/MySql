===========================================================================

# CATATAN MYSQL

===========================================================================
## Part 0 — DATABASE MANAGEMENT (CREATE, USE, DROP, ALTER)

### 1. CREATE DATABASE

---

Membuat database baru bernama **MyDB**.

```sql
CREATE DATABASE MyDB;
```

-- Hasil: Database baru bernama MyDB berhasil dibuat.

===========================================================================

### 2. USE DATABASE

---

Memilih database yang akan digunakan untuk operasi berikutnya.

```sql
USE MyDB;
```

-- Hasil: Semua perintah berikutnya akan dijalankan di dalam database MyDB.

===========================================================================

### 3. DROP DATABASE

---

Menghapus database secara permanen (termasuk seluruh tabel dan datanya).
⚠️HATI-HATI!⚠️ Setelah dihapus, data tidak bisa dikembalikan.

```sql
DROP DATABASE MyDB;
```

-- Hasil: Database MyDB dan seluruh isinya dihapus.

===========================================================================

### 4. ALTER DATABASE → READ ONLY

---

Mengubah mode database menjadi read-only (tidak bisa diubah/diedit).
Biasanya digunakan untuk backup atau proteksi data.

```sql
ALTER DATABASE MyDB READ ONLY = 1;
```

-- Hasil: Database MyDB hanya bisa dibaca, tidak bisa dimodifikasi.

---

Untuk mengembalikannya agar bisa diubah lagi:

```sql
ALTER DATABASE MyDB READ ONLY = 0;
```

-- Hasil: Database bisa kembali di-edit seperti biasa.

===========================================================================

#### RANGKUMAN (DATABASE MANAGEMENT)

* CREATE DATABASE → Membuat database baru.
* USE → Memilih database aktif untuk digunakan.
* DROP DATABASE → Menghapus database beserta seluruh datanya.
* ALTER DATABASE → Mengubah properti database (misal: read-only).

===========================================================================

#### KESIMPULAN (DATABASE MANAGEMENT)

* CREATE → bikin database baru.
* USE → masuk ke database tertentu.
* DROP → hapus database beserta isinya.
* ALTER → ubah pengaturan database (contohnya read-only mode).

===========================================================================

## Part 1 — DDL (Data Definition Language)

### 1. CREATE TABLE

---

Membuat tabel baru bernama "employees".

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,     -- Kolom unik sebagai primary key
    first_name VARCHAR(50),          -- Nama depan, maksimal 50 karakter
    last_name VARCHAR(50),           -- Nama belakang, maksimal 50 karakter
    hourly_pay DECIMAL(5, 2),        -- Gaji per jam (contoh 999.99)
    hire_date DATE                   -- Tanggal masuk kerja
);
```

===========================================================================

### 2. RENAME TABLE

---

Mengubah nama tabel "employees" menjadi "workers".

```sql
RENAME TABLE employees TO workers;
```

===========================================================================

### 3. DROP TABLE

---

Menghapus tabel secara permanen (HATI-HATI, datanya juga ikut hilang).

```sql
DROP TABLE employees;
```

===========================================================================

### 4. ALTER TABLE → ADD

---

Menambahkan kolom baru ke tabel.

```sql
ALTER TABLE employees
ADD phone_number VARCHAR(15);
```

-- Menambah kolom "phone_number" dengan maksimal 15 karakter.

===========================================================================

### 5. ALTER TABLE → RENAME COLUMN

---

Mengubah nama kolom.

```sql
ALTER TABLE employees
RENAME COLUMN phone_number TO email;
```

-- Kolom "phone_number" diubah jadi "email".

===========================================================================

### 6. ALTER TABLE → MODIFY

---

Mengubah tipe data atau panjang kolom.

```sql
ALTER TABLE employees
MODIFY COLUMN email VARCHAR(15);
```

-- Kolom "email" sekarang maksimal 15 karakter.

===========================================================================

### 7. ALTER TABLE → MODIFY + AFTER

---

Memindahkan kolom ke urutan tertentu.

```sql
ALTER TABLE employees
MODIFY email VARCHAR(100) AFTER last_name;
```

-- Kolom "email" diubah panjangnya jadi 100 karakter
-- lalu diletakkan setelah "last_name".

===========================================================================

### 8. ALTER TABLE → MODIFY + FIRST

---

Memindahkan kolom jadi yang pertama.

```sql
ALTER TABLE employees
MODIFY email VARCHAR(100) FIRST;
```

-- Kolom "email" sekarang ada di posisi paling depan tabel.

===========================================================================

### 9. ALTER TABLE → DROP COLUMN

---

Menghapus kolom dari tabel.

```sql
ALTER TABLE employees
DROP COLUMN email;
```

-- Kolom "email" dihapus dari tabel.

===========================================================================

#### RANGKUMAN (DDL)

* CREATE TABLE → Membuat tabel baru beserta kolomnya.
* RENAME TABLE → Mengganti nama tabel.
* DROP TABLE   → Menghapus tabel beserta datanya.
* ALTER TABLE  → Mengubah struktur tabel.

  * ADD COLUMN      → Menambah kolom baru.
  * RENAME COLUMN   → Mengubah nama kolom.
  * MODIFY COLUMN   → Mengubah tipe data/ukuran kolom atau posisi kolom.
  * DROP COLUMN     → Menghapus kolom.

===========================================================================

#### KESIMPULAN (DDL)

* CREATE → bikin sesuatu yang baru.
* RENAME → ganti nama.
* DROP   → hapus.
* ALTER  → ubah isi/struktur yang sudah ada.

===========================================================================

## Part 2 — DML (Data Manipulation Language / INSERT)

### 1. INSERT → Single Row

---

Menambahkan 1 data (baris) ke dalam tabel "employees".

```sql
INSERT INTO employees
VALUES (1, "Eugene", "Krabs", 25.50, "2023-01-02");

SELECT * FROM employees;
```

-- Hasil: Data Eugene Krabs masuk ke tabel.

===========================================================================

### 2. INSERT → Multiple Rows

---

Menambahkan beberapa data sekaligus ke dalam tabel "employees".

```sql
INSERT INTO employees
VALUES  (2, "Squidward", "Tentacles", 15.00, "2023-01-03"),
        (3, "Spongebob", "Squarepants", 12.50, "2023-01-04"),
        (4, "Patrick", "Star", 12.50, "2023-01-05"),
        (5, "Sandy", "Cheeks", 17.25, "2023-01-06");

SELECT * FROM employees;
```

-- Hasil: Semua data masuk sekaligus (Squidward, Spongebob, Patrick, Sandy).

===========================================================================

### 3. INSERT → Specific Columns

---

Menambahkan data hanya pada kolom tertentu.
(Kolom yang tidak disebutkan akan bernilai NULL, jika NULL diperbolehkan).

```sql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (6, "Sheldon", "Plankton");

SELECT * FROM employees;
```

-- Hasil: Sheldon Plankton masuk tabel,
-- sedangkan kolom lain (hourly_pay, hire_date) kosong/NULL.

===========================================================================

#### RANGKUMAN (DML → INSERT)

* INSERT (Single Row) → Menambahkan 1 data.
* INSERT (Multiple Rows) → Menambahkan banyak data sekaligus.
* INSERT (Specific Columns) → Mengisi data ke kolom tertentu saja.

===========================================================================

#### KESIMPULAN (DML → INSERT)

* INSERT digunakan untuk **menambah data baru** ke dalam tabel.
* Bisa menambahkan **1 baris**, **banyak baris**, atau hanya **kolom tertentu**.

===========================================================================
## Part 3 — DQL (Data Query Language / SELECT)

### 1. SELECT * 

---

Menampilkan semua data dari tabel "employees".

```sql
SELECT * FROM employees;
```

-- Hasil: Semua kolom dan semua baris ditampilkan.

===========================================================================

### 2. SELECT → Specific Columns (first_name, last_name)

---

Menampilkan hanya kolom tertentu.

```sql
SELECT first_name, last_name FROM employees;
```

-- Hasil: Hanya "first_name" dan "last_name" yang ditampilkan.

===========================================================================

### 3. SELECT → Specific Columns (last_name, first_name)

---

Menampilkan kolom dalam urutan berbeda.

```sql
SELECT last_name, first_name FROM employees;
```

-- Hasil: Kolom "last_name" muncul lebih dulu dibanding "first_name".

===========================================================================

### 4. SELECT → WHERE (Exact Match by employee_id)

---

Menampilkan data karyawan dengan employee_id = 1.

```sql
SELECT *
FROM employees
WHERE employee_id = 1;
```

-- Hasil: Hanya 1 baris yang employee_id-nya sama dengan 1.

===========================================================================

### 5. SELECT → WHERE (Exact Match by first_name)

---

Menampilkan data karyawan dengan nama depan "Spongebob".

```sql
SELECT *
FROM employees
WHERE first_name = "Spongebob";
```

-- Hasil: Data karyawan bernama Spongebob.

===========================================================================

### 6. SELECT → WHERE (Comparison ≥)

---

Menampilkan karyawan dengan gaji per jam lebih besar atau sama dengan 15.

```sql
SELECT *
FROM employees
WHERE hourly_pay >= 15;
```

-- Hasil: Semua karyawan yang gajinya ≥ 15.

===========================================================================

### 7. SELECT → WHERE (Date Comparison)

---

Menampilkan karyawan yang tanggal masuk kerjanya sebelum atau sama dengan 3 Januari 2023.

```sql
SELECT hire_date, first_name
FROM employees
WHERE hire_date <= "2023-01-03";
```

-- Hasil: Nama + tanggal masuk kerja karyawan lama.

===========================================================================

### 8. SELECT → WHERE (Not Equal)

---

Menampilkan semua data kecuali employee_id = 1.

```sql
SELECT *
FROM employees
WHERE employee_id != 1;
```

-- Hasil: Semua data ditampilkan, kecuali ID 1.

===========================================================================

### 9. SELECT → WHERE (IS NULL)

---

Menampilkan karyawan yang belum memiliki tanggal masuk (hire_date kosong).

```sql
SELECT *
FROM employees
WHERE hire_date IS NULL;
```

-- Hasil: Karyawan tanpa tanggal masuk.

===========================================================================

### 10. SELECT → WHERE (IS NOT NULL)

---

Menampilkan karyawan yang sudah memiliki tanggal masuk (hire_date terisi).

```sql
SELECT *
FROM employees
WHERE hire_date IS NOT NULL;
```

-- Hasil: Semua karyawan dengan hire_date yang terisi.

===========================================================================

#### RANGKUMAN (DML → SELECT)

* SELECT * → Ambil semua kolom.
* SELECT col1, col2 → Ambil kolom tertentu saja.
* WHERE → Menyaring data dengan kondisi.
   * = → Sama dengan.
   * != → Tidak sama dengan.
   * >=, <= → Perbandingan angka/tanggal.
   * IS NULL → Nilai kosong.
   * IS NOT NULL → Nilai tidak kosong.

===========================================================================

#### KESIMPULAN (DML → SELECT)

* SELECT digunakan untuk membaca/menampilkan data.
* Bisa menampilkan semua kolom, kolom tertentu, atau disaring dengan kondisi.
* Cocok untuk laporan, debugging, atau cek isi tabel.

===========================================================================

## Part 4 — DML (Data Manipulation Language / UPDATE & DELETE)

### 1. UPDATE → Mengubah Data

---

Mengubah nilai kolom pada baris tertentu.

```sql
UPDATE employees
SET hourly_pay = 10.25
WHERE employee_id = 6;

SELECT * FROM employees;
```

-- Hasil: Gaji (hourly_pay) milik karyawan dengan employee_id = 6 berubah jadi 10.25.

Catatan Penting:
Selalu gunakan WHERE saat UPDATE supaya tidak semua data ikut berubah.
Jika WHERE dihapus, seluruh baris akan di-update dengan nilai baru.

===========================================================================

### 2. DELETE → Menghapus Data

---

Menghapus baris tertentu dari tabel.

```sql
DELETE FROM employees
WHERE employee_id = 6;

SELECT * FROM employees;
```

-- Hasil: Data dengan employee_id = 6 dihapus dari tabel.
Catatan Penting:
Sama seperti UPDATE, jangan pernah lupa WHERE.
Jika WHERE dihapus, semua data akan terhapus permanen dari tabel.

===========================================================================

#### RANGKUMAN (DML → UPDATE & DELETE)

* UPDATE → Mengubah nilai kolom pada data tertentu.
* DELETE → Menghapus baris data dari tabel.
* Gunakan WHERE untuk menargetkan baris tertentu.
* Gunakan SELECT * FROM employees; setelahnya untuk memastikan hasilnya.

===========================================================================

#### KESIMPULAN (DML → UPDATE & DELETE)

* UPDATE = ubah isi data.
* DELETE = hapus data.
* Tanpa WHERE = semua data bisa berubah atau terhapus.

===========================================================================

