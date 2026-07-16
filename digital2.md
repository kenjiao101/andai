# Kemiskinan dan Akses Internet di Indonesia: Studi Kasus Statistik (2024)

### Analisis kemiskinan dan akses internet di seluruh provinsi di Indonesia menggunakan korelasi, regresi, dan uji chi-square untuk mengukur kesenjangan digital di Indonesia.

## 📝 Daftar Isi

1. [Gambaran Umum](#-gambaran-umum)
2. [Rumusan Masalah](#-rumusan-masalah)
3. [Dataset](#-dataset)
4. [Tech Stack](#-tech-stack)
5. [Screenshot](#-screenshot)
6. [Hasil dan Performa](#-hasil-dan-performa)
7. [Panduan Menjalankan Proyek](#-panduan-menjalankan-proyek)
8. [Keterbatasan](#-keterbatasan)

---

## 📌 Gambaran Umum

Proyek ini merupakan analisis statistik yang mengkaji hubungan antara tingkat kemiskinan dan akses internet rumah tangga di seluruh provinsi di Indonesia. Analisis dilakukan menggunakan dua pendekatan yang saling independen: pendekatan kontinu melalui korelasi Pearson dan regresi linear, serta pendekatan kategorikal melalui uji chi-square dan Fisher's exact test, menggunakan data BPS tahun 2024 yang mencakup `37` provinsi. Alur analisis dimulai dari pembersihan dan penggabungan data, dilanjutkan dengan analisis univariat dan bivariat, pemodelan regresi beserta pengujian seluruh asumsi statistiknya, kemudian pengujian hubungan kategorikal menggunakan ukuran efek serta analisis post-hoc. Hasil akhirnya menunjukkan temuan yang tervalidasi melalui dua pendekatan berbeda, yaitu bahwa tingkat kemiskinan dan akses internet memiliki hubungan yang kuat, baik berdasarkan metode kontinu maupun kategorikal.

## ❓ Rumusan Masalah

**Konteks:** Tingkat akses internet di Indonesia menunjukkan variasi yang sangat besar antarprovinsi, mulai dari lebih dari `97%` di Kepulauan Riau hingga hanya sekitar `12%` di Papua Pegunungan. Tingkat kemiskinan juga memperlihatkan variasi yang serupa, berkisar antara `4.00%` hingga `32.97%`. Kedua pola tersebut telah banyak didokumentasikan dalam publikasi rutin BPS.

**Kesenjangan:** Meskipun demikian, laporan deskriptif tersebut belum mampu menjawab apakah kedua pola tersebut memiliki hubungan yang signifikan secara statistik, seberapa kuat hubungan tersebut, seberapa andal hasilnya, serta apakah kesimpulan yang diperoleh tetap konsisten ketika diuji menggunakan lebih dari satu metode statistik.

**Solusi:** Proyek ini menguji hubungan antara tingkat kemiskinan dan akses internet menggunakan dua pendekatan independen, yaitu pendekatan kontinu (korelasi Pearson dan regresi linear dengan pengujian seluruh asumsi statistik) serta pendekatan kategorikal (uji chi-square independensi dan Fisher's exact test yang dilengkapi ukuran efek serta analisis post-hoc), kemudian membandingkan apakah kedua pendekatan menghasilkan kesimpulan yang konsisten.

## 📊 Dataset

### Metadata

| Atribut | Detail |
|---|---|
| **Sumber** | BPS (Badan Pusat Statistik), 2 tabel |
| **Tautan** | [Tabel Akses Internet](https://www.bps.go.id/id/statistics-table/2/Mzk4IzI=/persentase-rumah-tangga-yang-pernah-mengakses-internet-dalam-3-bulan-terakhir-menurut-provinsi-dan-klasifikasi-daerah.html), [Tabel Tingkat Kemiskinan](https://www.bps.go.id/id/statistics-table/2/MTkyIzI=/persentase-penduduk-miskin--p0--menurut-provinsi-dan-daerah.html) |
| **Format** | CSV |
| **Ukuran** | `37` baris (provinsi) × `5` kolom setelah proses pembersihan dan penggabungan data |
| **Lisensi** | Belum diverifikasi, silakan periksa ketentuan penggunaan data BPS sebelum mendistribusikan ulang file CSV mentah |
| **Cakupan Waktu** | `2024` (angka kemiskinan menggunakan data Maret 2024 / Semester I agar konsisten secara temporal) |
| **Tanggal Akses** | `[Isi dengan tanggal akses data yang sebenarnya]` |

### Kamus Data (Kolom Utama)

| Kolom | Tipe Data | Deskripsi | Contoh Nilai |
|---|:---:|---|---|
| `Provinsi` | `str` | Nama provinsi yang telah distandardisasi menjadi huruf kapital | `"PAPUA PEGUNUNGAN"` |
| `Kemiskinan_Persen` | `float` | Persentase penduduk miskin (P0), Maret 2024 | `32.97` |
| `Internet_Total` | `float` | **Variabel target** — persentase rumah tangga yang mengakses internet dalam tiga bulan terakhir | `12.15` |
| `Kategori_Kemiskinan` | `str` | **Variabel turunan** — tingkat kemiskinan yang dikelompokkan menjadi Rendah / Sedang / Tinggi berdasarkan kuartil | `"Tinggi"` |
| `Kategori_Internet` | `str` | **Variabel turunan** — tingkat akses internet yang dikelompokkan menjadi Rendah / Sedang / Tinggi berdasarkan kuartil | `"Rendah"` |

## 🛠️ Tech Stack

| Layer | Teknologi | Peran dalam Proyek |
|:---:|:---:|---|
| Bahasa Pemrograman | Python 3 | Bahasa utama untuk pembersihan data, analisis statistik, dan visualisasi |
| Environment | Google Colab | Lingkungan interaktif untuk menjalankan notebook, eksplorasi, dan pelaporan bertahap |
| Pemrosesan Data | Pandas, NumPy | Pembersihan data, standardisasi nama provinsi, penggabungan dataset, dan kategorisasi berdasarkan kuartil |
| Visualisasi | Matplotlib, Seaborn | Plot distribusi, scatter plot dengan garis tren, heatmap tabel kontingensi, dan plot diagnostik regresi |
| Pemodelan Statistik | Scikit-learn | Pemodelan regresi linear (`LinearRegression`) dan perhitungan `R²` |
| Pengujian Statistik | SciPy (`scipy.stats`) | Korelasi Pearson, uji F, uji t, Shapiro-Wilk, Breusch-Pagan, chi-square, dan Fisher's exact test |
| Version Control | Git + GitHub | Pengelolaan versi proyek dan dokumentasi perubahan |

## 🎥 Screenshot

### Tingkat Kemiskinan vs. Akses Internet (Hubungan Bivariat)

<p align="center">
  <img width="700" height="430" alt="image"
       src="[URL gambar - scatter plot bivariat dari notebook bagian 3.3 Analisis Bivariat]" />
</p>

Provinsi dengan tingkat kemiskinan yang lebih tinggi secara konsisten terkonsentrasi pada tingkat akses internet yang lebih rendah, dengan korelasi Pearson sebesar `r = -0.8215` pada `37` provinsi yang dianalisis.

### Hasil Regresi Linear

<p align="center">
  <img width="700" height="430" alt="image"
       src="[URL gambar - regression plot dari notebook bagian 5.6 Visualisasi Regresi]" />
</p>

Model regresi yang diperoleh, yaitu `Akses Internet = 108.16 - 1.96 × Tingkat Kemiskinan`, mampu menjelaskan `R² = 0.6748` dari variasi data dan signifikan secara statistik pada `p < 0.001`.

### Tabulasi Silang Tingkat Kemiskinan dan Akses Internet

<p align="center">
  <img width="600" height="450" alt="image"
       src="[URL gambar - heatmap crosstabulation dari notebook bagian 4.5 atau 6.4 Visualisasi Chi-Square]" />
</p>

Dari `10` provinsi dengan tingkat kemiskinan tinggi, sebanyak `7` berada pada kategori akses internet rendah, jauh di atas nilai harapan sebesar `2.43`. Sel tersebut menjadi kontributor terbesar terhadap statistik chi-square dengan kontribusi sebesar `42.50%`.

### Fisher's Exact Test: Provinsi dengan Kemiskinan Tinggi vs. Akses Internet Tinggi

<p align="center">
  <img width="800" height="400" alt="image"
       src="[URL gambar - visualisasi tabel 2x2 dari notebook bagian 6.3.1 Fisher's Exact Test]" />
</p>

Tidak ada satu pun provinsi dengan tingkat kemiskinan tinggi yang termasuk ke dalam kategori akses internet tinggi (`Odds Ratio = 0`). Pola tersebut dikonfirmasi signifikan secara statistik melalui Fisher's exact test dengan `p = 0.036`.

## 📈 Hasil dan Performa

### Ringkasan Perbandingan Metode

| Metode | Statistik | Nilai | p-value | Kesimpulan |
|:---:|:---:|:---:|:---:|---|
| Korelasi Pearson | `r` | `-0.8215` | `< 0.001` | Korelasi negatif sangat kuat |
| Regresi Linear | `R²` | `0.6748` | `< 0.001` (Uji F) | Tingkat kemiskinan menjelaskan `67.48%` variasi akses internet |
| Uji Chi-Square | `chi-square` | `20.18` | `< 0.001` | Terdapat hubungan yang signifikan antar kategori |
| Fisher's Exact Test | `Odds Ratio` | `0` | `0.036` | Mengonfirmasi tidak adanya provinsi dengan kemiskinan tinggi dan akses internet tinggi secara bersamaan |

### Temuan Utama

1. **Tingkat kemiskinan dan akses internet memiliki hubungan negatif yang sangat kuat.** Korelasi Pearson pada `37` provinsi menghasilkan `r = -0.8215` (`R² = 0.6748`, `p < 0.001`), yang menunjukkan bahwa tingkat kemiskinan saja mampu menjelaskan sekitar dua pertiga variasi akses internet antarprovinsi.

2. **Setiap kenaikan 1 poin persentase tingkat kemiskinan berkaitan dengan penurunan sekitar 2 poin persentase akses internet.** Model regresi yang diperoleh adalah `Akses Internet = 108.16 - 1.96 × Tingkat Kemiskinan`, signifikan baik secara keseluruhan (`F = 72.62`, `p < 0.001`) maupun pada koefisien regresinya (`t = -8.52`, `p < 0.001`, 95% CI `[-2.43, -1.49]`), dan berlaku pada rentang tingkat kemiskinan yang diamati, yaitu `4.00%` hingga `32.97%`.

3. **Asumsi homoskedastisitas dan independensi pada model regresi tidak terpenuhi sehingga nilai p sebaiknya diinterpretasikan sebagai pendekatan.** Residu memenuhi asumsi normalitas (`Shapiro-Wilk p = 0.09`), namun tidak memenuhi uji homoskedastisitas Breusch-Pagan (`p < 0.001`) serta memiliki statistik Durbin-Watson sebesar `1.04`, di bawah kisaran yang umum diterima (`1.5–2.5`).

4. **Pendekatan kategorikal secara independen mengonfirmasi adanya hubungan dengan ukuran efek yang sangat kuat.** Setelah kedua variabel dikelompokkan menjadi kategori Rendah / Sedang / Tinggi berdasarkan kuartil, uji chi-square menunjukkan hubungan yang signifikan (`chi-square = 20.18`, `df = 4`, `p < 0.001`), dengan nilai Cramer's V sebesar `0.5222`, yang termasuk kategori sangat kuat untuk tabel `3×3`.

5. **Karena sebagian besar sel pada tabel kontingensi memiliki frekuensi harapan yang rendah, Fisher's exact test digunakan sebagai validasi yang lebih andal.** Sebanyak `77.8%` sel memiliki expected frequency di bawah `5`, sehingga digunakan tabel `2×2` yang disederhanakan (Kemiskinan Tinggi vs. Rendah–Sedang dan Akses Internet Tinggi vs. Rendah–Sedang). Fisher's exact test tetap menunjukkan hasil yang signifikan (`p = 0.036`).

6. **Tidak ada satu pun provinsi dengan tingkat kemiskinan tinggi yang memiliki akses internet tinggi.** Pada tabel `2×2`, diperoleh odds ratio sebesar `0`, yang berarti tidak terdapat provinsi dengan kombinasi kedua karakteristik tersebut, memperkuat pola yang telah ditunjukkan oleh analisis regresi.

7. **Kombinasi kemiskinan tinggi dan akses internet rendah merupakan penyumbang terbesar terhadap nilai chi-square.** Sel tersebut menyumbang `42.50%` dari total statistik chi-square, dengan `7` observasi dibandingkan nilai harapan `2.43` serta standardized residual sebesar `2.93`.

8. **Pendekatan kontinu dan kategorikal menghasilkan kesimpulan yang konsisten secara independen.** Nilai Cramer's V (`0.52`) maupun Pearson's r (`-0.82`) sama-sama termasuk kategori "sangat kuat" berdasarkan interpretasi konvensional masing-masing, sehingga memperkuat keandalan temuan penelitian ini.

## 🚀 Panduan Menjalankan Proyek

> Proyek ini merupakan bagian dari sebuah repository koleksi yang lebih besar. Clone repository utama terlebih dahulu (lihat README pada direktori root), kemudian masuk ke folder proyek ini.

1. Masuk ke folder proyek:

```bash
cd poverty-internet-access-2024
```

2. Buat virtual environment (Opsional):

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
```

3. Instal seluruh dependensi:

```bash
pip install -r requirements.txt
```

4. **Catatan dataset:** Dua file CSV dari BPS belum disertakan dalam folder proyek ini. Unduh keduanya melalui tautan pada bagian [Dataset](#-dataset), kemudian letakkan di dalam subfolder lokal `data/`. Notebook ini awalnya dikembangkan di Google Colab menggunakan `google.colab.files.upload()`. Jika dijalankan secara lokal, ganti pemanggilan tersebut dengan:

```python
pd.read_csv('data/<nama_file>.csv', skiprows=...)
```

5. Jalankan notebook:

```bash
jupyter notebook notebooks/eda_poverty_internet_access_2024.ipynb
```

Setelah langkah ke-4 selesai, seluruh sel dapat dijalankan secara berurutan dari atas ke bawah tanpa memerlukan input interaktif selain proses upload file yang sebelumnya digunakan di Google Colab.

---

## ⚠️ Keterbatasan

- **Interpretasi koefisien regresi:** Kemiringan garis regresi (`-1.9603`) hanya berlaku pada rentang tingkat kemiskinan yang diamati, yaitu `4.00%` hingga `32.97%`. Sementara itu, nilai intersep (`108.16%`) berada di luar batas realistis `0%–100%` sehingga tidak memiliki interpretasi praktis secara mandiri, karena merupakan hasil ekstrapolasi pada kondisi tingkat kemiskinan `0%`, yang berada di luar cakupan data observasi.

- **Ruang lingkup:** Analisis ini mencakup `37` dari `38` provinsi di Indonesia untuk satu periode pengamatan (`2024`) dan hanya menunjukkan adanya **hubungan statistik**, bukan hubungan sebab-akibat (*causation*). Faktor-faktor lain seperti investasi infrastruktur, kondisi geografis, dan tingkat pendidikan berada di luar ruang lingkup penelitian ini.

- **Data:** Satu provinsi (DKI Jakarta) dikeluarkan pada proses penggabungan data karena tidak memiliki nilai akses internet wilayah perdesaan. Selain itu, DKI Jakarta merupakan outlier yang sepenuhnya bersifat perkotaan dibandingkan provinsi lainnya, sehingga penghapusannya tidak dapat dianggap benar-benar acak terhadap variabel yang diteliti. Indikator akses internet yang digunakan juga hanya mengukur akses yang dilaporkan oleh rumah tangga dalam **tiga bulan terakhir**, bukan kualitas maupun kecepatan koneksi internet.

- **Keterbatasan teknis:** Model regresi tidak memenuhi asumsi homoskedastisitas maupun tidak adanya autokorelasi (`Breusch-Pagan p < 0.001`, `Durbin-Watson = 1.04`), sehingga interval kepercayaan dan nilai signifikansinya sebaiknya dipandang sebagai pendekatan, bukan estimasi yang benar-benar presisi. Selain itu, notebook masih bergantung pada proses upload interaktif menggunakan `files.upload()` di Google Colab sehingga tidak dapat dijalankan sepenuhnya di lingkungan lokal tanpa melakukan modifikasi sebagaimana dijelaskan pada bagian [Panduan Menjalankan Proyek](#-panduan-menjalankan-proyek).
