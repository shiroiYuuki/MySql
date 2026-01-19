===========================================================================

### 8. ALTER TABLE → MODIFY + FIRST

---

Memindahkan kolom jadi yang pertama.

```sql
ALTER TABLE employees
MODIFY email VARCHAR(100) FIRST;
```

-- Kolom "email" sekarang ada di posisi paling depan tabel.

===========================================================================