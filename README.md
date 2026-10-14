# 🎾 RacquetLab ID — Komparasi Raket Tenis (2010–2026) & AI Spec Finder

**RacquetLab ID** adalah prototipe aplikasi web interaktif yang gw buat untuk membandingkan spesifikasi raket tenis lintas generasi dari berbagai merek terkenal yang dirilis antara tahun **2010 hingga 2026**. Aplikasi ini menggabungkan katalog spesifikasi, visualisasi radar biomekanika, dan pencarian yang terhubung ke **Google Gemini AI**.
(ini gw bikin iseng iseng aja hehe)

---

## ✨ Fitur Utama

### 1. Head-to-Head Spec Matrix (Komparasi Side-by-Side)

- Bandingkan hingga **4 raket sekaligus** secara berdampingan.
- **4 Parameter Utama**:
  1. **Merek & Tahun Rilis** (Yonex, Wilson, Babolat, Head, Prince, Dunlop, Tecnifibre dari 2010–2026).
  2. **Berat Tanpa Senar (_Unstrung Weight_)** dalam satuan gram ($\text{g}$).
  3. **Ukuran Kepala (_Headsize_)** dalam satuan inci persegi ($\text{sq. in.}$).
  4. **Tipe Karakter Raket** (_Power_, _Control_, _Spin_, _Arm-Friendly / Comfort_, _Tweener_).
- **Metrik Biomekanika Pro**: Kekakuan batang (_Stiffness_ / $\text{RA}$), _Swingweight_ ($\text{kg}\cdot\text{cm}^2$), titik keseimbangan (_Balance Point_), dan pola senar (_String Pattern_).
- **Indikator Unggulan Otomatis**: Badge otomatis untuk menandai raket _Paling Ringan_, _Paling Stabil/Berat_, _Sweetspot Terbesar_, dan _Paling Ramah Lengan_.

### 2. Kolom Pencarian Berbasis AI (_AI Spec Finder_)

- Mencari raket spesifik di luar katalog bawaan menggunakan bahasa alami (_Natural Language Query_), contoh:
  - _"Cari raket tahun 2015-2025 yang ramah untuk tennis elbow di bawah 295 gram"_
  - _"Head Radical MP 2012 vs Babolat Pure Drive 2015"_
- Menggunakan _Structured JSON Schema_ pada **Gemini API** untuk mengekstrak spesifikasi raket secara akurat dan mengizinkan pengguna langsung menyimpannya ke katalog atau memasukkannya ke meja komparasi.

### 3. Analisis & Rekomendasi Biomekanika AI (_AI Verdict_)

- Menganalisis perbandingan raket yang sedang dipilih di meja komparasi secara _real-time_.
- Memberikan ulasan mendalam mengenai:
  - **Power vs. Control & Spin**
  - **Kenyamanan Lengan (_Tennis Elbow Safety_)** berdasarkan kombinasi $\text{RA}$ dan distribusi berat.
  - **Rekomendasi Profil Pemain** yang paling cocok untuk masing-masing raket.

### 4. Visualisasi Radar & Telemetri Bar

- **5-Axis Spider/Radar Chart**: Memetakan karakter permainan (_Power_, _Spin_, _Control_, _Comfort_, _Maneuverability_) dalam skala $0\text{--}100$.
- **Horizontal Telemetry Bars**: Perbandingan visual proporsional untuk Berat, _Headsize_, _Stiffness_ ($\text{RA}$), dan _Swingweight_.

### 5. Katalog Interaktif & Input Raket Kustom

- Filter berlapis berdasarkan kata kunci, merek, kategori berat ($\le 290\text{ g}$, $291\text{--}305\text{ g}$, $> 305\text{ g}$), _headsize_ ($\le 97\text{ sq. in.}$, $98\text{--}100\text{ sq. in.}$, $> 100\text{ sq. in.}$), tipe raket, serta rentang tahun rilis ($2010\text{--}2026$).
- Fitur **Input Manual** bagi pengguna yang ingin memasukkan raket hasil _custom/modifikasi_ (_lead tape_, ganti grip, dll.).

