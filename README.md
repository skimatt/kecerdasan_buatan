
# Panduan Push dan Update Project ke GitHub

## Persiapan Awal

1. Pastikan kamu sudah memiliki akun GitHub.
2. Buat repository baru di GitHub, misal: `kecerdasan_buatan`.
3. Pastikan Git sudah terinstall di komputer kamu.
4. Siapkan project lokal di folder kerja kamu.

---

## 1. Inisialisasi Git dan Hubungkan ke Repository GitHub

Buka terminal di folder project kamu:

```bash
cd path/to/project
git init
git remote add origin https://github.com/username/repository.git
````

Ganti `username` dan `repository` sesuai dengan milik kamu.

---

## 2. Buat `.gitignore`

Agar folder seperti `node_modules` dan file konfigurasi sensitif tidak ikut terupload, buat file `.gitignore` di root project dengan isi seperti ini:

```
node_modules/
dist/
.env
```

---

## 3. Push Project Pertama Kali

Tambahkan semua file ke staging area dan buat commit:

```bash
git add .
git commit -m "Initial commit"
```

Push ke GitHub dengan perintah:

```bash
git branch -M main
git push -u origin main
```

---

## 4. Mengatasi Error Push Ditolak Karena Perubahan di Remote

Jika kamu mendapat pesan error saat push seperti ini:

```
error: failed to push some refs to 'https://github.com/username/repository.git'
hint: Updates were rejected because the remote contains work that you do not have locally.
```

Maka lakukan pull dan rebase terlebih dahulu:

```bash
git pull origin main --rebase
```

Jika ada konflik, selesaikan secara manual kemudian lanjutkan:

```bash
git add .
git rebase --continue
```

Setelah itu, push ulang:

```bash
git push -u origin main
```

---

## 5. Update Project Setelah Ada Perubahan

Setiap kali kamu melakukan perubahan pada project, lakukan perintah berikut:

```bash
git add .
git commit -m "Deskripsi singkat perubahan"
git push
```

---

## 6. Memaksa Push (Gunakan dengan Hati-hati)

Jika kamu yakin ingin menimpa seluruh isi repository remote dengan project lokal kamu:

```bash
git push --force
```

> ⚠️ **Peringatan:** Perintah ini akan menghapus seluruh histori di remote dan menggantinya dengan isi lokal kamu.

---

## 7. Tips Tambahan

* Gunakan pesan commit yang jelas dan singkat agar mudah dipahami.
* Jangan upload folder `node_modules/` karena ukurannya besar dan bisa dihasilkan ulang.
* Pertimbangkan menggunakan branch terpisah untuk fitur baru, lalu merge ke `main`.
* Kamu juga bisa menggunakan SSH key untuk autentikasi GitHub agar lebih aman dan praktis.

---

## Referensi Perintah Git Dasar

| Perintah                      | Fungsi                                            |
| ----------------------------- | ------------------------------------------------- |
| `git init`                    | Membuat repository Git lokal baru                 |
| `git remote add origin <url>` | Menghubungkan repository lokal ke GitHub          |
| `git add .`                   | Menambahkan perubahan ke staging area             |
| `git commit -m "pesan"`       | Membuat commit dengan pesan                       |
| `git push`                    | Mengirim perubahan ke repository GitHub           |
| `git pull --rebase`           | Mengambil dan menyinkronkan perubahan dari GitHub |
| `git branch -M main`          | Mengganti nama branch menjadi `main`              |
| `git push --force`            | Memaksa push dan menimpa isi repository remote    |

---

Panduan ini bisa kamu gunakan untuk mengelola project kamu dengan Git dan GitHub secara efektif.



