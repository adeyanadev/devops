# Tutorial Manage Server

## 1. SSH via Terminal

SSH (Secure Shell) adalah protokol aman untuk mengakses server dari terminal. SSH sering digunakan untuk login remote, menjalankan perintah, dan mentransfer file secara aman.

### 1.1. Menghubungkan ke server
```bash
ssh username@alamat_server
```

### Contoh
```bash
ssh root@192.168.1.10
```

### 1.2. Menggunakan port tertentu
Jika server SSH tidak berjalan di port 22, gunakan opsi `-p`:
```bash
ssh -p 2222 username@alamat_server
```

### 1.3. Cara kerja autentikasi SSH
SSH dapat menggunakan dua metode autentikasi:
- password
- kunci SSH (lebih aman dan disarankan)

Biasanya jika Anda belum membuat kunci, SSH akan meminta password saat login. Ini tetap bisa dipakai, tetapi kurang aman dibandingkan menggunakan kunci SSH.

### 1.4. Membuat kunci SSH
SSH key dibuat di komputer lokal Anda, lalu dipasangkan ke server atau VM agar Anda bisa login dengan aman.

Langkahnya sangat sederhana:

1. Buka terminal di komputer Anda.
2. Jalankan perintah berikut:

```bash
ssh-keygen
```

Jika ingin memberi nama kunci sendiri, Anda bisa gunakan perintah berikut:

```bash
ssh-keygen -f ~/.ssh/nama_kunci
```

Penjelasan per bagian:
- `ssh-keygen` = perintah untuk membuat pasangan kunci SSH
- `-f ~/.ssh/nama_kunci` = memberi nama file kunci secara manual
- Anda bisa langsung menekan Enter untuk pilihan default lainnya
- Jika ingin, Anda bisa mengisi passphrase, tetapi bisa juga dikosongkan

Biasanya Anda akan melihat pertanyaan seperti ini:
- lokasi file: `~/.ssh/id_ed25519`
- passphrase: bisa dikosongkan jika tidak ingin memakai kata sandi tambahan

Jika Anda tekan Enter untuk semua pilihan, maka kunci akan dibuat otomatis.

### 1.5. Hasil dari proses pembuatan kunci
Setelah proses selesai, biasanya akan ada dua file di folder `~/.ssh`:
- `id_ed25519` = private key, simpan di komputer lokal dan jangan dibagikan
- `id_ed25519.pub` = public key, file ini yang dipasang ke server

Jadi inti pemahamannya adalah:
- private key ada di lokal Anda
- public key dipasang ke server
- saat login, server akan mengecek apakah kunci yang Anda punya cocok

### 1.6. Memasangkan public key ke server
Setelah kunci dibuat, langkah berikutnya adalah menaruh public key ke server.

Jika Anda menggunakan perintah berikut:

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub username@alamat_server
```

maka public key akan otomatis ditambahkan ke server.

Jika perintah `ssh-copy-id` tidak tersedia, Anda bisa lakukan cara manual:

```bash
cat ~/.ssh/id_ed25519.pub
```

Salin hasilnya, lalu tempelkan ke file berikut di server:

```bash
~/.ssh/authorized_keys
```

### 1.7. Login menggunakan kunci SSH
Setelah public key berhasil dipasang, Anda bisa login ke server dengan perintah berikut:

```bash
ssh -i ~/.ssh/id_ed25519 username@alamat_server
```

Jika berhasil, Anda akan masuk ke server tanpa harus memasukkan password.

### 1.8. SSH tanpa password (cara paling umum)
Jika Anda ingin login ke server tanpa password, cara yang paling umum adalah memakai kunci SSH. Prinsipnya sederhana:

1. Anda membuat kunci di komputer lokal.
2. Public key Anda dikirim ke server.
3. Saat Anda login, server akan memeriksa kunci tersebut.
4. Kalau cocok, server mengizinkan Anda masuk tanpa meminta password.

Langkah-langkahnya:

#### Langkah 1: Buat kunci SSH di komputer lokal
```bash
ssh-keygen
```

Tekan Enter beberapa kali sampai proses selesai.

#### Langkah 2: Lihat isi public key
```bash
cat ~/.ssh/id_rsa.pub
```

Jika Anda memberi nama kunci sendiri, misalnya `nama_kunci`, maka file public key-nya biasanya ada di:
```bash
~/.ssh/nama_kunci.pub
```

#### Langkah 3: Tempelkan public key ke server
Gunakan perintah berikut:

```bash
ssh-copy-id username@alamat_server
```

Jika diminta, masukkan password akun server sekali saja. Setelah itu, public key akan ditambahkan ke server.

#### Langkah 4: Coba login lagi
```bash
ssh username@alamat_server
```

Kalau setup berhasil, Anda tidak perlu memasukkan password lagi.

#### Jika `ssh-copy-id` tidak tersedia
Anda bisa lakukan secara manual:

```bash
cat ~/.ssh/id_rsa.pub
```

Lalu tempelkan isi hasilnya ke file berikut di server:

```bash
~/.ssh/authorized_keys
```

### 1.9. Menguji koneksi SSH
```bash
ssh -v username@alamat_server
```

Perintah `-v` membantu melihat proses autentikasi dan mencari masalah jika login gagal.

### 1.9. Menutup koneksi
```bash
exit
```

### 1.10. Tips keamanan SSH
- Jangan memakai root login secara langsung jika tidak perlu
- Gunakan kunci SSH daripada password
- Batasi akses port SSH hanya dari IP tertentu
- Ganti port default jika diperlukan
- Selalu jaga file private key tetap aman

---

## 2. Text Manipulation & Monitoring

Berikut beberapa perintah untuk memanipulasi teks dan memantau sistem.

### Melihat isi file
```bash
cat file.txt
```

### Mencari teks dalam file
```bash
grep "kata" file.txt
```

### Menampilkan baris tertentu
```bash
sed -n '1,10p' file.txt
```

### Memantau log secara real-time
```bash
tail -f /var/log/syslog
```

### Melihat proses yang berjalan
```bash
ps aux
```

### Melihat penggunaan sumber daya
```bash
top
```

---

## 3. System Management

Perintah dasar untuk mengelola sistem Linux/Ubuntu.

### Memeriksa informasi sistem
```bash
uname -a
```

### Melihat penggunaan disk
```bash
df -h
```

### Melihat penggunaan memori
```bash
free -h
```

### Mengelola layanan
```bash
systemctl status nginx
systemctl restart nginx
systemctl stop nginx
```

### Mengupdate sistem
```bash
sudo apt update
sudo apt upgrade
```

### Menginstal paket
```bash
sudo apt install nginx
```
