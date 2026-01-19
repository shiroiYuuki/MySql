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