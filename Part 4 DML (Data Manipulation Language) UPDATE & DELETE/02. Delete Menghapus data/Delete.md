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