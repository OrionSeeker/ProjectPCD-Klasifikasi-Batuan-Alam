# Klasifikasi Batuan Alam
Project ini memiliki tujuan untuk membantu pakar batu agar dapat lebih cepat dan mudah dalam mengidentifikasi batu-batuan alam, sehingga pekerjaannya menjadi lebih efisien dan membantu pakar batu tersebut mengidentifikasi batuan alam yang memiliki nilai ekonomi tinggi misalnya quartz dan marble, sehingga dapat memperoleh keuntungan yang lebih tinggi

## Anggota Tim
1. Michael Effendy (F1D022012)
2. Karunia Putri (F1D022010)
3. Elyana Astuty (F1D022041)
4. Ridho Adhimam Putra (F1D022090)
5. Agus Gunawan (F1D020002)

## Augmentasi yang Digunakan
- Rotasi sudut 90, 180, dan 270 derajat
- Pencerminan sumbu x, sumbu y, dan sumbu x dan y

## Preprocessing yang Digunakan
1. Mengubah citra menjadi grayscale = citra yang awalnya memiliki 3 layer, yaitu RGB, diubah menjadi 1 layer saja yaitu grayscale. Alasannya adalah untuk mempercepat waktu komputasi (cukup menghitung satu layer) dan GLCM memerlukan citra grayscale
2. Menaikkan brightness = menambah nilai intensitas setiap piksel pada citra, jadi citra terlihat lebih cerah. Membantu memperjelas detail yang ada yang sebelumnya tidak terlihat saat brightnessnya rendah.
3. Melakukan clipping = Membatasi range nilai piksel menjadi 0 - 255. Jadi yang di atas 255 dipotong jadi 255, yang di bawah 0 dipotong jadi 0.
4. Melakukan ekualisasi histogram secara adaptif (CLAHE) = Meningkatkan kontras citra secara lokal. CLAHE membagi citra menjadi beberapa blok kecil dan dilakukan ekualisasi per blok tersebut, kemudian digabungkan dan batas antar blok diperhalus. Perbedaannya dari ekualisasi global adalah dengan CLAHE ini dapat dicegah overamplifikasi.
5. Membuat mask dan menghapus background menggunakan algoritma otsu = Otsu adalah algoritma untuk mencari batasan optimal untuk melakukan segmentasi atau thresholding pada citra. Algoritma ini mencari nilai batas yang meminimalkan varians dalam kelas antar-piksel, menjadi pemisahan antara background dengan foregroundnya. Mask hasil dari algoritma otsu itu digunakan untuk menentukan bagian mana dari citra yang dihapus. 

## Akurasi, Precision, Recall, dan F1-Score dari Cross Validation
Pelatihan dan validasi model dilakukan secara cross validation untuk menghindari overfitting dan membuat model mampu menangani data yang lebih general.
### Sebelum Augmentasi dan Preprocessing
![image](https://github.com/OrionSeeker/ProjectPCD-Klasifikasi-Batuan-Alam/assets/143796680/570877c3-4b8f-4328-b057-73467957c4b3)
Dapat dilihat bahwa akurasi tertinggi untuk percobaan tanpa augmentasi dan tanpa preprocessing dipegang oleh model Random Forest (37,3%)

### Sesudah Augmentasi dan Sebelum Preprocessing
![image](https://github.com/OrionSeeker/ProjectPCD-Klasifikasi-Batuan-Alam/assets/143796680/a1ed6eda-7d0e-4467-85b5-8a52328a5b73)
Dapat dilihat bahwa akurasi tertinggi untuk percobaan dengan augmentasi dan tanpa preprocessing dipegang oleh model Random Forest (61%)

### Sesudah Augmentasi dan Preprocessing
![image](https://github.com/OrionSeeker/ProjectPCD-Klasifikasi-Batuan-Alam/assets/143796680/a37becf3-36a8-4348-9495-5c7044d43749)
Dapat dilihat bahwa akurasi tertinggi untuk percobaan dengan augmentasi dan dengan preprocessing dipegang oleh model Random Forest (72,6%)
