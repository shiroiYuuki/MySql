===========================================================================

### 4. ALTER DATABASE → READ ONLY

---

Mengubah mode database menjadi read-only (tidak bisa diubah/diedit).
Biasanya digunakan untuk backup atau proteksi data.

```sql
ALTER DATABASE MyDB READ ONLY = 1;
```

-- Hasil: Database MyDB hanya bisa dibaca, tidak bisa dimodifikasi.

---

Untuk mengembalikannya agar bisa diubah lagi:

```sql
ALTER DATABASE MyDB READ ONLY = 0;
```

-- Hasil: Database bisa kembali di-edit seperti biasa.

===========================================================================