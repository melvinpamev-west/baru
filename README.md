# Aplikasi Jaga Kantor - Sistem Keamanan Terpadu

## 📋 Deskripsi

Aplikasi **Jaga Kantor** adalah sistem keamanan terpadu yang dirancang khusus untuk mendukung tugas satuan pengamanan (Satpam) dalam mengawasi, mencatat, dan melaporkan kegiatan patroli secara real-time.

## 🎯 Fitur Utama

### 1. 📍 Pencatatan Lokasi Otomatis (GPS Tracking)
- Rekam titik lokasi (koordinat GPS) otomatis
- Timestamp real-time untuk setiap laporan
- Nama petugas tercatat secara otomatis

### 2. 📸 Upload Bukti Foto
- Ambil foto langsung melalui aplikasi
- Preview foto sebelum menyimpan
- Foto tersimpan dengan cap waktu dan lokasi

### 3. 📝 Laporan Patroli Digital
- Format laporan yang rapi dan terstruktur
- Data lengkap: nama petugas, lokasi, waktu, jenis kegiatan, bukti foto, keterangan
- Pencarian dan filter yang mudah

### 4. 🌐 Dashboard Website Admin
- Monitoring real-time semua laporan patroli
- Filter berdasarkan tanggal, petugas, atau area
- Export laporan dalam format CSV
- Statistik dashboard yang informatif

### 5. 🔔 Notifikasi Real-time
- Notifikasi otomatis ke admin saat ada laporan baru
- Sistem notifikasi berbasis WebSocket
- Browser notification support

## 🛠️ Teknologi yang Digunakan

- **Frontend**: Next.js 15 dengan App Router, TypeScript, Tailwind CSS
- **UI Components**: shadcn/ui dengan Lucide icons
- **Backend**: Next.js API Routes dengan Prisma ORM
- **Database**: SQLite
- **Real-time**: Socket.IO untuk notifikasi real-time
- **Styling**: Tailwind CSS dengan tema yang responsif

## 📊 Struktur Database

### User Model
- `id`, `email`, `name`, `role` (SATPAM/ADMIN), `createdAt`, `updatedAt`

### PatrolReport Model
- `id`, `officerName`, `location`, `coordinates`, `activityType`
- `description`, `photoUrl`, `timestamp`, `createdAt`, `updatedAt`
- `reportedBy`, `userId` (relation ke User)

## 🚀 Cara Penggunaan

### Membuat Laporan Patroli Baru
1. Klik tab "Buat Laporan Baru"
2. Isi nama petugas (wajib)
3. Pilih jenis kegiatan (Patroli Rutin, Cek Pintu, Cek Area, Insiden)
4. Masukkan lokasi patroli (bisa pilih dari lokasi umum)
5. Klik tombol GPS untuk mendapatkan koordinat otomatis
6. Tambahkan keterangan jika diperlukan
7. Ambil foto sebagai bukti (opsional)
8. Klik "Simpan Laporan"

### Memantau Laporan
1. Di tab "Laporan Patroli", semua laporan akan ditampilkan dalam tabel
2. Gunakan filter untuk menyaring laporan berdasarkan:
   - Tanggal
   - Nama petugas
   - Lokasi
3. Klik ikon kamera untuk melihat foto bukti
4. Klik ikon mata untuk melihat lokasi di Google Maps
5. Export laporan ke CSV dengan tombol "Export CSV"

### Notifikasi Real-time
- Notifikasi akan muncul otomatis saat ada laporan baru
- Klik lonceng notifikasi di header untuk melihat daftar notifikasi
- Notifikasi insiden akan ditandai dengan warna merah

## 📱 Jenis Kegiatan Patroli

1. **Patroli Rutin** - Patroli terjadwal reguler
2. **Cek Pintu** - Pemeriksaan keamanan pintu dan akses
3. **Cek Area** - Pemeriksaan area tertentu
4. **Insiden** - Pelaporan insiden atau kejadian penting

## 🌟 Lokasi Umum yang Tersedia

- Pos Utama
- Area Parkir
- Gudang
- Lantai 1, 2, 3
- Ruang Server
- Kantin
- Lobby Utama
- Area Rawan

## 🔧 API Endpoints

### GET `/api/patrol-reports`
- Mendapatkan semua laporan patroli
- Support query parameters: `date`, `officer`, `location`

### POST `/api/patrol-reports`
- Membuat laporan patroli baru
- Required fields: `officerName`, `location`, `activityType`

### GET `/api/patrol-reports/[id]`
- Mendapatkan detail laporan spesifik

### PUT `/api/patrol-reports/[id]`
- Mengupdate laporan patroli

### DELETE `/api/patrol-reports/[id]`
- Menghapus laporan patroli

### GET `/api/patrol-reports/export`
- Export laporan ke CSV
- Support query parameters untuk filter

## 📈 Statistik Dashboard

- **Total Laporan Hari Ini** - Jumlah laporan yang dibuat hari ini
- **Petugas Aktif** - Jumlah petugas yang telah membuat laporan
- **Lokasi Dipantau** - Jumlah lokasi unik yang dipantau
- **Insiden** - Jumlah laporan insiden

## 🎨 Desain & UX

- **Responsive Design** - Optimal di desktop, tablet, dan mobile
- **Dark Mode Support** - Dapat beralih ke tema gelap
- **Accessibility** - Semantic HTML dan ARIA support
- **Loading States** - Indikator loading untuk async operations
- **Error Handling** - Pesan error yang jelas dan actionable

## 🔒 Keamanan

- Input validation di server dan client
- SQL injection prevention dengan Prisma ORM
- File upload security
- CORS configuration

## 📝 Catatan Pengembangan

- Aplikasi dibuat dengan Next.js 15 dan App Router
- Menggunakan TypeScript untuk type safety
- Database SQLite untuk kemudahan development
- Socket.IO untuk real-time notifications
- Komponen UI dari shadcn/ui untuk konsistensi desain

---

**Jaga Kantor** - Solusi keamanan terpadu untuk kantor modern.