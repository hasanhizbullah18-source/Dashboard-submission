
# Proyek Analisis Data: Products Dataset

- **Nama:** Urwah Hasan Hizbullah
- **Email:** hasanhizbullah18@gmail.com
- **ID Dicoding:** Hasan Hizbullah

## Pendahuluan
Proyek ini menganalisis dataset produk untuk memahami karakteristik produk dan kategori yang berbeda. Analisis ini mencakup identifikasi kategori produk dengan jumlah item terbanyak, serta hubungan antara berat dan dimensi fisik produk.

## Pertanyaan Bisnis

1.  Kategori produk apa yang memiliki jumlah produk terbanyak?
2.  Bagaimana hubungan antara berat produk dan fisiknya, dan kategori mana yang paling memiliki karakteristik paling unik dan ekstrim?

## Setup Lingkungan
Proyek ini menggunakan library Python berikut:
- `numpy`
- `pandas`
- `matplotlib.pyplot`
- `seaborn`

## Data Wrangling

### Gathering Data
Data dikumpulkan dari dua file CSV:
- `products_dataset.csv`: Berisi informasi detail tentang produk.
- `product_category_name_translation.csv`: Berisi terjemahan nama kategori produk dari Portugis ke Inggris.

### Assessing Data
- Dataset `products_df` memiliki 32951 entri dan 9 kolom. Beberapa kolom numerik dan kategori (`product_category_name`, `product_name_lenght`, `product_description_lenght`, `product_photos_qty`, `product_weight_g`, `product_length_cm`, `product_height_cm`, `product_width_cm`) memiliki nilai yang hilang.
- Tidak ada duplikasi data yang ditemukan dalam `products_df`.
- `product_category_name_english` juga memiliki nilai hilang setelah merge.

### Cleaning Data
- `products_df` digabungkan dengan `translation_df` berdasarkan `product_category_name` untuk menambahkan kolom `product_category_name_english`.
- Nilai yang hilang pada kolom numerik (`product_weight_g`, `product_length_cm`, `product_height_cm`, `product_width_cm`, `product_name_lenght`, `product_description_lenght`, `product_photos_qty`) diisi dengan median dari masing-masing kolom.
- Nilai yang hilang pada `product_category_name_english` diisi dengan 'Unknown'.
- Nilai yang hilang pada `product_category_name` diisi dengan modus dari kolom tersebut.
- Setelah pembersihan, tidak ada lagi nilai yang hilang di DataFrame `product_df`.

## Exploratory Data Analysis (EDA)

### Pertanyaan 1: Kategori produk apa yang memiliki jumlah produk terbanyak?
- Ditemukan 10 kategori produk teratas berdasarkan jumlah produk. `bed_bath_table` memiliki jumlah produk terbanyak, diikuti oleh `sports_leisure` dan `furniture_decor`.

### Pertanyaan 2: Bagaimana hubungan antara berat produk dan fisiknya, dan kategori mana yang paling memiliki karakteristik paling unik dan ekstrim?
- Analisis korelasi menunjukkan korelasi positif yang kuat antara berat produk (`product_weight_g`) dengan semua dimensi fisik (`product_length_cm`, `product_height_cm`, `product_width_cm`). Ini berarti semakin besar dimensi fisik suatu produk, semakin berat produk tersebut.
- Beberapa kategori menunjukkan karakteristik fisik yang ekstrem, misalnya kategori seperti furniture, construction tools, dan bath, bed, table cenderung memiliki berat dan ukuran yang lebih besar, sedangkan stationery, toys, dan fashion accessories memiliki bobot dan ukuran yang jauh lebih kecil.

## Visualisasi & Analisis Eksplanatori

### Visualisasi untuk Pertanyaan 1
- Sebuah bar plot digunakan untuk menampilkan 10 kategori produk teratas berdasarkan jumlah produk. `bed_bath_table` adalah kategori yang dominan.

### Visualisasi untuk Pertanyaan 2
- Sebuah heatmap korelasi antara atribut produk dan atribut fisik ditampilkan untuk menunjukkan hubungan antar variabel. Korelasi positif yang kuat antara berat dan dimensi fisik terlihat jelas.

## Kesimpulan

1.  **Kategori Produk Terbanyak:** Kategori produk dengan jumlah produk terbanyak (fokus inventaris utama) adalah `bed_bath_table`. Ini menunjukkan variasi produk yang besar di area kebutuhan rumah tangga dan kamar mandi.
2.  **Hubungan Berat dan Dimensi Fisik:** Terdapat korelasi positif yang kuat antara berat produk dan dimensi fisiknya (panjang, lebar, tinggi). Semakin besar dimensi fisik produk, semakin berat produk tersebut. Analisis ini membantu memahami bagaimana karakteristik fisik produk bervariasi antar kategori dan dapat dimanfaatkan dalam pengelolaan inventaris serta strategi penataan produk.

## File Output
- `cleaned_products_data.csv`: DataFrame yang telah dibersihkan dan digabungkan (`product_df`) disimpan ke dalam file CSV ini.
