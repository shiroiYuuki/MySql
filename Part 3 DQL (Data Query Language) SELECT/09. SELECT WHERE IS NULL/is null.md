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