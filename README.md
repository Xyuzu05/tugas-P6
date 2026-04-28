# tugas-P6
# 📚 Tugas 1: Eksplorasi Database Perpustakaan dengan Query SQL

## 📌 Deskripsi

Pada tugas ini, dilakukan eksplorasi database **perpustakaan** menggunakan query SQL untuk memahami pengolahan data seperti perhitungan, pencarian, pengelompokan, dan manipulasi data.

---

## 📊 1. Statistik Buku

### 1.1 Total Buku

**Query:**

```sql
SELECT COUNT(*) AS total_buku FROM buku WHERE is_deleted = 0;
```

**Hasil:**
![Total Buku](screenshot/1_total_buku.png)

**Penjelasan:**
Query ini digunakan untuk menghitung jumlah seluruh buku yang tersedia. Berdasarkan hasil, terdapat sejumlah buku aktif dalam database.

---

### 1.2 Total Nilai Inventaris

**Query:**

```sql
SELECT SUM(harga * stok) AS total_inventaris FROM buku WHERE is_deleted = 0;
```

**Hasil:**
![Total Inventaris](screenshot/2_inventaris.png)

**Penjelasan:**
Query ini menghitung total nilai inventaris buku berdasarkan harga dikalikan stok.

---

### 1.3 Rata-rata Harga Buku

**Query:**

```sql
SELECT AVG(harga) AS rata_harga FROM buku WHERE is_deleted = 0;
```

**Hasil:**
![Rata Harga](screenshot/3_rata_harga.png)

**Penjelasan:**
Digunakan untuk mengetahui rata-rata harga buku dalam database.

---

### 1.4 Buku Termahal

**Query:**

```sql
SELECT judul, harga FROM buku 
WHERE is_deleted = 0 
ORDER BY harga DESC LIMIT 1;
```

**Hasil:**
![Buku Termahal](screenshot/4_termahal.png)

**Penjelasan:**
Menampilkan buku dengan harga tertinggi.

---

### 1.5 Buku dengan Stok Terbanyak

**Query:**

```sql
SELECT judul, stok FROM buku 
WHERE is_deleted = 0 
ORDER BY stok DESC LIMIT 1;
```

**Hasil:**
![Stok Terbanyak](screenshot/5_stok.png)

**Penjelasan:**
Menampilkan buku dengan jumlah stok paling banyak.

---

## 🔍 2. Filter dan Pencarian

### 2.1 Buku Programming Harga < 100.000

```sql
SELECT * FROM buku 
WHERE kategori = 'Programming' AND harga < 100000 AND is_deleted = 0;
```

![Filter 1](screenshot/6_filter1.png)

Menampilkan buku kategori Programming dengan harga di bawah 100.000.

---

### 2.2 Buku dengan Kata PHP atau MySQL

```sql
SELECT * FROM buku 
WHERE judul LIKE '%PHP%' OR judul LIKE '%MySQL%';
```

![Filter 2](screenshot/7_filter2.png)

Menampilkan buku berdasarkan kata kunci pada judul.

---

### 2.3 Buku Tahun 2024

```sql
SELECT * FROM buku 
WHERE tahun_terbit = 2024 AND is_deleted = 0;
```

![Filter 3](screenshot/8_filter3.png)

Menampilkan buku yang diterbitkan pada tahun 2024.

---

### 2.4 Buku dengan Stok 5–10

```sql
SELECT * FROM buku 
WHERE stok BETWEEN 5 AND 10 AND is_deleted = 0;
```

![Filter 4](screenshot/9_filter4.png)

Menampilkan buku dengan jumlah stok tertentu.

---

### 2.5 Buku oleh Budi Raharjo

```sql
SELECT * FROM buku 
WHERE pengarang = 'Budi Raharjo' AND is_deleted = 0;
```

![Filter 5](screenshot/10_filter5.png)

Menampilkan buku berdasarkan pengarang.

---

## 📊 3. Grouping dan Agregasi

### 3.1 Jumlah Buku per Kategori

```sql
SELECT kategori, COUNT(*) AS jumlah_buku, SUM(stok) AS total_stok
FROM buku
WHERE is_deleted = 0
GROUP BY kategori;
```

![Grouping 1](screenshot/11_group1.png)

Menampilkan jumlah buku dan total stok per kategori.

---

### 3.2 Rata-rata Harga per Kategori

```sql
SELECT kategori, AVG(harga) AS rata_harga
FROM buku
WHERE is_deleted = 0
GROUP BY kategori;
```

![Grouping 2](screenshot/12_group2.png)

Menampilkan rata-rata harga buku per kategori.

---

### 3.3 Kategori dengan Inventaris Terbesar

```sql
SELECT kategori, SUM(harga * stok) AS total_inventaris
FROM buku
WHERE is_deleted = 0
GROUP BY kategori
ORDER BY total_inventaris DESC
LIMIT 1;
```

![Grouping 3](screenshot/13_group3.png)

Menampilkan kategori dengan nilai inventaris terbesar.

---

## ✏️ 4. Update Data

### 4.1 Kenaikan Harga 5%

```sql
UPDATE buku 
SET harga = harga * 1.05
WHERE kategori = 'Programming';
```

![Update 1](screenshot/14_update1.png)

Melakukan update harga buku kategori Programming.

---

### 4.2 Penambahan Stok

```sql
UPDATE buku 
SET stok = stok + 10
WHERE stok < 5;
```

![Update 2](screenshot/15_update2.png)

Menambahkan stok untuk buku dengan stok rendah.

---

## 📋 5. Laporan Khusus

### 5.1 Buku Perlu Restock

```sql
SELECT * FROM buku 
WHERE stok < 5 AND is_deleted = 0;
```

![Laporan 1](screenshot/16_laporan1.png)

Menampilkan buku yang perlu ditambah stok.

---

### 5.2 Top 5 Buku Termahal

```sql
SELECT judul, harga FROM buku
WHERE is_deleted = 0
ORDER BY harga DESC
LIMIT 5;
```

![Laporan 2](screenshot/17_laporan2.png)

Menampilkan 5 buku dengan harga tertinggi.

---

## 🧠 Kesimpulan

Dari hasil eksplorasi database ini, dapat dipahami bahwa SQL sangat membantu dalam pengolahan data, baik untuk analisis maupun manipulasi data secara efisien.

---

## 📁 Struktur File

```
tugas-database/
├── query_tugas.sql
├── README.md
└── screenshot/
```
