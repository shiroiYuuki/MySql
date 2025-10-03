===========================================================================
# CATATAN MYSQL (DDL / Data Definition Language)
===========================================================================

## Part 1

### 1. CREATE TABLE
   ---------------------------------------------------------------------------
   Membuat tabel baru bernama "employees".

   CREATE TABLE employees (
       employee_id INT PRIMARY KEY,     -- Kolom unik sebagai primary key
       first_name VARCHAR(50),          -- Nama depan, maksimal 50 karakter
       last_name VARCHAR(50),           -- Nama belakang, maksimal 50 karakter
       hourly_pay DECIMAL(5, 2),        -- Gaji per jam (contoh 999.99)
       hire_date DATE                   -- Tanggal masuk kerja
   );
===========================================================================
### 2. RENAME TABLE
   ---------------------------------------------------------------------------
   Mengubah nama tabel "employees" menjadi "workers".

   RENAME TABLE employees TO workers;
===========================================================================
### 3. DROP TABLE
   ---------------------------------------------------------------------------
   Menghapus tabel secara permanen (HATI-HATI, datanya juga ikut hilang).

   DROP TABLE employees;
===========================================================================
### 4. ALTER TABLE → ADD
   ---------------------------------------------------------------------------
   Menambahkan kolom baru ke tabel.

   ALTER TABLE employees
   ADD phone_number VARCHAR(15);

   -- Menambah kolom "phone_number" dengan maksimal 15 karakter.
===========================================================================
### 5. ALTER TABLE → RENAME COLUMN
   ---------------------------------------------------------------------------
   Mengubah nama kolom.

   ALTER TABLE employees
   RENAME COLUMN phone_number TO email;

   -- Kolom "phone_number" diubah jadi "email".
===========================================================================
### 6. ALTER TABLE → MODIFY
   ---------------------------------------------------------------------------
   Mengubah tipe data atau panjang kolom.

   ALTER TABLE employees
   MODIFY COLUMN email VARCHAR(15);

   -- Kolom "email" sekarang maksimal 15 karakter.
===========================================================================
### 7. ALTER TABLE → MODIFY + AFTER
   ---------------------------------------------------------------------------
   Memindahkan kolom ke urutan tertentu.

   ALTER TABLE employees
   MODIFY email VARCHAR(100) AFTER last_name;

   -- Kolom "email" diubah panjangnya jadi 100 karakter
   -- lalu diletakkan setelah "last_name".
===========================================================================
### 8. ALTER TABLE → MODIFY + FIRST
   ---------------------------------------------------------------------------
   Memindahkan kolom jadi yang pertama.

   ALTER TABLE employees
   MODIFY email VARCHAR(100) FIRST;

   -- Kolom "email" sekarang ada di posisi paling depan tabel.
===========================================================================
### 9. ALTER TABLE → DROP COLUMN
   ---------------------------------------------------------------------------
   Menghapus kolom dari tabel.

   ALTER TABLE employees
   DROP COLUMN email;

   -- Kolom "email" dihapus dari tabel.
===========================================================================
#### 1. CREATE TABLE
   → Membuat tabel baru beserta kolomnya.

#### 2. RENAME TABLE
   → Mengganti nama tabel.

#### 3. DROP TABLE
   → Menghapus tabel (beserta semua data di dalamnya).

#### 4. ALTER TABLE
   → Digunakan untuk mengubah struktur tabel yang sudah ada.
      - ADD COLUMN      → Menambah kolom baru.
      - RENAME COLUMN   → Mengubah nama kolom.
      - MODIFY COLUMN   → Mengubah tipe data/ukuran kolom, atau posisi kolom.
      - DROP COLUMN     → Menghapus kolom dari tabel.
===========================================================================
#### KESIMPULAN:
- CREATE → bikin sesuatu yang baru.
- RENAME → ganti nama.
- DROP   → hapus.
- ALTER  → ubah isi/struktur yang sudah ada.

===========================================================================

## Part 2

### 1. INSERT → Single Row
   ---------------------------------------------------------------------------
   Menambahkan 1 data (baris) ke dalam tabel "employees".

   INSERT INTO employees
   VALUES (1, "Eugene", "Krabs", 25.50, "2023-01-02");

   SELECT * FROM employees;

   -- Hasil: Data Eugene Krabs masuk ke tabel.

===========================================================================

### 2. INSERT → Multiple Rows
   ---------------------------------------------------------------------------
   Menambahkan beberapa data sekaligus ke dalam tabel "employees".

   INSERT INTO employees
   VALUES  (2, "Squidward", "Tentacles", 15.00, "2023-01-03"), 
           (3, "Spongebob", "Squarepants", 12.50, "2023-01-04"), 
           (4, "Patrick", "Star", 12.50, "2023-01-05"), 
           (5, "Sandy", "Cheeks", 17.25, "2023-01-06");

   SELECT * FROM employees;

   -- Hasil: Semua data masuk sekaligus (Squidward, Spongebob, Patrick, Sandy).

===========================================================================

### 3. INSERT → Specific Columns
   ---------------------------------------------------------------------------
   Menambahkan data hanya pada kolom tertentu.
   (Kolom yang tidak disebutkan akan bernilai NULL, jika NULL diperbolehkan).

   INSERT INTO employees (employee_id, first_name, last_name)
   VALUES (6, "Sheldon", "Plankton");

   SELECT * FROM employees;

   -- Hasil: Sheldon Plankton masuk tabel,
   -- sedangkan kolom lain (hourly_pay, hire_date) kosong/NULL.

===========================================================================

#### RANGKUMAN:
- INSERT (Single Row) → Menambahkan 1 data.
- INSERT (Multiple Rows) → Menambahkan banyak data sekaligus.
- INSERT (Specific Columns) → Mengisi data ke kolom tertentu saja.

===========================================================================

#### KESIMPULAN:
- INSERT digunakan untuk **menambah data baru** ke dalam tabel.
- Bisa menambahkan **1 baris**, **banyak baris**, atau hanya **kolom tertentu**.

=========================================================================== 
