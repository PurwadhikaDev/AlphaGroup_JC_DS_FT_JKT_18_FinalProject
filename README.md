# AlphaGroup_JC_DS_FT_JKT_18_FinalProject

# E-Commerce Customer Churn 
   by: 
1. Muhammad Nanda Reza Putra
2. Andri Rifky Aditama

# Business Problem Understanding

## Context
Perkembangan Teknologi telah memtransformasi insdustri perdagangan dunia. Pergeseran ini membuat pola perdagangan dunia juga beralih ke perdagangan secara online. Banyak Perusahaan yang membuat pelanggan melakukan **Churn**. **Churn** pada E-Commerce adalah suatu perilaku pelanggan berhenti melakukan transaksi pada perusahaan E-Commerce. Nilai dari pelanggan yang melakukan **Churn** mengindikasikan seberapa banyak pelanggan yang tidak melakukan transaksi lagi pada perusahaan ini. Tingginya **Churn Rate** adalah sesuatu yang ingin dihindari pada bisnis ini. **Churn Rate** yang tinggi mengindikasikan bahwa pelanggan mungkin tidak puas dengan barang atau jasa diberikan. Perusahaan akan lebih mempertahankan pelanggan, karena dibutuhkan biaya lebih besar untuk mencari pelanggan yang baru. Sebuah perusahaan 'X' pada suatu negara memiliki bisnis perusahaan *E-Commerce* dimana para pelanggan dapat bertransaksi untuk berbelanja peralatan elektronik (Laptop & aksesoris dan Handphone), pakaian , grosir dan lainnya. Perusahaan ini ingin mengetahui *behavior* pelanggan yang melakukan **Churn** dan ingin mengurangi jumlah pelanggan yang **Churn**. Dilakukan sebuah model prediksi yang tepat untuk menentukan pelanggan yang berhenti bertransaksi (churn) atau tidak menggunakan machine learning. Dengan target yang ditentukan sebagai berikut :

Target: 
* 0 : Customer tidak Churn 
* 1 : Customer Churn


# Problem Statement

