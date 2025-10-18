# 🚀 SETUP CEPAT - JAGA KANTOR

## 📋 Langkah 1: Buat Admin Default

Buka browser dan akses:
```
http://localhost:3000/api/init-admin
```

**Response yang diharapkan:**
```json
{
  "message": "Admin created successfully",
  "admin": {
    "email": "admin@jagakantor.com",
    "name": "Administrator",
    "password": "admin123"
  }
}
```

## 🔑 Langkah 2: Login Admin

1. Buka: `http://localhost:3000/login`
2. Email: `admin@jagakantor.com`
3. Password: `admin123`

## 👥 Langkah 3: Registrasi Satpam

1. Klik tombol "Sign Up" di kanan atas
2. Atau buka: `http://localhost:3000/register`
3. Isi data satpam (nama, email, password)
4. Otomatis dapat role SATPAM

## ✅ SELESAI!

Sistem sudah siap digunakan:
- **Admin**: Monitor laporan, export data, kelola user
- **Satpam**: Submit laporan patroli harian

## 📱 Fitur Tersedia:
- ✅ Landing Page profesional
- ✅ Responsive di HP/Desktop
- ✅ Reset password & ubah email
- ✅ Real-time notifications
- ✅ Filter & export laporan
- ✅ Keamanan berlapis

---
*Untuk panduan lengkap, lihat file `PANDUAN-LENGKAP.md`*