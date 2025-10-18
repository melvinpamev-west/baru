# 📋 PANDUAN LENGKAP SISTEM JAGA KANTOR

## 🏢 Tentang Aplikasi

Jaga Kantor adalah sistem pelaporan patroli keamanan yang modern dan terintegrasi. Aplikasi ini dirancang khusus untuk mengelola laporan patroli keamanan kantor dengan fitur real-time monitoring dan notifikasi instan.

## 🚀 Fitur Utama

### ✨ Fitur yang Sudah Tersedia:
- **Landing Page Profesional** - Halaman utama dengan navigasi Sign In/Sign Up
- **Multi-Role Authentication** - Sistem login terpisah untuk Admin dan Satpam
- **Form Laporan Patroli** - Input laporan dengan foto, GPS, dan keterangan
- **Real-time Notifications** - Notifikasi instan untuk admin saat ada laporan baru
- **Filter & Export** - Filter laporan berdasarkan tanggal, petugas, lokasi
- **Reset Password** - Fitur lupa password dengan token reset
- **Ubah Email & Password** - Pengaturan akun untuk admin dan satpam
- **Responsive Design** - Tampilan optimal di desktop dan mobile

### 📱 Responsivitas
- ✅ Mobile-friendly navigation
- ✅ Touch-friendly buttons (minimum 44px)
- ✅ Responsive grid layouts
- ✅ Optimized for all screen sizes

## 👮‍♂️ Role & Akses

### 🔵 Admin (Administrator)
- **Email Default**: `admin@jagakantor.com`
- **Password Default**: `admin123`
- **Akses Penuh**: Monitor semua laporan, export data, kelola user
- **Dashboard**: `/admin`

### 🟢 Satpam (Petugas Keamanan)
- **Registrasi**: Bisa daftar akun baru
- **Akses Terbatas**: Hanya submit laporan patroli
- **Dashboard**: `/dashboard`

## 🛠️ Instalasi & Setup

### 1. Inisialisasi Admin Default
```bash
# Jalankan sekali untuk membuat admin default
curl -X POST http://localhost:3000/api/init-admin
```

### 2. Akses Aplikasi
- **URL**: `http://localhost:3000`
- **Landing Page**: Halaman utama dengan tombol Sign In/Sign Up

## 🔐 Keamanan

### ✅ Fitur Keamanan:
- **Password Hashing** - Menggunakan bcrypt
- **JWT Authentication** - Token-based authentication
- **Role-based Access Control** - Akses berdasarkan peran
- **HTTP-only Cookies** - Secure token storage
- **Input Validation** - Validasi data di server & client
- **SQL Injection Protection** - Menggunakan Prisma ORM

### 🔒 Password Requirements:
- Minimal 6 karakter
- Bisa mengubah password di menu Settings
- Reset password via email (development: token ditampilkan di response)

## 📱 Cara Penggunaan

### Untuk Admin:

1. **Login**
   - Buka `http://localhost:3000/login`
   - Email: `admin@jagakantor.com`
   - Password: `admin123`

2. **Dashboard Admin**
   - Monitor semua laporan patroli
   - Filter berdasarkan tanggal/petugas/lokasi
   - Export data ke CSV/Excel
   - Terima notifikasi real-time

3. **Ubah Email/Password**
   - Menu Settings → Pengaturan
   - Bisa ubah email dan password
   - Memerlukan password lama untuk konfirmasi

### Untuk Satpam:

1. **Registrasi (Baru)**
   - Buka `http://localhost:3000/register`
   - Isi nama, email, password
   - Otomatis role SATPAM

2. **Login**
   - Buka `http://localhost:3000/login`
   - Gunakan email dan password yang didaftarkan

3. **Buat Laporan**
   - Pilih lokasi patroli
   - Pilih jenis aktivitas
   - Upload foto bukti (opsional)
   - Isi keterangan
   - Submit laporan

4. **Pengaturan Akun**
   - Menu Settings → Pengaturan
   - Bisa ubah email dan password

## 🌐 API Endpoints

### Authentication:
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user

### Password Reset:
- `POST /api/reset-password` - Request reset token
- `POST /api/reset-password` (dengan token) - Reset password

### Update Profile:
- `PUT /api/update-email` - Update email user

### Patrol Reports:
- `GET /api/patrol-reports` - Get all reports (admin only)
- `POST /api/patrol-reports` - Create new report

### Setup:
- `POST /api/init-admin` - Initialize admin default

## 📊 Struktur Database

### Users Table:
```sql
- id (String, Primary Key)
- name (String)
- email (String, Unique)
- password (String, Hashed)
- role (Enum: ADMIN, SATPAM)
- createdAt (DateTime)
- updatedAt (DateTime)
```

### PatrolReports Table:
```sql
- id (String, Primary Key)
- officerName (String)
- location (String)
- coordinates (String, Optional)
- activityType (Enum)
- description (String, Optional)
- photoUrl (String, Optional)
- timestamp (DateTime)
- createdAt (DateTime)
- updatedAt (DateTime)
```

## 🎨 UI/UX Design

### Design System:
- **Color Scheme**: Blue primary, gray neutral
- **Typography**: Clean, modern font hierarchy
- **Components**: Shadcn/ui component library
- **Icons**: Lucide React icons
- **Responsive**: Mobile-first design

### Accessibility:
- Semantic HTML5 elements
- ARIA labels and roles
- Keyboard navigation support
- Screen reader compatibility
- High contrast colors

## 🚨 Troubleshooting

### Common Issues:

1. **Login Gagal**
   - Pastikan email dan password benar
   - Cek role user (ADMIN/SATPAM)
   - Clear browser cache

2. **Tidak Bisa Submit Laporan**
   - Pastikan semua field required diisi
   - Cek koneksi internet
   - Refresh halaman dan coba lagi

3. **Reset Password Tidak Berhasil**
   - Pastikan token valid (1 hour expiry)
   - Cek email sudah terdaftar atau belum
   - Password minimal 6 karakter

4. **Notifikasi Tidak Muncul**
   - Pastikan WebSocket terhubung
   - Refresh browser
   - Cek browser console untuk error

## 📞 Support

### Technical Support:
- **Error Logs**: Cek browser console dan server logs
- **Database**: Verify Prisma connection
- **Environment**: Check .env configuration

### Development:
```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Run linting
npm run lint
```

## 🔄 Update & Maintenance

### Regular Tasks:
1. **Backup Database** - Export data regularly
2. **Update Dependencies** - Keep packages updated
3. **Security Audit** - Check for vulnerabilities
4. **Performance Monitoring** - Monitor app performance

### Future Enhancements:
- [ ] Push notifications mobile
- [ ] Advanced analytics dashboard
- [ ] Multi-location support
- [ ] Integration with CCTV systems
- [ ] Offline mode support

## 📝 Notes

### Security Best Practices:
- ✅ Regular password updates
- ✅ Monitor failed login attempts
- ✅ Keep software updated
- ✅ Use HTTPS in production
- ✅ Regular security audits

### Performance Tips:
- ✅ Optimize image uploads
- ✅ Implement caching strategies
- ✅ Monitor database queries
- ✅ Use CDN for static assets

---

## 🎉 Selamat Menggunakan!

Sistem Jaga Kantor siap digunakan. Untuk pertanyaan atau bantuan teknis, silakan merujuk ke dokumentasi ini atau menghubungi tim support.

**Admin Default**: `admin@jagakantor.com` / `admin123`

*Versi 1.0.0 - Production Ready*