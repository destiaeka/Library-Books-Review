# Book Review Web Project 📚

## 🧩 Deskripsi Singkat

Proyek ini merupakan aplikasi web sederhana yang dibangun untuk menampilkan rekomendasi buku beserta ulasan dan komentar dari pengguna.  
Seluruh infrastruktur dan manajemen cloud-nya dikelola melalui **Lovable Cloud AI**, sehingga proses pengembangan frontend dan backend dapat dilakukan dengan lebih efisien dan otomatis.

---

## ⚙️ Teknologi yang Digunakan

Proyek ini menggunakan teknologi modern untuk mendukung performa dan tampilan yang responsif, di antaranya:

- ⚡ **Vite** — Build tool modern untuk pengembangan cepat.  
- ⚛️ **React (TypeScript)** — Library JavaScript untuk membangun tampilan antarmuka yang dinamis.  
- 🎨 **Tailwind CSS** — Framework CSS untuk desain yang konsisten dan efisien.  
- 🧱 **shadcn/ui** — Komponen UI siap pakai berbasis Tailwind.  

---

## 💻 Menjalankan Proyek Secara Lokal

Meskipun proyek ini dikelola oleh **Lovable Cloud**, pengembangan juga bisa dilakukan secara lokal menggunakan Node.js.

Pastikan Node.js dan npm sudah terpasang di sistem Anda.  
Jika belum, disarankan menginstalnya menggunakan [nvm (Node Version Manager)](https://github.com/nvm-sh/nvm#installing-and-updating).

Langkah-langkah menjalankan proyek:
1. Clone repository
```git clone https://github.com/destiaeka/Library-Books-Review.git```

2. Masuk ke direktori proyek
```cd Library-Books-Review```

3. Instal seluruh dependensi
```npm install```

4. Jalankan server pengembangan
```npm run dev```

## 🐳 Menjalankan Menggunakan Docker
Proyek ini juga telah dikemas dalam Docker image sehingga dapat dijalankan secara langsung tanpa perlu instalasi manual.
1. pull image
```docker pull destiaeka/booksreview```

2. Run the Container
``` docker run -d --name booksreview -p 80:80 destiaeka/booksreview```

3. Aplikasi dapat diakses pada alamat ```http://localhost``` 

## ⚙️ CI/CD Workflow
Proyek ini dilengkapi dengan workflow otomatis yang menangani proses berikut:
- Build image Docker dari source code.
- Push image ke Docker Hub.
- Deploy otomatis ke cluster Kubernetes (K3s).
Semua proses tersebut dijalankan melalui GitHub Actions, sehingga setiap perubahan kode akan otomatis melalui pipeline CI/CD untuk memastikan integritas dan ketersediaan aplikasi

🧑‍💻 Pengembang

Destia Eka
📦 Repository: Library-Books-Review
🐋 Docker Hub: destiaeka/booksreview