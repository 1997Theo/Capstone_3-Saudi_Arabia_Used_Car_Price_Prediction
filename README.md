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
