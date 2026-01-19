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