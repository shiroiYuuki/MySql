===========================================================================

### 1. CREATE TABLE

---

Membuat tabel baru bernama "employees".

```sql
CREATE TABLE employees (
    employee_id INT,                 -- Kolom unik sebagai primary key
    first_name VARCHAR(50),          -- Nama depan, maksimal 50 karakter
    last_name VARCHAR(50),           -- Nama belakang, maksimal 50 karakter
    hourly_pay DECIMAL(5, 2),        -- Gaji per jam (contoh 999.99)
    hire_date DATE                   -- Tanggal masuk kerja
);
```

===========================================================================