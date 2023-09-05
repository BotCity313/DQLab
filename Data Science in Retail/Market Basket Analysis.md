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



Berikut adalah kode yang setara dalam bahasa pemrograman Python menggunakan library mlxtend untuk melakukan analisis Market Basket Analysis:


# Menggunakan library mlxtend
from mlxtend.frequent_patterns import apriori
from mlxtend.frequent_patterns import association_rules

# Membaca transaksi dari file data_transaksi.txt
import pandas as pd
df = pd.read_csv("https://storage.googleapis.com/dqlab-dataset/data_transaksi.txt", sep="\t", header=None, skiprows=1, usecols=[0, 1])

# Menampilkan data transaksi
print(df)

# Menghasilkan model Market Basket Analysis
frequent_itemsets = apriori(df, min_support=0.1, use_colnames=True)
rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1)

# Menampilkan aturan asosiasi
print(rules)


Dalam kode Python ini, kita menggunakan library mlxtend untuk melakukan analisis Market Basket Analysis. Kami membaca data transaksi dari file "data_transaksi.txt" menggunakan Pandas, lalu menghasilkan model Market Basket Analysis dengan menghitung itemset yang sering muncul (frequent itemsets) dan aturan asosiasi (association rules) berdasarkan tingkat support dan lift yang telah ditentukan.


Parameter specification:
 confidence minval smax arem  aval originalSupport maxtime support minlen
        0.5    0.1    1 none FALSE            TRUE       5     0.1      1
 maxlen target   ext
     10  rules FALSE

Algorithmic control:
 filter tree heap memopt load sort verbose
    0.1 TRUE TRUE  FALSE TRUE    2    TRUE

Absolute minimum support count: 1 

set item appearances ...[0 item(s)] done [0.00s].
set transactions ...[4 item(s), 10 transaction(s)] done [0.00s].
sorting and recoding items ... [4 item(s)] done [0.00s].
creating transaction tree ... done [0.00s].
checking subsets of size 1 2 3 done [0.00s].
writing ... [16 rule(s)] done [0.00s].
creating S4 object  ... done [0.00s].

> #Menampilkan paket produk
> inspect(subset(mba, lift>1))
    lhs                     rhs        support confidence lift    
[1] {Pet Food}           => {Sirup}    0.4     0.8000000  1.333333
[2] {Sirup}              => {Pet Food} 0.4     0.6666667  1.333333
[3] {Gula,Pet Food}      => {Sirup}    0.1     1.0000000  1.666667
[4] {Pet Food,Teh Celup} => {Sirup}    0.2     0.6666667  1.111111

Pesan ini merupakan keluaran dari proses analisis Market Basket Analysis yang telah Anda jalankan. Di bawah ini, saya akan menjelaskan hasil dari analisis tersebut dalam bahasa Indonesia:

Hasil analisis menunjukkan aturan-aturan asosiasi yang ditemukan berdasarkan parameter-parameter yang Anda atur sebelumnya:

Aturan: {Pet Food} => {Sirup}

Support: 0.4
Confidence: 0.8000000
Lift: 1.333333


Aturan: {Sirup} => {Pet Food}

Support: 0.4
Confidence: 0.6666667
Lift: 1.333333



Aturan: {Gula, Pet Food} => {Sirup}

Support: 0.1
Confidence: 1.0000000
Lift: 1.666667



Aturan: {Pet Food, Teh Celup} => {Sirup}

Support: 0.2
Confidence: 0.6666667
Lift: 1.111111


Dalam konteks analisis Market Basket, aturan-asosiasi ini mengindikasikan hubungan antara item yang dibeli bersama-sama dalam transaksi. Nilai Support mengukur seberapa sering kombinasi item tersebut muncul dalam transaksi, Confidence mengukur seberapa sering item yang satu muncul jika item lainnya ada, dan Lift mengukur seberapa kuatnya hubungan antara item-item tersebut dibandingkan dengan kemunculan acak.

Misalnya, aturan pertama menunjukkan bahwa jika pelanggan membeli "Pet Food," maka mereka juga memiliki 80% kemungkinan untuk membeli "Sirup." Lift sekitar 1.33 mengindikasikan bahwa hubungan antara keduanya lebih kuat daripada hubungan acak.

