# Laporan Proyek Machine Learning - Jericho Luthfi Syahli

## Domain Proyek
Cryptocurrency merupakan bentuk uang digital yang memanfaatkan teknologi kriptografi untuk memastikan keamanan transaksi dan mengatur penciptaan unit baru. Cryptocurrency berbeda dari mata uang konvensional karena tidak terkait dengan negara atau lembaga keuangan tertentu. Sebaliknya, cryptocurrency dikelola melalui jaringan terdesentralisasi dan transaksi dicatat dalam blockchain.

### Cara Kerja Cryptocurrency
Setiap transaksi cryptocurrency dicatat dalam blockchain, sebuah buku besar publik yang terdistribusi di seluruh jaringan. Setelah transaksi diverifikasi oleh node di jaringan, transaksi ditambahkan ke blockchain dan tidak dapat diubah. Sebagai imbalan, node yang memverifikasi transaksi menerima imbalan dalam bentuk cryptocurrency.

### Bagaimana Harga Cryptocurrency Ditentukan?
Harga cryptocurrency ditentukan oleh kekuatan pasar dan permintaan. Semakin banyak orang yang ingin membeli cryptocurrency tertentu, semakin tinggi harga cryptocurrency tersebut. Faktor-faktor seperti adopsi teknologi, regulasi pemerintah, dan masalah keamanan juga mempengaruhi harga cryptocurrency. Karena sifat cryptocurrency yang relatif baru dan sangat fluktuatif, harga dapat berubah dengan cepat dan sulit diprediksi.

---
Proyek ini berfokus pada pengembangan model Machine Learning untuk memprediksi harga Bitcoin (BTC). Bitcoin adalah cryptocurrency pertama dan paling terkenal yang sering digunakan sebagai acuan untuk cryptocurrency lainnya. Dengan meningkatnya minat dan investasi dalam Bitcoin, model prediksi harga dapat membantu investor dan pedagang dalam membuat keputusan investasi yang lebih baik.

Tujuan proyek ini adalah untuk mengembangkan model Machine Learning yang dapat memprediksi harga Bitcoin di masa depan dengan lebih akurat. Harga Bitcoin yang sangat fluktuatif membuat prediksi menjadi tantangan, dan model ini bertujuan untuk membantu investor membuat keputusan investasi yang lebih terinformasi.

## Business Understanding
### Problem Statements
Masalah utama yang dihadapi adalah fluktuasi harga Bitcoin yang tinggi dan sulit diprediksi. Hal ini menyulitkan investor dalam membuat keputusan investasi yang tepat. Misalnya, jika harga BTC meningkat, investor mungkin ingin membeli untuk potensi keuntungan, sementara jika harga turun, mereka mungkin ingin menjual untuk menghindari kerugian. Model Machine Learning dapat membantu dalam memprediksi harga BTC dan memberikan informasi yang lebih baik untuk keputusan investasi.

### Goals
Tujuan dari proyek ini adalah mengembangkan model Machine Learning yang dapat memprediksi harga Bitcoin dengan tingkat akurasi yang lebih tinggi. Selain itu, proyek ini bertujuan untuk meningkatkan pemahaman tentang Bitcoin dan penggunaan Machine Learning dalam memprediksi harga cryptocurrency.

