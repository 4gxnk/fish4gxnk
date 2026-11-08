# 🐟 Fish Hastle Auto Bot

Automation script (Auto-Clicker, Auto-Cast, Auto-Sell, dll) for Fish Hastle game via Telegram MiniApp. 

---

## 📱 Cara Install & Menjalankan di Termux (Android)


### Langkah 1: Persiapan Termux & Install Ubuntu
Buka aplikasi Termux Anda dan jalankan perintah berikut secara berurutan:

```bash
# 1. Update Termux
pkg update -y && pkg upgrade -y

# 2. Install X11
pkg update && pkg install x11-repo -y
‎pkg install termux-x11-nightly -y

# 3. Install proot-distro
pkg install proot-distro -y

# 4. Install Ubuntu di dalam Termux
proot-distro install ubuntu

# 4. Masuk ke environment Ubuntu
proot-distro login ubuntu
# atau
proot-distro login ubuntu --shared-tmp
```

### Langkah 2: Install Dependensi Python di Ubuntu
Setelah berhasil masuk ke Ubuntu (ditandai dengan prompt `root@localhost`), jalankan:

```bash
# 1. Update sistem Ubuntu & Install Python dan pip
apt update && apt install python3 python3-pip python3-venv -y
# 2. install git
apt install git
```

### Langkah 3: Setup Script & Playwright
```bash
# 1. Clone repository ini
git clone https://github.com/4gxnk/4GXNK-ENGINE-V9.2---Fish-Hastle-Auto-Bot

# 2. Install library Python
pip install -r requirements.txt

# 3. Install browser Chromium untuk Playwright
playwright install chromium

# 4. Install dependensi sistem yang dibutuhkan Chromium
playwright install-deps
```
### Langkah Opsional: Menampilkan Visual (termux x11)
```bash
# 1. buka sesi termux baru

# 2. masukan command
termux-x11 :0 &

# 3. balik ke sesi 1 login ubuntu
proot-distro login ubuntu --shared-tmp
export DISPLAY=:0
‎export LIBGL_ALWAYS_SOFTWARE=1
‎export MESA_LOADER_DRIVER_OVERRIDE=swrast

# 4. mematikan termux x11
pkill -f termux-x11
‎pkill -f Xorg
‎pkill -f X
‎```


### Langkah 4: Menjalankan Script
Pastikan file script utama kamu (misal: `auto.py`) dan `config.json` sudah ada di dalam folder. 
*(Gunakan `nano config.json` untuk mengubah mode script).*

```bash
# Jalankan bot
python3 auto.py
```
> **Catatan:** Untuk pemakaian berikutnya, Anda hanya perlu membuka Termux lalu mengetik:
> `proot-distro login ubuntu` ➡️ `cd fish4gxnk` ➡️ `python3 auto.py`

---

## ⚙️ Konfigurasi (`config.json`)

Script ini membaca pengaturan dari file `config.json` secara otomatis. Jika belum ada, script akan membuatnya di run pertama.
```json
{
    "HEADLESS_MODE": true,
    "ENABLE_SESSION_1": true,
    "ENABLE_SESSION_2": false
}
```
*   `HEADLESS_MODE`: `true` untuk menjalankan tanpa layar GUI ( `true` untuk Termux/VPS agar ringan dan tidak crash).
*   `ENABLE_SESSION_1` & `2`: Ubah ke `true` atau `false` untuk mengaktifkan/menonaktifkan akun atas/bawah.

---

## 🎮 Daftar Perintah (Command Line)
Saat script berjalan, Anda bisa mengontrol bot secara real-time melalui terminal.
*Format penulisan:* `<target> <perintah> <nilai>`
*(Target: `1` untuk akun atas, `2` untuk akun bawah, `all` untuk keduanya)*

### Command Dasar
*   `all auto on` : Menyalakan fitur Native Auto bawaan game untuk semua akun.
*   `1 click on` : Menyalakan fast-clicker pada akun 1.
*   `2 speed 1.5`: Mengaktifkan speedhack 1.5x pada akun 2.
*   `all sell on` : Menyalakan Auto-Sell.
*   `all lock 5`  : Mengunci ikan dengan Rarity 5 ke atas (tidak akan dijual otomatis).

### Fitur Map & Pathfinding
*   `1 map <id map>`  : Pindah pulau otomatis.
*   `all water`   : Karakter otomatis berjalan mencari air terdekat untuk memancing.

### Fitur Shop & Gacha
*   `1 shop` : Membuka UI Toko.
*   `1 buy luck 5` : Membeli item (contoh ID: luck) sebanyak 5 buah secara instan.
*   `all gacha free` : Mengambil hadiah Gacha gratis harian.
*   `all altar` : Berdoa di altar secara otomatis untuk mendapatkan koin.

### Command Global
*   `refresh 15` : Mengatur agar halaman game di-refresh otomatis setiap 15 menit (mencegah lag/freeze).
*   `exit` : Menghentikan script dan menyimpan sesi dengan aman.

---

## ⚠️ Troubleshooting
*   **Akses Ditolak (Nomor Tidak Terdaftar):** Pastikan admin sudah memasukkan nomor Telegram Anda, https://t.me/jcolm.
*   **Koneksi Telegram Terputus / Minta Nomor Terus:** Hapus file `session.session` dan `session2.session` di folder Anda, lalu jalankan ulang agar script meminta kode OTP baru.