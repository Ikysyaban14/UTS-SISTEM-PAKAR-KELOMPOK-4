# 💻 Sistem Pakar Identifikasi Kerusakan Laptop

Program ini merupakan implementasi **Sistem Pakar** untuk mendeteksi kerusakan laptop menggunakan metode **Backward Chaining** berbasis Python.

Sistem akan melakukan analisa berdasarkan gejala yang dialami pengguna, kemudian memberikan kemungkinan jenis kerusakan yang terjadi.

---

## 📑 Daftar Isi

- [🚀 Jalankan Online](#-jalankan-online)
- [📖 Deskripsi Sistem](#-deskripsi-sistem)
- [🧠 Metode Backward Chaining](#-metode-backward-chaining)
- [📚 Knowledge Base](#-knowledge-base)
- [⚙️ Cara Penggunaan](#️-cara-penggunaan)
- [💻 Teknologi](#-teknologi)

---

## 🚀 Jalankan Online

Program dapat dijalankan melalui Google Colab:
https://colab.research.google.com/drive/1MzzKppZe9tkZwn6858m6l_SRB82JO7dU?usp=sharing
---

## 📖 Deskripsi Sistem
Kerusakan laptop sering kali sulit dikenali oleh pengguna biasa karena banyak gejala antar komponen memiliki kemiripan.
Melalui sistem ini, pengguna dapat mengetahui kemungkinan kerusakan hanya dengan menjawab beberapa pertanyaan gejala.
Program ini cocok digunakan sebagai:
Media pembelajaran Artificial Intelligence
Implementasi Sistem Pakar
Simulasi diagnosa perangkat komputer
Alat bantu identifikasi awal kerusakan laptop

## 🧠 Metode Backward Chaining
Backward Chaining adalah metode penalaran yang dimulai dari tujuan atau kesimpulan, lalu sistem mencari fakta/gejala yang mendukung kesimpulan tersebut.

### Cara Kerja:
- Sistem memilih target kerusakan
- Sistem menanyakan gejala terkait
- Jika semua gejala terpenuhi, target dianggap benar
- Jika tidak sesuai, sistem berpindah ke target lain
- Hasil akhir ditampilkan ke pengguna

---

## 📚 Knowledge Base

### 🖥️ Data Kerusakan
| Kode | Jenis Kerusakan |
|------|----------------|
| K01  | Kerusakan LCD / LED |
| K02  | Kerusakan IC Power |
| K03  | Kerusakan VGA |
| K04  | Kerusakan RAM |
| K05  | Kerusakan Harddisk |
| K06  | Kerusakan Motherboard |
| K07  | Kerusakan Keyboard |
| K08  | Kerusakan DVD Drive |
| K09  | Kerusakan Port USB |
| K10  | Kerusakan Touchpad |
| K11  | Kerusakan Wifi |
| K12  | Kerusakan Sistem Operasi |

---

## 🔍 Data Gejala
| Kode | Gejala |
|------|--------|
| G01  | Laptop mati total |
| G02  | Layar gelap |
| G03  | Layar bergaris |
| G04  | Laptop restart sendiri |
| G05  | Bunyi beep saat booting |
| G06  | Laptop lambat |
| G07  | Harddisk loading lama |
| G08  | Keyboard tidak berfungsi |
| G09  | Touchpad tidak bergerak |
| G10  | Wifi tidak terdeteksi |
| G11  | USB tidak terbaca |
| G12  | Laptop cepat panas |

---

## 🧾 Aturan IF - THEN
- IF G02 AND G03 THEN K01
- IF G01 THEN K02
- IF G04 AND G12 THEN K03
- IF G05 THEN K04
- IF G06 AND G07 THEN K05
- IF G01 AND G12 THEN K06
- IF G08 THEN K07
- IF DVD tidak terbaca THEN K08
- IF G11 THEN K09
- IF G09 THEN K10
- IF G10 THEN K11
- IF G06 THEN K12

---

## ⚙️ Cara Penggunaan
1. Jalankan program Python  
2. Sistem akan memberikan pertanyaan gejala  
3. Jawab dengan:
   - y = Ya  
   - n = Tidak  

---

## 💻 Teknologi
- Python
- Terminal / CMD
- Artificial Intelligence
- Expert System
- Backward Chaining