## Data Understanding
### Data Source
Data yang digunakan diambil dari sumber berikut: [Bitcoin Historical Data](https://finance.yahoo.com/quote/BTC-USD/history/?period1=1410912000&period2=1722915722).

### Data Description
Dataset ini berisi data harga Bitcoin dari tanggal 2014-09-17 sampai tanggal 2024-08-06. Dataset ini terdiri dari beberapa variable tetapi hanya dua variabel utama saja yang terpakai yaitu:
* **Date**: Tanggal transaksi.
* **Close**: Harga penutupan Bitcoin pada tanggal tertentu.
* **Open**: Harga pembukaan Bitcoin pada tanggal tertentu.
* **High**: Harga tertinggi Bitcoin pada tanggal tertentu.
* **Low**: Harga terendah Bitcoin pada tanggal tertentu.
* **Adj Close**: Harga penutupan yang disesuaikan dengan faktor-faktor seperti pembagian saham.
* **Volume**: Jumlah Bitcoin yang diperdagangkan pada tanggal tertentu.

Data berukuran (3560, 50, 1) (3560, 1). Data ini memberikan gambaran tentang harga Bitcoin dari waktu ke waktu, meskipun tidak mencakup semua aspek pasar cryptocurrency. Untuk kondisi data terdapat Missing value yang akan dibersihkan di data preparation.

#### Bitcoin Price Chart
![gambar](https://github.com/user-attachments/assets/ee399dd3-f3c9-4fe6-b1fa-b3f4f189e31b)

## Data Preparation
* **Pengecekan Data**: Dataset ini telah dibersihkan dari nilai yang hilang. Nilai null dihilangkan dengan drop.
* **Format Tanggal**: Kolom 'Date' diubah formatnya menggunakan `pd.to_datetime` dan diatur sebagai indeks.
* **Feature Selection**: Hanya kolom 'Date' dan 'Close' yang digunakan. Kolom harga diubah menjadi float dan dinormalisasi menggunakan `MinMaxScaler`.
* **Normalisasi Data**: Normalisasi digunakan untuk menghindari masalah stabilitas numerik pada algoritma Machine Learning.
* **Pembagian Data**: Dataset dibagi menjadi data latih dan data uji dengan proporsi 80% data latih dan 20% data uji menggunakan `train_test_split`.

## Modeling
* **Model yang Digunakan**: Model sequential dengan LSTM, lapisan Dense, dan Dropout. LSTM dipilih untuk kemampuannya dalam menangani data urutan dan memori jangka panjang.
* **Arsitektur Model**:
  
  ![gambar](https://github.com/user-attachments/assets/d8178bdb-ed64-4229-a38d-878ac01b8ac5)
* **Model Training**
  ![gambar](https://github.com/user-attachments/assets/7bb110aa-7aeb-4bac-b152-dfd4e3339f6c)
  Model ditrain untuk 500 epochs.
## Evaluasi Model
  ![gambar](https://github.com/user-attachments/assets/d7cd7802-a453-428b-a0db-aff605fbefec)
  - Final Training Loss: 0.0001
  - Final Validation Loss: 0.0002:

* **Interpretation**
  
  - Nilai loss yang rendah pada dataset pelatihan dan validasi menunjukkan bahwa model berfungsi dengan baik dalam meminimalkan kesalahan prediksi. Secara spesifik, nilai loss akhir pada pelatihan sebesar 0.0001 dan pada validasi sebesar 0.0002 menunjukkan tingkat kesalahan yang sangat rendah, yang umumnya merupakan hasil yang positif.
  - Meskipun nilai loss yang rendah, penting untuk menilai apakah model mengalami overfitting. Overfitting terjadi ketika model tampil baik pada dataset pelatihan dan validasi tetapi gagal untuk digeneralisasikan ke data baru yang belum pernah dilihat. Disarankan untuk mengevaluasi kinerja model pada dataset tambahan atau melalui cross-validation untuk memastikan ketahanan dan kemampuan generalisasi.
  - Fungsi loss yang digunakan dalam model ini adalah Mean Squared Error (MSE), yang cocok untuk tugas regresi di mana tujuan utamanya adalah meminimalkan selisih kuadrat rata-rata antara nilai yang diprediksi dan nilai sebenarnya. Pastikan bahwa MSE sesuai dengan skala dan karakteristik data Anda. Dalam kasus di mana prediksi atau fitur data memiliki karakteristik tertentu, mungkin perlu menggunakan metrik atau fungsi loss lain.

## Model Prediction
![gambar](https://github.com/user-attachments/assets/d04fe768-0b1c-45b9-a39e-1315d319727c)

* **Prediction Summary**
Prediksi model telah divisualisasikan, menunjukkan harga Bitcoin yang diperkirakan berdasarkan data historis yang diberikan. Hasil prediksi memberikan wawasan tentang tren harga di masa depan, yang dapat membantu investor dalam membuat keputusan yang terinformasi. Meskipun demikian, satu hal yang pasti adalah bahwa prediksi ini tidak terlalu baik. LSTM mengalami kesulitan dalam memprediksi harga Bitcoin.
