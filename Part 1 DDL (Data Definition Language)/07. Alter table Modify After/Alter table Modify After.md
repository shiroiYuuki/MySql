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