Ini adalah hasil yang berguna untuk mengidentifikasi pola pembelian pelanggan dan dapat digunakan untuk perencanaan stok, rekomendasi produk, dan strategi pemasaran yang lebih baik.




AIPRM - ChatGPT Prompts
  Favorites
  AIPRM
Public
Own
  Hidden
  Add List
Topic

All
Activity

All
Sort by

Top Votes Trending
Model

Not specific

Search
Prompts per Page

12
Showing 1 to 12 of 4251 Prompts
Prev
Next

Human Written |100% Unique |SEO Optimized Article
SEO / Writing
·
Jumma
·
2 weeks ago
GPT-3.5-turbo GPT-4 Human Written | Plagiarism Free | SEO Optimized Long-Form Article With Proper Outline [Upgraded Version]

  6.9M
  5.2M
  1.2K  

Midjourney Prompt Generator
Generative AI / Midjourney
·
kenny
·
5 months ago
Outputs four extremely detailed midjourney prompts for your keyword.

  1.7M
  1.1M
  502  

Yoast SEO Optimized Content Writer
Copywriting / Writing
·
Luna Perkins
·
2 months ago
Write detail YoastSEO optimized article by just putting blog title. I need 5 more upvotes so that I can create more prompts. Hit upvote(Like) button.

  211.8K
  130.3K
  495  

Fully SEO Optimized Article including FAQ's
SEO / Writing
·
Muhammad Talha (MTS)
·
3 hours ago
GPT-3.5-turbo GPT-4 GPT-4 browsing GPT-4 plugins [Version: 3.1] Enjoyed the prompt? Give it an upvote! | Yoast and Rank Math SEO Optimized | Create a 100% Unique | Plagiarism Free Content with | Title | Meta Description | Headings with Proper H1-H6 Tags | up to 2000 Words Article with FAQs, and Conclusion.

  2.2M
  1.7M
  467  

Write Best Article to rank on Google
Copywriting / Writing
·
Faisal Arain
·
1 month ago
GPT-3.5-turbo GPT-4 Write Best Smart Article Best to rank no 1 on Google by just writing Title for required Post. If you like the results then please hit like button.

  1.3M
  868.9K
  395  

Write a Complete Book in One Click
Copywriting / Writing
·
Md Mejbahul Alam
·
5 months ago
Write a full book with different chapters

  982.0K
  602.9K
  383  

Buyer Persona Legend
Marketing / Marketing
·
RonGPT
·
6 months ago
Generate detailed User Personas for your Business with data neatly organized into a table.

  314.8K
  152.3K
  370  

Keyword Strategy
SEO / Ideation
·
AIPRM
·
2 months ago
GPT-3.5-turbo Create a keyword strategy and SEO content plan from 1 [KEYWORD]

  1.2M
  837.7K
  352  

Human-like Rewriter - V1.6
Copywriting / Writing
·
pneb
·
6 months ago
Re-write your ai-generated article with this tool! You can get up-to 90-100% Human Generated score!

  1.2M
  828.8K
  351  

Get Monthly Content Calendar In 1 Click
Marketing / Marketing
·
Google Business Profile Services
·
3 months ago
Get a beautifully organized 4-week content calendar that targets your primary keyword using only transaction longtail keyword & clickbait style post titles. Try it out!

  577.3K
  331.1K
  350  

YouTube Script Creator
Copywriting / Script Writing
·
WilliamCole
·
6 months ago
Create captivating script ideas for your YouTube videos. Enter a short description of your video. Generates: Title, Scene, and Entire Script.

  820.3K
  465.8K
  349  

Outrank Article
SEO / Writing
·
AIPRM
·
2 months ago
GPT-3.5-turbo Outrank the competition with an in-depth, SEO-optimized article based on [YOUR COMPETITOR URL]. Be like your competition, just a little better ;-)

  1.4M
  982.6K
  346  

Add Public Prompt
Prompts per Page

12
Showing 1 to 12 of 4251 Prompts
Prev
Next
