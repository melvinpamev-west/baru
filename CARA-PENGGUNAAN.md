# 📋 Panduan Lengkap Penggunaan Aplikasi Jaga Kantor

## 🎯 Sistem Autentikasi Role-Based

Aplikasi **Jaga Kantor** sekarang memiliki sistem autentikasi dengan role-based access control:

### 👮‍♂️ **ROLE SATPAM** - Hanya Input Laporan
- **URL**: `/dashboard`
- **Fitur**: Login, Register, Input laporan patroli
- **Akses**: Hanya bisa melihat dan membuat laporan sendiri

### 👨‍💼 **ROLE ADMIN** - Monitoring & Export
- **URL**: `/admin`
- **Fitur**: Monitoring semua laporan, export data, notifikasi
- **Akses**: Bisa melihat semua laporan dari semua satpam

---

## 🚀 Cara Mulai Menggunakan

### 1. **Buat Akun Demo**
Buka browser dan akses: `http://localhost:3000/api/setup-demo`

Akun demo akan otomatis dibuat:
- **Admin**: `admin@jagakantor.com` / `admin123`
- **Satpam**: `satpam@jagakantor.com` / `satpam123`

### 2. **Akses Login Page**
Buka: `http://localhost:3000/login`

---

## 👮‍♂️ PANDUAN UNTUK SATPAM

### 📱 Login sebagai Satpam
1. Buka `http://localhost:3000/login`
2. Masukkan email: `satpam@jagakantor.com`
3. Password: `satpam123`
4. Klik "Masuk"

### 📝 Membuat Laporan Patroli
Setelah login, satpam akan diarahkan ke `/dashboard`:

1. **Tab "Buat Laporan"** (Default)
   - Nama petugas sudah terisi otomatis
   - Pilih jenis kegiatan:
     - Patroli Rutin
     - Cek Pintu  
     - Cek Area
     - Insiden
   - Masukkan lokasi (bisa pilih dari badge)
   - Klik 📍 untuk dapatkan GPS otomatis
   - Tambah keterangan
   - Ambil foto bukti
   - Klik "Simpan Laporan"

2. **Tab "Riwayat Laporan"**
   - Lihat laporan yang sudah dibuat
   - (Fitur akan segera tersedia)

### 📸 Cara Upload Foto
- Klik tombol "Ambil Foto"
- Pilih "Take Photo" untuk foto baru
- Atau "Choose File" untuk upload dari galeri
- Foto akan muncul sebagai preview

### 📍 GPS Tracking Otomatis
- Klik tombol 📍 di sebelah "Koordinat GPS"
- Browser akan minta izin lokasi → klik "Allow"
- Koordinat akan terisi otomatis

---

## 👨‍💼 PANDUAN UNTUK ADMIN

### 🔐 Login sebagai Admin
1. Buka `http://localhost:3000/login`
2. Masukkan email: `admin@jagakantor.com`
3. Password: `admin123`
4. Klik "Masuk"

### 📊 Dashboard Admin Features
Admin akan diarahkan ke `/admin`:

1. **Statistik Real-time**
   - Total Laporan Hari Ini
   - Petugas Aktif
   - Lokasi Dipantau
   - Jumlah Insiden

2. **Notifikasi Real-time** 🔔
   - Klik lonceng di header kanan
   - Akan muncul notifikasi laporan baru
   - Notifikasi insiden berwarna merah

3. **Filter Laporan**
   - Filter berdasarkan tanggal
   - Filter berdasarkan nama petugas
   - Filter berdasarkan lokasi

4. **Tabel Laporan Lengkap**
   - Lihat semua laporan dari semua satpam
   - Klik 📷 untuk lihat foto bukti
   - Klik 👁️ untuk lihat lokasi di Google Maps
   - Export ke CSV

5. **Tab "Manajemen User"**
   - (Fitur akan segera tersedia)
   - Tambah, edit, nonaktifkan akun satpam

---

## 🔄 Alur Kerja Sistem Lengkap

### 🌅 Contoh Patroli Pagi:

**SATPAM (Budi Santoso):**
1. Login di HP/laptop → `/dashboard`
2. Buat laporan: "Pos Utama" → "Patroli Rutin"
3. Ambil foto pos jaga
4. Klik "Simpan Laporan"

