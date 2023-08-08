# Capstone_3-Saudi_Arabia_Used_Car_Price_Prediction

**Project Description**
Proyek bertujuan untuk membuat model yang dapat memprediksi harga Mobil Bekas Arab Saudi untuk membuat sistem rekomendasi untuk perusahaan marketplace mobil bekas di saudi arabia. Pada set ini terdapat langkah-langkah yang dilakukan yaitu Defining Business Problem, Data Understanding, Exploratory Data Analysis, Data Analysis, Data Preprocessing (Data Cleaning and Feature Engineering), Modeling (Benchmarking Models, Hyperparameter Tuning, Financial Impact Analysis of the model), serta memberikan Kesimpulan dan Rekomendasi berdasarkan kinerja model sebagai Data Scientist kepada pemangku kepentingan.

**Problem Statement**
Karena harga jual mobil ditentukan langsung oleh penjual, terkadang penjual mengalami kebingungan dalam menentukan harga yang pantas untuk mobil bekas yang akan dijual, dimana terdapat kemungkinan bahwa penjual akan memberikan harga yang sangat tinggi sehingga harga-harga mobil yang ada pada platform akan menjadi kurang relevan terhadap pasar, sehingga pembeli juga menjadi enggan untuk bertransaksi di platform dan pada akhirnya platform tersebut akan menjadi sepi dan ada kemungkinan untuk bangkrut.

Cara paling jitu untuk menjadikan platform Syarah menjadi platform nomor satu adalah `Sistem rekomendasi harga mobil jual yang akurat`, agar penjual mendapatkan profit yang sepadan dan pembeli juga mendapatkan mobil yang sesuai selera dengan harga yang 'reasonable' (masuk akal). 
Hal ini sangat dibutuhkan agar baik penjual dan pembeli mempercayai perusahaan sebagai `perusahaan yang capable dalam menciptakan kondisi market yang tidak overprice maupun underprice sehingga baik penjual dan pembeli tidak akan dirugikan.`

**Goals** 
Agar dapat mewujudkan sistem rekomendasi yang relevan, perusahaan membutuhkan suatu tools untuk dapat memprediksi harga mobil bekas seakurat mungkin dengan harga pasar berdasarkan data-data pada mobil tersebut seperti Tahun keluaran mobil, Ukuran Mesin mobil, Fitur pada mobil, Tipe mobil, Perusahaan Pembuat mobil, Jarak Tempuh mobil, Asal mobil, Region mobil yang dijual, dan Transmisi pada mobil. Adanya perbedaan pada fitur-fitur tersebut sudah pasti menyebabkan perbedaan pada harga jual mobil.

Syarah berharap dengan adanya sistem rekomendasi yang memprediksi harga secara fair, maka jumlah user yang aktif pada platform akan bertambah. Sehingga tentu saja hal itu akan menaikkan revenue perusahaan, dalam konteks ini 'paid ads' yang dipurchase oleh pembeli

**Metric Evaluation**
Untuk melakukan evaluasi pada model yang dibuat,  metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana RMSE adalah nilai rata-rata akar kuadrat dari error, MAE adalah absolut nilai rata-rata dari error, sedangkan MAPE adalah rata-rata persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai RMSE, MAE, dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi harga sewa sesuai dengan limitasi fitur yang digunakan. Hanya saja pada kasus ini, kita akan `menekankan penilaian pada metrik MAE dan MAPE`, dimana dari sisi business owner ataupun penjual mobil, `akan lebih mudah menginterpretasikan error dalam bentuk persen ataupun nilai toleransinya` terhadap harga keseluruhan.

Selain itu, kita juga bisa menggunakan nilai R-squared atau adj. R-squared jika model yang nanti terpilih sebagai final model adalah model linear. Nilai R-squared digunakan untuk mengetahui seberapa baik model dapat merepresentasikan varians keseluruhan data. Semakin mendekati 1, maka semakin fit pula modelnya terhadap data observasi. Namun, metrik ini tidak valid untuk model non-linear.

**Setelah melakukan Analisis, Modeling, dan Tuning, didapatkan Kesimpulan dan Rekomendasi Sebagai Berikut :**

**Conclusion**
Berdasarkan hasil pemodelan diatas, didapatkan kesimpulan sebagai berikut :

- **Saat melakukan analisis karakteristik mobil yang bersifat Negotiable, tidak ditemukan karakteristik khusus kecuali dari asal mobil tersebut. Dimana pada data mobil bekas yang 'Origin'-nya memiliki nilai 'Unknown', lebih banyak mobil bekas yang harganya 'Negotiable' dibandingkan dengan mobil bekas yang tidak Negotiable**

- **Limitasi pada model adalah sebagai berikut :**

    | **Fitur** | **Tipe Data** | **Limitasi** |
    | --- | --- | --- |
    | Type | Object | Semua nilai unik kolom 'Type' pada dataset (347 tipe mobil) |
    | Region | Object | Semua nilai unik kolom 'Region' pada dataset (27 region)|
    | Make | Object | Semua nilai unik kolom 'Make' pada dataset (27 Perusahaan) |
    | Gear_Type | Object | Semua nilai unik kolom 'Gear Type' pada dataset (Automatic dan Manual) |
    | Origin | Object | Semua nilai unik kolom 'Origin' pada dataset (4 daerah asal) |
    | Options | Object | Semua nilai unik kolom 'Options Type' pada dataset (Full, Semi Full, Standard) |
    | Year | Float | Mobil yang dibuat pada diantara tahun 1997 sampai 2022 |
    | Engine_Size | Float | Mobil yang kapasitas mesinnya berukuran 1 L - 8 L |
    | Mileage | Object | Mobil yang Jarak tempuhnya 100 KM - 381500 KM |
    | Price | Integer | Mobil dengan range harga 10000 SAR - 300000 SAR | 
