# Wer Server

Projek Membangun Web Server sebagai syarat kelulusan kelas Dicoding -Belajar Jaringan Komputer untuk Pemula- 
Semua file hasil konfigurasi dapat diakses pada : <br>
[Konfigurasi NGINX](https://github.com/Muhmdwild/dicoding-webserver/blob/main/default)<br>
[Konfigurasi Apache2](000-default.conf)<br>
[Konfigurasi Port Apache](ports.conf)<br>
[app.js](app.js)<br>

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


## Analisis Konfigurasi

Berikut ini adalah analisis konfigurasi web server sesuai dengan kriteria di atas :

```bash
# Dalam konfigurasi file pada direktory /etc/nginx/sites-available/default
# Reverse Proxy
location / {
		proxy_pass http://localhost:8000;
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection 'upgrade';
		proxy_set_header Host $host;
		proxy_cache_bypass $http_upgrade;
		
		limit_req zone=one;
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		# try_files $uri $uri/ =404;
	}

```
Baris ini mengarahkan semua permintaan yang cocok dengan blok location ini ke http://localhost:8000. Artinya, Nginx berfungsi sebagai reverse proxy yang meneruskan permintaan ke server aplikasi yang berjalan di port 8000 pada localhost.

```bash
# Dalam konfigurasi file pada direktory /etc/nginx/sites-available/default
# Menerapkan Limit Access di NGINX

limit_req_zone $binary_remote_addr zone=one:10m rate=6r/m;
```
Baris ini menjelaskan request yang dapat dilakukan adalah 6 request per menit atau 1 request setiap 10 detik.

```bash
# Dalam konfigurasi file pada direktory /etc/nginx/sites-available/default
# Merubah Port dari 80 menjadi 8000

server {
	listen 3000 default_server;
	listen [::]:3000 default_server;
```

Baris tersebut Digunakan untuk merubah port yang akan digunakan oleh Nginx.