Pada suatu perusahaan tingginya pelanggan yang melakukan *Churn* merupakan suatu indikator tingkat kegagalan suatu perusahaan E-Commerce. Dimana apabila *Churn rate* sebesar 5 % maka kita akan kehilangan 5 % dari pelanggan tersebut. Tentu, Perusahaan sebisa mungkin harus menekan nilai *churn rate* ini sekecil mungkin. Sehingga diperlukan upaya untuk mengurangi persentase pelanggan yang melakukan *Churn*. Seperti disebutkan sebelumnya bahwa untuk mencari pelanggan lebih dibutuhkan biaya yang lebih besar dibandingkan mempertahankan pelanggan [sumber](https://www.woopra.com/blog/churn-rate-vs-retention-rate#:~:text=Customer%20churn%20rate%20is%20the,up%20and%20stay%20with%20you.). menurut [sumber](https://www.woopra.com/blog/churn-rate-vs-retention-rate#:~:text=Customer%20churn%20rate%20is%20the,up%20and%20stay%20with%20you.) apabila kita melakukan suatu *ads* untuk menarik pelanggan baru dgn biaya sebesar 100 dolar perbulan untuk mendapatkan pelanggan baru dan biaya perpelanggan perbulan sebesar 50 dolar, maka setidaknya setiap bulan harus ada 2 pelanggan untuk menutup biaya pelanggan baru tersebut. Salah satu cara perusahaan telekomunikasi mempertahankan pelanggannya agar tidak melakukan Churn yaitu memberikan insentif retensi terhadap pelanggan. Insentif retensi terdiri dari berbagai macam seperti memberikan potongan harga, memberikan paket layanan yang menarik, memberikan prioritas pelayanan dan lain-lain. Namun, kebijakan pemberian insentif retensi belum dilakukan secara efektif. Kebijakan tersebut sering ditemui berbagai kendala bahkan membuat
perusahaan semakin merugi. 


## Goals

Sehingga dari permasalahan yang ada, perusahaan ingin memiliki kemampuan untuk dilakukannya prediksi kemungkinan seorang pelanggan akan *Churn* atau tidak. Untuk memfokuskan upaya retensi,pemberian insentif meningkatkan pelayanan pada pelanggan yang terindikasi akan melakukan *Churn*. Selain itu juga agar perusahaan mengetahui faktor yang memengaruhi pelanggan bertahan agar strategi bisnis yang dilakukan tepat dengan keinginan pelanggan untuk menurunkan tingkat dari pelanggan yang *Churn*.

## Analytics Approach

Akan dilakukan analisa bagaimana faktor pembeda dari pelanggan yang melakukan *Churn* dan tidak. selanjutnya akan dibuat model klasifikasi untuk memprediksi probabilitas dari pelanggan akan melakukan *Churn* atau tidak.


## Confussion Metric

![](https://txt.cohere.ai/content/images/2022/06/feature.png)


Target utama dalam masalah ini adalah pelanggan yang berhenti berlangganan (Churn), seperti target yang sudah disebutkan pada context sebelumnya yaitu:

Target:
* 0 : Tidak Churn 
* 1 : Churn

False Positive yaitu pelanggan yang aktualnya tidak tetapi diprediksi churn.<br>
**Konsekuensi** : Tidak efektif dalam pemberian insentif. <br>
False negative yaitu pelanggan yang aktualnya churn tetapi diprediksi tidak akan churn. <br>
**Konsekuensi** : Kehilangan pelanggan.

Berdasarkan Metric Evaluation yang ada akan digunakan serta konsekuensi yang ada. Akan dibuat model yang akan mengurangi resiko kehilangan pelanggan karena untuk mendapatkan pelanggan baru membutuhkan biaya lebih banyak dibandingkan kita mempertahankan pelanggan yang ada. Sehingga kita akan fokus pada nilai FN dengan mendapatkan nilai recall yang tinggi dan tetap membandingkan nilai precision agar tidak terlalu jauh. Kita ingin recall dan precisionya seimbang sehingga digunakan metric f1_score dengan data yang imbalance. Dilakukan juga Sampling Undersampling (NearMiss) dan Oversampling(SMOTE). Selanjutnya akan dibandingkan model mana yang paling cocok untuk digunakan pada kasus ini.

## Data Understanding
Sumber Data: [E-Commerce Dataset](https://www.kaggle.com/datasets/ankitverma2010/ecommerce-customer-churn-analysis-and-prediction)

Dataset merupakan data dari sebuah perusahaan terkemuka 'X'
Terdapat 20 kolom yang menmemberikan informasi mengenai ID customer, churn atau tidak, login menggunakan device apa dan lain-lain.

## Attribute Information

### Attribute Information

| Attribute | Data Type | Description |
| --- | --- | --- |
| Customer ID | Int | Unique customer ID |
| Churn | Int | Churn Flag 0 : Tidak Churn, 1 : Churn |
| Tenure | Float | Tenure of customer in organization |
| PreferredLoginDevice | Text | Preferred login device of customer |
| CityTier | Int | City tier |
| WarehouseToHome | Float | Distance in between warehouse to home of customer |
| PreferredPaymentMode | Text | Preferred payment method of customer |
| Gender | Text | Gender of customer |
| HourSpendOnApp | Float | Number of hours spend on mobile application or website |
| NumberOfDeviceRegistered | Int | Total number of deceives is registered on particular customer |
| PreferedOrderCat | Object | Preferred order category of customer in last month |
| SatisfactionScore | Int | Satisfactory score of customer on service |
| MaritalStatus | Object | Marital status of customer|
| NumberOfAddress | Int | Total number of added added on particular customer |
| Complain | Int | Any complaint has been raised in last month |
| OrderAmountHikeFromlastYear | Float | Percentage increases in order from last year |
| CouponUsed | Float | Total number of coupon has been used in last month |
| OrderCount | Float | Total number of orders has been places in last month |
| DaySinceLastOrder | Float | Day Since last order by customer |
| CashbackAmount | Float | Average cashback in last month |

# Kesimpulan & Rekomendasi 
1. Dari analisa yang sudah dilakukan model yang memiliki performa paling maksimal yaitu menggunakan model **GradientBoost Classifier** dengan dilakukan hyperparameter tuning.
2. Parameter yang paling baik menggunakan parameter : max_depth=5, n_estimators=200, 'model__learning_rate': 0.1, 'model__max_depth': 5,'model__n_estimators': 200.
3. Nilai Recall dan Precision dari kelas positif yaitu masing-masing sebesar **87% dan 79%**
4. Fitur paling berpengaruh pada model yaitu **Tenure, NumberOfAddress dan Complain**
5. Dengan menggunakan model ini dapat menghemat sampai dengan **70 %** total pengeluaran perusahaan dibandingkan dengan perusahan tidak menggunakan model.

**Rekomendasi** :
1. Dapat menggunakan algoritma Machine Learning lain seperti CatBoost, LightLgbm.
2. Menambahkan Feature lain seperti Tanggal Transaksi, kota asal, Durasi barang sampai ke rumah pelanggan dan lain-lain yang berhubungan dengan Perusahaan E-Commerce
3. Menggunakan sumber lain dalam perhitungan biaya Customer Acquisition dan mempertahankan pelanggan.
4. Data yang di analisa tidak seimbang (Imbalance) sehingga dapat menggunakan algoritma statistik lain.

**Rekomendasi Bisnis**
1. Memberikan promo yang lebih banyak pada pelanggan baru agar pelanggan tersebut dapat bertahan dalam periode yang lama. Perusahaan dapat melakukan strategi bisnis agar pelanggan dapat tetap setia menggunakan transaksi barang platform E-commerce dengan memberikan komunikasi yang baik antara pelanggan dan Perusahaan karena komunikasi yang baik akan membuat pelanggan tetap setia menggunakan layanan yang ada pada E-Commerce kita. Selain itu juga dapat meningkatkan kualitas produk yang dijual agar pelanggan tetap setia dan akan melakukan repeat order pada transaksi berikutnya. 
2. Dan juga daripada menunggu complain yang datang, mulailah dengan mengembangkan keterampilan komunikasi dengan pelanggan serta pastikan complain yang datang dari pelanggan haruslah ditindak lanjuti secara cepat dan tepat waktu untuk memastikan kebutuhan pelanggan terpenuhi.
3. Perusahaan dapar melakukan campaign segemented terhadap pelanggan yang berstatus single karena memiliki Churn lebih tinggi.
4. Meningkatkan kembali kualitas produk terutama pada kategori mobile phone agar pelanggan tetap setia menggunakan layanan E-Commerce.
