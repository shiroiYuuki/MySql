===========================================================================

### 6. ALTER TABLE → MODIFY

---

Mengubah tipe data atau panjang kolom.

```sql
ALTER TABLE employees
MODIFY COLUMN email VARCHAR(15);
```

-- Kolom "email" sekarang maksimal 15 karakter.

===========================================================================