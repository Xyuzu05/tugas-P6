
# Tugas Pemweb II - Pertemuan 6

60324033_Naufal Setyabagas Alifian

## Hasil Query

### 1. Total Buku

Query:

```sql
SELECT COUNT(*) AS total_buku FROM buku WHERE is_deleted = 0;
```

Hasil: 7




### 2. Total Inventaris

```sql
SELECT SUM(harga * stok) AS total_inventaris FROM buku WHERE is_deleted = 0;
```

Hasil: 6.850.000
Screenshot: screenshot/2_inventaris.png

---

### 3. Rata-rata Harga

```sql
SELECT AVG(harga) AS rata_harga FROM buku WHERE is_deleted = 0;
```

Hasil: 96.250
Screenshot: screenshot/3_rata.png

---

### 4. Buku Termahal

```sql
SELECT judul, harga FROM buku ORDER BY harga DESC LIMIT 1;
```

Hasil: Laravel Framework Advanced - 125000
Screenshot: screenshot/4_termahal.png

---

### 5. Stok Terbanyak

```sql
SELECT judul, stok FROM buku ORDER BY stok DESC LIMIT 1;
```

Hasil: Web Design Principles - 15
Screenshot: screenshot/5_stok.png

---

### 6. Programming < 100.000

```sql
SELECT * FROM buku WHERE kategori='Programming' AND harga < 100000;
```

Hasil: Pemrograman PHP untuk Pemula, PHP Web Services, JavaScript Modern
Screenshot: screenshot/6_filter1.png

---

### 7. Judul PHP/MySQL

```sql
SELECT * FROM buku WHERE judul LIKE '%PHP%' OR judul LIKE '%MySQL%';
```

Hasil: Pemrograman PHP untuk Pemula, PHP Web Services, Mastering MySQL Database
Screenshot: screenshot/7_filter2.png

---

### 8. Tahun 2024

```sql
SELECT * FROM buku WHERE tahun_terbit = 2024;
```

Hasil: Laravel Framework Advanced, PHP Web Services, PostgreSQL Advanced
Screenshot: screenshot/8_filter3.png

---

### 9. Stok 5–10

```sql
SELECT * FROM buku WHERE stok BETWEEN 5 AND 10;
```

Hasil: BK-001, BK-002, BK-003, BK-007
Screenshot: screenshot/9_filter4.png

---

### 10. Pengarang Budi Raharjo

```sql
SELECT * FROM buku WHERE pengarang='Budi Raharjo';
```

Hasil: Pemrograman PHP untuk Pemula, PHP Web Services
Screenshot: screenshot/10_filter5.png

---

### 11. Jumlah Buku per Kategori

```sql
SELECT kategori, COUNT(*), SUM(stok) FROM buku GROUP BY kategori;
```

Hasil: Programming (4 | 30), Database (2 | 12), Web Design (1 | 15), Networking (1 | 3)
Screenshot: screenshot/11_group1.png

---

### 12. Rata-rata Harga per Kategori

```sql
SELECT kategori, AVG(harga) FROM buku GROUP BY kategori;
```

Hasil: Programming (92.500), Database (105.000), Web Design (85.000), Networking (110.000)
Screenshot: screenshot/12_group2.png

---

### 13. Inventaris Terbesar

```sql
SELECT kategori, SUM(harga*stok) FROM buku GROUP BY kategori ORDER BY SUM(harga*stok) DESC LIMIT 1;
```

Hasil: Programming
Screenshot: screenshot/13_group3.png

---

### 14. Update Harga

```sql
UPDATE buku SET harga = harga * 1.05 WHERE kategori='Programming';
```

Screenshot: screenshot/14_update1.png

---

### 15. Update Stok

```sql
UPDATE buku SET stok = stok + 10 WHERE stok < 5;
```

Screenshot: screenshot/15_update2.png

---

### 16. Restock

```sql
SELECT * FROM buku WHERE stok < 5;
```

Screenshot: screenshot/16_laporan1.png

---

### 17. Top 5 Termahal

```sql
SELECT judul, harga FROM buku ORDER BY harga DESC LIMIT 5;
```

Screenshot: screenshot/17_laporan2.png
