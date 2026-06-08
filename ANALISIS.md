# Analisis Perbaikan

## Permasalahan 1

### Gejala
command docker compose up -d langsung error saat di-run

### Penyebab
Baris ke-3 di docker-compose.yml tertulis services tanpa : (titik dua) sehingga tidak valid

### Solusi
Tambahkan : (titik dua) setelah services

## Permasalahan 2

### Gejala
Container web1 gagal terhubung ke database

### Penyebab
Nama service database di compose adalah db, bukan mysql

### Solusi
Ubah mysql pada DB_HOST menjadi "db" pada service web1

## Permasalahan 3

### Gejala
koneksi web2 ke mysql ditolak

### Penyebab
Password pada DB_PASS tidak cocok (wrongpassword) dengan password yang didefinisikan di service db

### Solusi
Ubah password dari wrongpassword menjadi student123

## Permasalahan 4

### Gejala
docker compose build gagal untuk service web3

### Penyebab
folder web pada context di service web3 tertulis ./web33

### Solusi
Ubah ./web33 menjadi ./web3 di service web3 bagian context

## Permasalahan 5

### Gejala
nginx tidak bisa meneruskan request ke web3, karena networks yang tertulis hanya backend

### Penyebab
Network isolation di Docker

### Solusi
Tambahkan frontend ke networks web3

## Permasalahan 6

### Gejala
Docker compose error "volume db-data declared but not defined"

### Penyebab
Service db merujuk volume db-data, tapi bagian volumes: di atas hanya mendefinisikan database-data

### Solusi
Samakan namanya di bagian volumes: bawah dari database-data menjadi db-data


## Permasalahan 7 (nginx.conf)

### Gejala
web1 tidak akan pernah menerima traffic sama sekali

### Penyebab
Nama service di docker-compose yang tertulis adalah web11:80 bukan web1:80

### Solusi
Ubah nama servicenya dari web11 menjadi web1 di file nginx.conf

## Permasalahan 8

### Gejala
request ke web3 selalu gagal

### Penyebab
Apache dalam web3 tertulis 8080

### Solusi
Ubah port 8080 di web3 menjadi "server web3:80;" 

## Permasalahan 9

### Gejala
nginx gagal start dengan error unexpected nginx

### Penyebab
file diawali dengan nginx dan diakhiri (`)

## Permasalahan 10 (Dockerfile web1 dan web3)

### Gejala
docker compose build langsung gagal dengan error image not found

### Penyebab
terdapat typo (apach) di web1 dan (apche) di web3 

### Solusi
perbaiki nama (apach) dan (apche)  menjadi (apache)
