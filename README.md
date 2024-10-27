# Wer Server

Projek Membangun Web Server sebagai syarat kelulusan kelas Dicoding-Belajar Jaringan Komputer untuk Pemula- 

## Kriteria

1. Menyiapkan Web Server
Langkah pertama yang perlu dilakukan dalam membangun web server adalah melakukan persiapan terlebih dahulu. Persiapan ini mencakup beberapa hal berikut ini.
Melakukan cloning dari repositori GitHub yang sudah disediakan
Memasang NGINX.
Memastikan web server Node.js dan NGINX sama-sama bisa diakses dengan baik.

2. Mengonfigurasi NGINX sebagai Reverse Proxy Server
Setelah kriteria 1 berhasil Anda kerjakan, lanjutlah menyelesaikan kriteria 2. Di kriteria ini, Anda diminta untuk mengonfigurasi NGINX yang sudah terinstal supaya menjadi reverse proxy server. Ini bertujuan agar saat diakses melalui port 80 (yang digunakan oleh NGINX), permintaan atau request dapat diteruskan ke web server.

3. Menerapkan Limit Access di NGINX
Usai menyelesaikan kriteria 2, lanjutkan pengerjaan proyek akhir Anda dengan mengerjakan kriteria 3. Kriteria ini meminta Anda untuk mengonfigurasikan NGINX (alias reverse proxy server) untuk menerapkan limit access atau rate limit guna meningkatkan keamanan pada web server. 


## Langkah Penyelesaian

Langkah-langkah untuk menginstal proyek ini secara lokal :

```bash
# Clone repository ini
git clone https://github.com/username/nama-proyek.git

# Masuk ke direktori proyek
cd nama-proyek

# Instal dependencies
npm install
