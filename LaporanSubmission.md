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

Data ini memberikan gambaran tentang harga Bitcoin dari waktu ke waktu, meskipun tidak mencakup semua aspek pasar cryptocurrency.

#### Bitcoin Price Chart
![gambar](https://github.com/user-attachments/assets/ee399dd3-f3c9-4fe6-b1fa-b3f4f189e31b)

## Data Preparation
* **Pengecekan Data**: Dataset ini telah dibersihkan dari nilai yang hilang.
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
  
  - The low loss values on both training and validation datasets suggest that the model performs well in minimizing the prediction error. Specifically, the final           training loss of 0.0001 and the final validation loss of 0.0002 indicate a very low error rate, which is generally a positive outcome.
  - Despite the low loss values, it is crucial to assess whether the model is overfitting. Overfitting occurs when a model performs well on training and validation          datasets but fails to generalize to new, unseen data. It is recommended to evaluate the model's performance on additional datasets or through cross-validation           to ensure robustness and generalizability.
  - The loss function used in this model is Mean Squared Error (MSE), which is suitable for regression tasks where the goal is to minimize the average squared       difference between predicted and actual values. Confirm that MSE aligns with the scale and nature of your data. In cases where predictions or data features have specific characteristics, it might be necessary to use other metrics or loss functions.

## Model Prediction
![gambar](https://github.com/user-attachments/assets/d04fe768-0b1c-45b9-a39e-1315d319727c)

***Prediction Summary**
The model’s predictions have been visualized, showing the forecasted Bitcoin prices based on the historical data provided. The prediction results offer insights into future price trends, which can assist investors in making informed decisions. Although one thing is certain it is not a really good predictions. LSTM have a hard time  predicting the price of Bitcoin.