&ensp;
  
- **Hyperparameter tuning berhasil meningkatkan performa model dalam semua metrik (RMSE, MSE, dan MAPE) dengan hasil sebagai berikut :**

    - RMSE, MAE & MAPE sebelum tuning   : 21881, 12889, 17.9%
    - RMSE, MAE & MAPE setelah tuning 2 : 21497, 12165, 16.9%

&ensp;
- **Model yang dipilih adalah model XGBoost yang ditransformasi ke skala logaritmik terlebih dahulu, kemudian ditransformasi kembali dengan fungsi inverse agar dapat diiterpretasi. Pemilihan ini berdasarkan dari proses cross validation dan model XGBoost mendapatkan nilai score tertinggi dalam semua metrik. Model dengan transformasi logaritmik ini juga memberikan hasil yang lebih baik dibandingkan model tanpa ditransformasi ke skala logaritmik. Hal ini disebabkan karena rentang variasi data yang sangat besar, sehingga model akan lebih mudah belajar dengan skala logaritmik dibandingkan skala normal**

- **Parameter tuning terbaik yang didapat pada model XGBoost adlaah sebagai berikut :**
    - model__regressor__subsample: 0.9
    - model__regressor__reg_alpha: 0.1
    - model__regressor__n_estimators: 152
    - model__regressor__max_depth: 7
    - model__regressor__learning_rate: 0.15
    - model__regressor__colsample_bytree: 0.8
    
&ensp;
- **Nilai MAPE yang didapatkan setelah tuning adalah 16.9 %, yang mana dapat dikategorikan sebagai 'good forecasting' menurut Lewis, C. D.**
    
- **Model memiliki hasil prediksi 49 % yang underestimate, dan 51 % yang overestimate, sehingga dapat dikatakan bahwa model ini merupakan model yang cukup balance dalam prediksinya**

- **Lima Fitur yang paling berpengaruh terhadap pembentukan harga mobil bekas pada model adalah Year (Tahun Produksi Mobil), Make (Perusahan Pembuat Mobil), Engine Size (Kapasitas Mesin Mobil), dan Options (Pilihan Fitur Mobil), dan Type (tipe mobil)**

- **Pada test set, total transaksi yang diprediksi lebih kecil sebesar 4% dari total transaksi aktual, yang mana hal itu sudah cukup baik karena tidak terlalu berbeda jauh**
  
**Recommendation**
Berdasarkan pemodelan dan analisis data yang sudah dilakukan, diberikan rekomendasi sebagai berikut :

- **Untuk penjual yang berasal dari Origin (wilayah) 'Unknown', sebaiknya diberikan rekomendasi untuk membuat harga mobil yang Negotiable**

- **Untuk menguji efektivitas model pada kondisi real, lakukan A/B testing terhadap lakunya mobil antara mobil yang dijual dengan menggunakan harga prediksi dengan mobil yang dijual tanpa menggunakan harga prediksi (ditentukan oleh user langsung tanpa ada rekomendasi)**

- **Perusahaan dianjurkan untuk membuat sistem rekomendasi harga dengan menaikkan harga 5 % dari harga prediksi agar revenue perusahaan menyamai revenue aktual. Selain itu, sebaiknya disosialisasikan bahwa sistem rekomendasi harga ini memiliki nilai toleransi +/- 17% terhadap harga pasar, agar user menjadi aware dan dapat mempertimbangkan hal itu dalam menentukan harga jual mobilnya.**

- **Untuk meningkatkan performa model, dapat dilakukan hal-hal berikut :**
    - Membedakan mobil antik dan mobil non antik berdasarkan tahun pembuatan mobil, dimana semua mobil yang tahun pembuatannya sudah melewati 30 tahun dari tahun terkini. Setelah itu bisa dikembangkan model independen terhadap mobil antik tersebut

    - Membedakan mobil 'luxury' dan mobil 'komersil' berdasarkan tipe, make, dan harga mobilnya. Setelah itu, kembangkan model independen untuk mobil 'komersil' (contohnya, mobil dengan harga < 100000 SAR) dan mobil 'luxury' (contohnya, mobil dengan harga > 100000 SAR). Hal ini diperlukan untuk membuat model yang akurat untuk masing-masing cluster sehingga harapannya nilai RMSE, MAE, dan MAPE bisa turun secara drastis

    - Jika memungkinkan untuk mendapatkan lebih banyak data, boleh dicoba untuk menggunakan model yang lebih kompleks seperti neural network agar prediksi/rekomendasi harga yang dihasilkan lebih akurat. Tetapi, jika kondisi datanya dan fitur-fiturnya tidak dapat ditambah, kemungkinan besar hasilnya tidak akan berubah secara signifikan

    - Jika memungkinkan, sebaiknya ditambahkan fitur kondisi inspeksi pada data dimana dapat dikasifikasikan menjadi beberapa kategori (contoh : sangat baik, baik, cukup, kurang, dan sangat kurang). Hal ini tentunya akan sangat membantu model untuk membentuk harga prediksi.

    - Jika memungkinkan, sebaiknya ditambahkan fitur yang berisi metode pembayaran yang diterima oleh penjual (apakah cash atau cicilan). Hal ini sudah pasti mempengaruhi harga mobil yang akan dijual karena ada pengaruh dari nilai uang itu sendiri (faktor inflasi dll)

- **Jika memungkinkan, sebaiknya pada data ditambahkan kolom user (penjual) agar kita dapat melihat penjual mana yang telah menjual mobil paling banyak, sehingga kita dapat melakukan strategic partnership dengan user tersebut untuk dapat mengejar target perusahaan, yaitu memiliki Gross Transaction Value setinggi mungkin**
