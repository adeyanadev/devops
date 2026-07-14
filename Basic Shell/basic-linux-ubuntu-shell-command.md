# Basic Linux Ubuntu Shell Command

Dokumen ini berisi beberapa perintah shell dasar yang sering digunakan di Linux Ubuntu.

## Navigasi folder
- `pwd` : melihat direktori saat ini
- `ls` : melihat isi folder
- `ls -la` : melihat isi folder termasuk file tersembunyi
- `cd <nama_folder>` : masuk ke folder tertentu
- `cd ..` : kembali ke folder sebelumnya

## Mengelola file dan folder
- `mkdir <nama_folder>` : membuat folder baru
- `rmdir <nama_folder>` : menghapus folder kosong
- `rm <nama_file>` : menghapus file
- `rm -r <nama_folder>` : menghapus folder beserta isinya
- `cp <file_asal> <file_tujuan>` : menyalin file
- `mv <file_asal> <file_tujuan>` : memindahkan atau mengubah nama file

## Melihat isi file
- `cat <nama_file>` : melihat isi file
- `less <nama_file>` : melihat isi file halaman per halaman
- `head <nama_file>` : melihat 10 baris pertama
- `tail <nama_file>` : melihat 10 baris terakhir

## Manajemen proses
- `ps` : melihat proses yang sedang berjalan
- `top` : melihat proses secara real-time
- `kill <pid>` : menghentikan proses berdasarkan ID

## Akses root dan izin
- `sudo <perintah>` : menjalankan perintah dengan hak admin
- `chmod +x <nama_file>` : memberi izin eksekusi
- `chown <user>:<group> <file>` : mengubah pemilik file

## Informasi sistem
- `whoami` : melihat user yang sedang login
- `uname -a` : melihat informasi kernel
- `df -h` : melihat penggunaan disk
- `free -h` : melihat penggunaan memori

## Pencarian dan filter
- `find <lokasi> -name <nama_file>` : mencari file berdasarkan nama
- `grep <kata> <nama_file>` : mencari teks di dalam file
- `grep -R <kata> <folder>` : mencari teks secara rekursif di folder

## Arsip dan kompresi
- `tar -cvf <file.tar> <folder>` : membuat arsip tar
- `tar -xvf <file.tar>` : mengekstrak arsip tar
- `tar -czvf <file.tgz> <folder>` : membuat arsip gzip
- `tar -xzvf <file.tgz>` : mengekstrak arsip gzip

## History dan bantuan
- `history` : melihat riwayat perintah yang pernah dijalankan
- `man <perintah>` : melihat manual halaman perintah
- `<perintah> --help` : melihat opsi bantuan singkat dari suatu perintah

## Pengguna dan hak akses
- `whoami` : menampilkan nama user saat ini
- `id` : menampilkan ID user dan grup
- `sudo -i` : masuk ke shell root secara interaktif
- `su <nama_user>` : berpindah ke user lain

## Jaringan dasar
- `ip a` : melihat alamat IP dan antarmuka jaringan
- `ping <alamat>` : menguji koneksi ke host tertentu
- `curl <url>` : mengunduh konten dari URL
- `wget <url>` : mengunduh file dari URL

## Paket dan instalasi
- `apt update` : memperbarui daftar paket
- `apt upgrade` : meng-upgrade paket yang terinstal
- `apt install <nama_paket>` : menginstal paket baru
- `apt remove <nama_paket>` : menghapus paket
- `apt search <kata_kunci>` : mencari paket yang tersedia

## Sistem dan log
- `df -h` : melihat kapasitas disk
- `du -sh <folder>` : melihat ukuran folder
- `journalctl` : melihat log sistem
- `tail -f /var/log/syslog` : mengikuti log secara real-time

## Shell scripting sederhana
Contoh script bash dasar:

```bash
#!/bin/bash
echo "Halo, dunia!"
name="Ubuntu"
echo "Selamat datang di $name"
```

Cara mengeksekusi:

```bash
chmod +x nama_script.sh
./nama_script.sh
```

## Tips praktis
- Gunakan tab untuk melengkapi nama file atau folder secara otomatis
- Gunakan panah atas untuk mengulang perintah sebelumnya
- Gabungkan perintah dengan `&&` untuk menjalankan berurutan jika berhasil
- Gunakan `|` untuk mengalirkan output ke perintah lain

## Ringkasan
Dokumen ini memberikan dasar yang cukup lengkap untuk bekerja dengan shell Linux Ubuntu secara efektif.
