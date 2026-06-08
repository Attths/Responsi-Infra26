# Analisis Perbaikan

## Permasalahan 1

### Gejala
command docker compose up -d langsung error saat di-run

### Penyebab
Baris ke-3 di docker-compose.yml tertulis services tanpa : (titik dua) sehingga tidak valid

### Solusi
Tambahkan : (titik dua) setelah services

###########################

## Permasalahan 2

### Gejala
Container web1 gagal terhubung ke database

### Penyebab
Nama service database di compose adalah db, bukan mysql

### Solusi
Ubah mysql pada DB_HOST menjadi "db" pada service web1

##########################

## Permasalahan 3

### Gejala
koneksi web2 ke mysql ditolak

### Penyebab
Password pada DB_PASS tidak cocok (wrongpassword) dengan password yang didefinisikan di service db

### Solusi
Ubah password dari wrongpassword menjadi student123

######################## 