---

## 🛠️ Tech Stack

- **Frontend Markup & Styling**: HTML5, Tailwind CSS (via CDN) dengan konfigurasi tema gelap (_Dark Court Telemetry_).
- **Scripting & State Management**: Vanilla JavaScript (ES6+), _Zero-Build Single-File Architecture_.
- **Visualisasi Grafik**: Custom Dynamic SVG Generator (untuk ilustrasi proporsi kepala raket & _Radar Chart_).
- **Ikon & Tipografi**: [Lucide Icons](https://lucide.dev/), Google Fonts (`Space Grotesk`, `Inter`, `JetBrains Mono`).
- **Integrasi AI & Eksternal**:
  - **Google Gemini API** (`gemini-3-flash-preview`) untuk _AI Spec Finder_ dan _Biomechanical Verdict_.
  - **Google Custom Search JSON API** (Opsional) untuk mengambil foto produk raket asli dari Google Images.

---

## 📂 Struktur Proyek

Proyek ini dirancang dengan arsitektur _Single-File_ agar mudah dijalankan dan dibagikan tanpa proses _bundling_ yang rumit:

```text
racquetlab-id/
├── index.html       # Aplikasi utama (HTML, Tailwind Config, SVG Engine, & JS Logic)
└── README.md        # Dokumentasi proyek & panduan konfigurasi API
```

---

## 🚀 Cara Menjalankan Proyek

1. **Unduh atau Clone File**
   Simpan file `index.html` ke dalam direktori lokal Anda.
2. **Jalankan di Browser**
   - Klik dua kali file `index.html` untuk membukanya langsung di browser modern (Chrome, Edge, Firefox, Safari), **atau**
   - Gunakan ekstensi **Live Server** di VS Code / jalankan server lokal Python:
     ```bash
     python -m http.server 8080
     ```
   - Buka `http://localhost:8080` di browser Anda.

## 📊 Panduan Singkat Metrik Spesifikasi Raket

| Metrik                   | Satuan                      | Penjelasan & Dampak di Lapangan                                                                                                                                                                    |
| :----------------------- | :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Berat (_Unstrung_)**   | $\text{gram (g)}$           | Berat raket sebelum dipasang senar. $\le 290\text{ g}$ mudah diayun pemula/intermediate; $> 305\text{ g}$ sangat stabil menahan bola keras lawan.                                                  |
| **Headsize**             | $\text{sq. in.}$            | Luas penampang kepala raket. $\le 97\text{ sq. in.}$ fokus pada kontrol & presisi; $100\text{ sq. in.}$ seimbang (_tweener_); $> 102\text{ sq. in.}$ memberikan _sweetspot_ besar & tenaga ekstra. |
| **Stiffness (Kekakuan)** | $\text{RA}$                 | Indeks kelenturan batang raket. $< 62\text{ RA}$ terasa lembut dan aman untuk lengan (_tennis elbow_); $> 67\text{ RA}$ kaku dan memberikan pantulan bola (_power_) eksplosif.                     |
| **Swingweight**          | $\text{kg}\cdot\text{cm}^2$ | Bobot ayun dinamis saat raket diayunkan. Semakin tinggi nilainya ($> 325\text{ kg}\cdot\text{cm}^2$), semakin besar daya dobrak (_plow-through_) namun membutuhkan teknik ayunan yang kuat.        |

---

## 📝 Lisensi

Proyek prototipe ini dibuat untuk tujuan edukasi, riset perlengkapan olahraga tenis, dan pengembangan antarmuka web interaktif. Seluruh nama merek dan seri raket (Yonex, Wilson, Babolat, Head, Prince, Dunlop, Tecnifibre) adalah hak cipta dari masing-masing produsen terkait.
