Pilih lebih dari satu : Quiz: Apa tujuan dari Market Basket Analysis?
Apa tujuan dari Market Basket Analysis?
JAWABAN

Untuk menemukan pola unik dari sebuah dataset transaksi
Mengenali pelanggan secara lebih personal
Membuat paket produk yang bisa meningkatkan penjualan
Menyusun produk pada rak atau website yang berhubungan erat
Menemukan jarak terpendek dengan para customer

**Tujuan dari Market Basket Analysis** adalah:

-  Untuk menemukan pola unik dari sebuah dataset transaksi.
-  Membuat paket produk yang bisa meningkatkan penjualan.
-  Menyusun produk pada rak atau website yang berhubungan erat.




#Menggunakan library arules
library(arules)

#Membaca transaksi dari file data_transaksi.txt
transaksi <- read.transactions(file="https://storage.googleapis.com/dqlab-dataset/data_transaksi.txt", format="single", sep="\t", cols=c(1,2), skip=1)

#Menampilkan data transaksi dengan print dan inspect 
inspect(transaksi)

#Menghasilkan model Market Basket Analysis
mba <- apriori(transaksi,parameter = list(supp = 0.1, confidence = 0.5))

#Menampilkan paket produk
inspect(subset(mba, lift>1))

Kode yang Anda berikan adalah contoh penggunaan library arules dalam bahasa pemrograman R untuk melakukan analisis Market Basket Analysis. Saya akan menjelaskan setiap langkah yang Anda lakukan dalam kode tersebut:

**Menggunakan Library arules**: Anda mengimpor library arules, yang digunakan untuk melakukan analisis aturan asosiasi, termasuk Market Basket Analysis.

**Membaca Transaksi dari File**: Anda membaca data transaksi dari file "data_transaksi.txt" yang tersimpan di lokasi yang diberikan dalam URL. Anda mengatur format file sebagai "single" dan menentukan bahwa kolom 1 dan 2 dari file ini akan digunakan sebagai transaksi. Anda juga melewati baris pertama yang berisi header dengan skip=1.

**Menampilkan Data Transaksi**: Anda menggunakan fungsi inspect untuk menampilkan data transaksi yang telah dibaca. Ini membantu Anda memeriksa apakah data transaksi telah dibaca dengan benar.

**Menghasilkan Model Market Basket Analysis**: Anda membuat model Market Basket Analysis menggunakan fungsi apriori. Anda mengatur parameter supp (support) sebesar 0.1 (10%) dan confidence sebesar 0.5 (50%). Ini berarti Anda hanya akan mempertimbangkan aturan yang memiliki tingkat support minimal 10% dan tingkat confidence minimal 50%.

**Menampilkan Paket Produk**: Anda menggunakan fungsi inspect lagi untuk menampilkan aturan-aturan yang telah dihasilkan oleh model Market Basket Analysis. Anda menggunakan subset untuk hanya menampilkan aturan-aturan yang memiliki nilai "lift" lebih dari 1. Lift adalah salah satu metrik penting dalam Market Basket Analysis yang mengukur sejauh mana dua produk berkaitan satu sama lain.

Dengan demikian, kode ini membantu Anda melakukan analisis Market Basket Analysis pada data transaksi yang telah dibaca, dan menampilkan aturan-aturan asosiasi yang relevan berdasarkan tingkat support, confidence, dan lift yang telah Anda tentukan.