**ADMIN (Di Kantor):**
1. Login di desktop → `/admin`
2. 🔔 Notifikasi muncul otomatis
3. Lihat laporan Budi di tabel
4. Cek foto dan lokasi GPS
5. Export data jika needed

### 🚨 Contoh Laporan Insiden:

**SATPAM Menemukan Insiden:**
1. Buat laporan → Jenis: "Insiden"
2. Lokasi: "Area Parkir"
3. Foto: Ambil foto kejadian
4. Keterangan: "Mobil mencurigakan"

**ADMIN Menerima Notifikasi:**
1. 🔔 Notifikasi merah muncul
2. Segera cek dashboard
3. Lihat foto dan lokasi GPS
4. Ambil tindakan lanjutan

---

## 📱 Cara Akses Mobile

### 📲 Dari HP Android/iPhone:
1. Buka browser (Chrome/Safari)
2. Ketik: `http://localhost:3000/login`
3. Login dengan akun satpam
4. Aplikasi responsif untuk mobile
5. Kamera HP bisa digunakan untuk foto

### 🖥️ Cara Akses Desktop:
1. Buka browser di laptop/PC
2. Login dengan akun admin
3. Dashboard lebih lebar untuk monitoring
4. Export data lebih mudah

---

## 🔐 Keamanan Sistem

### 🛡️ Proteksi Route:
- **Middleware** otomatis redirect ke login jika belum auth
- **Role-based access**: Satpam tidak bisa akses `/admin`
- **JWT Token**: Secure authentication dengan HTTP-only cookies
- **Password Hashing**: Menggunakan bcrypt untuk keamanan

### 🚫 Akses Terbatas:
- **Satpam**: Hanya bisa lihat laporan sendiri
- **Admin**: Bisa lihat semua laporan
- **Route Protection**: Otomatis redirect sesuai role

---

## 🆘 Troubleshooting

### ❌ Common Issues:

**Tidak bisa login:**
- Pastikan email dan password benar
- Coba akun demo yang tersedia
- Clear cache browser

**GPS tidak muncul:**
- Pastikan location service ON
- Allow browser access location
- Refresh browser dan coba lagi

**Foto tidak upload:**
- Check koneksi internet
- Pastikan file size < 10MB
- Coba dengan format JPG/PNG

**Redirect tidak berfungsi:**
- Clear browser cache
- Pastikan tidak ada error di console
- Refresh halaman

---

## 🎯 Best Practices

### ✅ Untuk Satpam:
- Selalu login sebelum mulai patroli
- Ambil foto bukti di setiap lokasi
- Isi keterangan yang jelas dan detail
- Pastikan GPS aktif untuk lokasi akurat
- Buat laporan tepat waktu

### ✅ Untuk Admin:
- Monitor dashboard secara berkala
- Segera cek notifikasi insiden
- Export data mingguan/bulanan
- Verifikasi lokasi dengan GPS
- Backup data penting

---

## 📈 Export Data

### 📊 Cara Export Laporan:
1. Login sebagai admin → `/admin`
2. Gunakan filter jika perlu
3. Klik tombol "Export CSV"
4. File otomatis diunduh
5. Buka di Excel untuk analisis

### 📋 Format Export:
- No, Nama Petugas, Lokasi
- Tanggal & Waktu, Jenis Kegiatan
- Keterangan, Koordinat GPS

---

## 🔗 Link Penting

- **Login**: `http://localhost:3000/login`
- **Register**: `http://localhost:3000/register`
- **Dashboard Satpam**: `http://localhost:3000/dashboard`
- **Dashboard Admin**: `http://localhost:3000/admin`
- **Setup Demo**: `http://localhost:3000/api/setup-demo`

---

## 🎉 Selamat Menggunakan!

Sistem **Jaga Kantor** sekarang sudah memiliki:
- ✅ **Autentikasi Role-Based** 
- ✅ **Dashboard Terpisah** untuk Satpam & Admin
- ✅ **Proteksi Route** Otomatis
- ✅ **Real-time Notifications**
- ✅ **Mobile Responsive**
- ✅ **Export Data**

**Satpam** fokus input laporan, **Admin** fokus monitoring! 🛡️