
# Crypto List - Tugas 3 MSIM4401

Aplikasi ini merupakan tugas dari mata kuliah **MSIM4401** yang bertujuan untuk menampilkan daftar cryptocurrency yang diambil dari API [CoinLore](https://api.coinlore.net/api/tickers/). Aplikasi ini dibangun menggunakan **Ionic Framework** dengan **Vue 3** dan menggunakan **TypeScript** untuk menjaga struktur data yang kuat.

## Fitur Utama
- Menampilkan ranking, nama, dan harga (USD) dari cryptocurrency.
- Memuat data secara dinamis melalui API saat pertama dijalankan dan menggunakan tombol **Refresh**.
- Tampilan tabel yang responsif dengan kolom **Rank**, **Bitcoin**, dan **USD**.
- Menampilkan pesan saat data belum dimuat.

## Cara Menjalankan Aplikasi
1. **Clone repository ini**:
   ```bash
   git clone <url-repository>
   cd <nama-folder>
   ```

2. **Install dependensi**:
   Jalankan perintah berikut untuk menginstal semua dependensi yang diperlukan:
   ```bash
   npm install
   ```

3. **Jalankan aplikasi**:
   Gunakan perintah berikut untuk menjalankan aplikasi:
   ```bash
   ionic serve
   ```

4. **Akses aplikasi**:
   Buka browser Anda dan akses aplikasi pada alamat:
   ```
   http://localhost:8100
   ```

## Teknologi yang Digunakan
- **Ionic Framework**: Untuk membangun aplikasi dengan desain responsif dan elemen-elemen UI yang modern.
- **Vue 3**: Framework JavaScript untuk membangun antarmuka pengguna.
- **TypeScript**: Untuk memastikan tipe data yang konsisten di seluruh aplikasi.
- **Axios**: Untuk melakukan permintaan HTTP ke API.


## Cara Kerja
1. Aplikasi memuat data cryptocurrency saat pertama kali dijalankan.
2. Klik tombol **Refresh** untuk **memuat ulang** data cryptocurrency.
3. Aplikasi akan mengirimkan permintaan ke API CoinLore untuk mendapatkan data cryptocurrency.
4. Data yang berhasil dimuat akan ditampilkan dalam tabel dengan kolom:
   - **Rank**: Ranking cryptocurrency.
   - **Bitcoin**: Nama cryptocurrency.
   - **USD**: Harga cryptocurrency dalam USD.

## Contoh Tampilan
**Tampilan saat data berhasil dimuat**:
```
| Rank | Name         | USD  |
| 1    | Bitcoin      | 27604.54   |
|------|--------------|------------|
| Rank | Name         | USD  |
| 2    | Ethereum     | 1720.54    |
|------|--------------|------------|
```


## Catatan
- Pastikan Anda memiliki koneksi internet yang aktif untuk memuat data dari API.
- Anda dapat memodifikasi proyek ini untuk menambahkan fitur lainnya, seperti pagination atau filter data cryptocurrency.

---
