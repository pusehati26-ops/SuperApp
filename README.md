# GWG Super App v3.1 — Generasi Wangi Group

Sistem Manajemen Konsinyasi berbasis web dengan Firebase Realtime Database.

---

## ✅ Fitur v3.1

| Fitur | Status |
|-------|--------|
| ☁️ Sinkronisasi real-time (Firebase) | ✅ |
| 🔐 Login Google (halaman login tersendiri) | ✅ |
| 👤 Multi-user dengan role (Admin/Manajer/Sales) | ✅ |
| 📄 Ekspor PDF Landscape profesional | ✅ |
| 🟢 Ekspor Excel (.xlsx) | ✅ |
| 🚀 Deploy Netlify (build config lengkap) | ✅ |

---

## 🔧 Setup Firebase (WAJIB untuk sinkronisasi & login)

### Langkah 1: Buat Project Firebase
1. Buka https://console.firebase.google.com
2. Klik **"Add project"** → beri nama (mis: `gwg-super-app`)
3. Nonaktifkan Google Analytics (opsional) → **Create project**

### Langkah 2: Tambah Web App
1. Di dashboard project → klik ikon **Web** (`</>`)
2. Nama: `GWG Super App` → **Register app**
3. **Salin** nilai `firebaseConfig` yang muncul

### Langkah 3: Aktifkan Realtime Database
1. Menu kiri → **Build → Realtime Database**
2. **Create Database** → pilih region (asia-southeast1 / Singapore)
3. Pilih **"Start in test mode"** → Enable

### Langkah 4: Aktifkan Google Sign-In
1. Menu kiri → **Build → Authentication**
2. **Get started** → tab **Sign-in method**
3. Klik **Google** → Enable → pilih support email → **Save**

### Langkah 5: Paste Config ke Source Code

Buka file `src/GWG_SuperApp.jsx`, cari baris ini di bagian atas:
```js
const FIREBASE_CONFIG = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  ...
};
```

Ganti dengan config dari Langkah 2:
```js
const FIREBASE_CONFIG = {
  apiKey: "AIzaSy...",
  authDomain: "gwg-super-app.firebaseapp.com",
  databaseURL: "https://gwg-super-app-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "gwg-super-app",
  storageBucket: "gwg-super-app.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890",
};
```

---

## 👥 Sistem Role

| Role | Dashboard | Wilayah/Rute/Toko/Produk/Kontrol | Menu Pengguna |
|------|-----------|-----------------------------------|---------------|
| **Admin** | ✅ | ✅ | ✅ |
| **Manajer** | ✅ | ✅ | ❌ |
| **Sales** | ✅ | ✅ | ❌ |

**Cara tambah user:**
1. Login sebagai Admin
2. Buka tab **👤 Pengguna** → Tambah pengguna baru
3. Isi nama, email (harus sama persis dengan email Google), dan pilih role
4. User tersebut bisa login dengan Google menggunakan email yang terdaftar

---

## 🚀 Cara Deploy ke Netlify

### Opsi A: Drag & Drop (paling mudah)
```bash
npm install
npm run build
```
Drag folder `dist/` ke https://app.netlify.com/drop

### Opsi B: Connect GitHub
1. Push project ke GitHub
2. Di Netlify: **New site from Git** → pilih repo
3. Build command: `npm run build`
4. Publish directory: `dist`
5. Klik **Deploy site**

### Tambah Domain Custom (opsional)
Di Firebase Console → Authentication → **Authorized domains** → tambahkan domain Netlify Anda.

---

## 💻 Development Lokal

```bash
npm install
npm run dev
# Buka http://localhost:5173
```
