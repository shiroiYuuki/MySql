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