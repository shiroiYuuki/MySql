===========================================================================

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