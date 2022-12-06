# Laporan Proyek Machine Learning - Luthfan Hadi Hilsan

## Domain Proyek
Kepopuleran *anime* (animasi Jepang) telah memunculkan berbagai macam
produk *anime* seperti *action figure*, pernak-pernik bergambar anime, kostum,
komik Jepang, majalah-majalah *fashion* Jepang, bahkan tayangan animasi di
televisi didominasi oleh tayangan *anime*. 

Ada ribuan *anime* yang tersedia di internet. Sebagai pembuat aplikasi penyedia *anime*, sangat dibutuhkan sistem rekomendasi untuk mempermudah pengguna untuk menemukan anime genre yang sesuai untuk ditonton. Berdasarkan masalah ini, kita bisa menggunakan *machine learning* untuk mengatasinya.
## *Business Understanding*


### *Problem Statements*

- Bagaimana caranya mendapatkan *anime* dengan *genre* sejenis?.

### *Goals*

- Menggunakan metode *Content Based Filtering* bisa dibuatkan sistem rekomendasi *genre* anime yang sejenis. 


## *Data Understanding*
Dengan menggunakan dataset dari *Anime Recommendation Database 2020* yang didalamnya terdapat 35 kolom yang terdiri dari 2 atribut dan 33 fitur yang akan kita latih, dan terdapat 17561 baris yang terdiri dari 48 *genre*. Data dapat diunduh dari *kaggle* [*Anime Recommendation Database 2020*] (https://www.kaggle.com/datasets/hernan4444/anime-recommendation-database-2020).

### Variabel-variabel pada *Anime Recommendation Database 2020* yang dipakai pada model ini adalah sebagai berikut:

- *MAL_ID* : Nomor ID dari *anime*
- *Name* : Nama lengkap dari *anime*
- *Genres* : Jenis konten dari *anime* 
- *Score* : Rata rata penilaian pengguna terhadap *anime* tersebut
- *Episode* : Jumalah *episode*
- *Aired* : Tanggal *broadcast*
- *Premierd* : *Season premiere*
- *Producers* : Daftar dari produser 


## *Data Preparation*
Sebelum data digunakan, ada beberapa tahap yang dilakukan yaitu.
- *Explore Data*
    Pada tahap ini, akan dicek terlebih dahulu isi dari dataset, jumlah *genres*.
- *Data Filtering*
    Setelah dilihat isi dari dataset, dapat disimpulkan dari 35 kolom, akan dipakai 2 kolom yaitu kolom *name* dan *genres*. Diinisialkan dataset yang telah filter dengan nama '*data_filtered*'. Dari dataset tersebut, dipastikan telrebih dahulu apakah sudah tidak ada data *null* ataupun *duplicate*. 

## Modeling
Model yang akan dipakai untuk *anime recomendation* ini menggunakan *matrix tfidf* dan untuk menilai hubungan antar komponen matriks akan dicari dengan fungsi *cosine similarity*.

 1. *Matrix tfidf*
    Teknik matriks yang digunakan untuk menemukan representasi fitur penting dari setiap kategori yang akan di cobakan
 2. *Cosine similarity*
    Teknik matriks yang digunakan untuk menentukan seberapa mirip antar fitur yang dibandingkan. Nilai dari *cosine similarity* yaitu dari -1 hingga 1. Semakin besar nilainya maka antar fitur tersebut semakin mirip.

Dalam membangun model ini ada beberapa tahap. yaitu:
 1. Membuat matrik tfidf
    Matrix ini dibuat berdasarkan kolom genres. Setelah membuat matrix, kita mengubah vektor matriks ini menggunakan fungsi todense().
 2. Menghitung nilai *cosine similarity*
    Dengan fungsi *cosine_similarity*, dihitung nilai *cosine similarity* dari matriks tfidf yang telah dibut
 3. Membuat fungsi *anime_recomendation*
    Fungsi ini berguna untuk membandingkan nilai cosine similarity dari nama judul *anime* yang di masukkan dan mengembalikan default 5 rekomendasi teratas yang memiliki genres yang sejenis.
 4. Testing fungsi *anime_rcomendation*

    Untuk melihat hasil dari fungsi *anime_rcomendation*, diambil sample nama anime '*Taiko no Tatsujin*' yang
    bergenre '*Game*'. Setelah dicoba memanggil rekomendasi dengan memanggil fungsi *anime_recomendation*, mendapatkan hasil seperti berikut :

<center>

|Name|Genres|
|:---|:---:|
|Sword Art Online Fatal Bullet|Game|
|Future Card Buddyfight Battsu: All-Star Fight|Game|
|BIGOTRE Capture Mission|Game|
|Ekimemo!|Game|
|Paperman|Game|
|Treasure Gaust|Game|
|Battle Spirits: Burning Soul|Game|
|Future Card Buddyfight Battsu|Game|
|Oreca Battle|Game|
|Future Card Buddyfight|Game|

</center>

## Evaluation
Untuk evaluasi menggunakan metode precission dengan rumus dibawah ini :

$$ precission = { relevan recomendation \over showed recomendation} $$


Dari rumus diatas, dicobakan salah satu judul *anime* yang bergenre '*Game*', yaitu '*Taiko no Tatsujin*'. 

Dari *top recomendation* yang didapatkan, 10 dari 10 data yang ditampilkan mendapatkan judul anime yang bergenre '*Game*', Sehingga didapatkan hasil *precision* yaitu 10/10 = 1.0.

**---Terima Kasih---**

