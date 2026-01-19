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