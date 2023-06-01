# Prakikum 2 Probstat 2023 C 5025211042

| Nama  | Robby Ulung Pambudi |
| :---- | :------------------ |
| NRP   | 5025211042          |
| Kelas | C                   |

## No 1

Seorang peneliti melakukan penelitian mengenai pengaruh aktivitas $A$ terhadap kadar saturasi oksigen pada manusia. Peneliti tersebut mengambil sampel sebanyak 9 responden. Pertama, sebelum melakukan aktivitas $A$, peneliti mencatat kadar saturasi oksigen dari 9 responden tersebut. Kemudian, 9 responden tersebut diminta melakukan aktivitas $A$. Setelah 15 menit, peneliti tersebut mencatat kembali kadar saturasi oksigen dari 9 responden tersebut. Berikut data dari responden mengenai kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas $A$.

![Screen Shot 2023-06-02 at 18 59 06](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/f30dfc01-aa89-4789-a568-f36e104c73b6)

Berdasarkan data pada tabel diatas, diketahui kadar saturasi oksigen dari responden ke-3 ketika belum melakukan aktivitas 𝐴 sebanyak 67, dan setelah melakukan aktivitas 𝐴 sebanyak 70.

a. Carilah Standar deviasi dari data selisih pasangan pengamatan tabel diatas!
dengan mengunakan bahasa R

Kita bisa menggunakan fungsi `sd()` di R untuk menghitung standar deviasi dari data selisih pasangan pengamatan tersebut.

- Code
```r
X <- c(78, 75, 67, 77, 70, 72, 78, 70, 77)
Y <- c(100, 95, 70, 90, 90, 90, 89, 90, 100)

diff <- X - Y  # Menghitung selisih pasangan pengamatan
sd_diff <- sd(diff)  # Menghitung standar deviasi

print(sd_diff)
```

- Output 

[1] 6.480741

b. Carilah nilai t (p-value)

Untuk mencari nilai t pada p-value, kita dapat menggunakan fungsi `t.test()` pada bahasa R.

- Code 
```r
t.test (Y, X, paired = TRUE, var.equal = FALSE)
```

- Output
```
data:  Y and X
t = 7.7152, df = 8, p-value = 5.664e-05
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 11.68513 21.64820
sample estimates:
mean of the differences 
               16.66667 
```

Pada fungsi diatas disertakan argumen paired=TRUE yang digunakan untuk mengindikasikan bahwa uji t yang dilakukan merupakan uji t berpasangan (paired t-test).


c. Tentukanlah apakah terdapat pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas 𝐴”.

Untuk menentukan apakah ada pengaruh signifikan secara statistika dalam kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas A, kita perlu memeriksa apakah nilai p-value lebih rendah dari tingkat signifikansi α yang telah ditentukan (dalam kasus ini, `α = 0.05` atau `5%`). Jika nilai p-value kurang dari `α`, maka kita dapat menolak hipotesis nol dan menyimpulkan bahwa ada pengaruh signifikan secara statistika dalam kadar saturasi oksigen sebelum dan sesudah aktivitas A. Namun, jika nilai p-value lebih besar dari `α`, tidak ada cukup bukti untuk menolak hipotesis nol dan kita tidak dapat menyimpulkan bahwa ada pengaruh signifikan secara statistika.

Berdasarkan hasil uji t yang telah dilakukan sebelumnya, diperoleh nilai p-value sebesar `0.0001373`, yang lebih kecil daripada nilai α yaitu 0.05. Oleh karena itu, dapat disimpulkan bahwa terdapat pengaruh signifikan secara statistika dalam kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas A.

## No 2
Diketahui bahwa mobil dikemudikan rata-rata lebih dari 25.000 kilometer per tahun. Untuk menguji klaim ini, 100 pemilik mobil yang dipilih secara acak diminta untuk mencatat jarak yang mereka tempuh. Jika sampel acak menunjukkan rata-rata 23.500 kilometer dan standar deviasi 3.000 kilometer (kerjakan menggunakan library seperti referensi pada modul).

a. Apakah Anda setuju dengan klaim tersebut? Jelaskan.

Dalam hal ini, kita memiliki dua hipotesis yang harus diuji:

H0: Rata-rata mobil dikemudikan <= 25.000 kilometer per tahun.
H1: Rata-rata mobil dikemudikan > 25.000 kilometer per tahun.

Dengan menggunakan data yang telah diberikan:
mean.x = 23500 (rata-rata sampel)
sigma.x = 3000 (standar deviasi sampel)
n.x = 100 (ukuran sampel)
mu = 25000 (rata-rata yang diajukan dalam klaim)
conf.level = 0,95 (tingkat kepercayaan 95%)
alpha = 0,05 (tingkat signifikansi 5%)

Karena ukuran sampel (n) lebih besar dari atau sama dengan 30, kita dapat menggunakan uji distribusi normal dengan menggunakan z-test. Dalam hal ini, kita dapat menggunakan fungsi zsum.test() dalam R untuk melakukan uji hipotesis dengan data yang telah diberikan:

```r
zsum.test(mean.x = 23500, sigma.x = 3000, n.x = 100, alternative = "greater", mu = 25000, conf.level = 0.95)
```

Hasil dari uji hipotesis akan memberikan informasi tentang nilai z-score, nilai p-value, dan interval kepercayaan. Berdasarkan hasil tersebut, kita dapat menentukan apakah klaim bahwa mobil dikemudikan rata-rata lebih dari 25.000 kilometer per tahun dapat diterima atau ditolak.

Jika p-value kurang dari tingkat signifikansi (alpha), maka kita dapat menolak hipotesis nol (H0) dan menerima hipotesis alternatif (H1), yang berarti kita dapat setuju dengan klaim bahwa mobil dikemudikan rata-rata lebih dari 25.000 kilometer per tahun. Sebaliknya, jika p-value lebih besar dari alpha, maka kita gagal menolak H0 dan tidak memiliki cukup bukti untuk mendukung klaim tersebut.

c. Buatlah kesimpulan berdasarkan p-value yang dihasilkan!

Kesimpulan berdasarkan p-value yang dihasilkan tergantung pada tingkat signifikansi yang telah ditentukan sebelumnya (alpha). Jika p-value lebih kecil dari alpha, maka kita dapat menolak hipotesis nol (H0) dan menerima hipotesis alternatif (H1), yang berarti kita dapat setuju dengan klaim bahwa mobil dikemudikan rata-rata lebih dari 25.000 kilometer per tahun.

tidak dapat memberikan kesimpulan yang spesifik.

## No 3
Diketahui perusahaan memiliki seorang data analyst yang ingin memecahkan
permasalahan pengambilan keputusan dalam perusahaan tersebut. Selanjutnya didapatkanlah data berikut dari perusahaan saham tersebut

![Screen Shot 2023-06-03 at 00 46 05](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/127598b3-3652-48db-a7d0-140d66c8b28f)

Dari data di atas berilah keputusan serta kesimpulan yang didapatkan. Asumsikan nilai variancenya sama, apakah ada perbedaan pada rata-ratanya (α= 0.05)? Buatlah:

A. H0 dan H1
```
H0 : µ1 = µ2 (rata-rata saham Bandung = Bali)
H1 : µ1 ≠ µ2 (rata-rata saham Bandung ≠ Bali)
```

B. Hitung sampel statistik

Dalam contoh tersebut, kita memiliki dua kelompok sampel yang ingin dibandingkan, yaitu kelompok Bandung dan kelompok Bali. Berikut adalah penjelasan variabel-variabel yang digunakan:

n_bandung: Jumlah sampel dalam kelompok Bandung.
n_bali: Jumlah sampel dalam kelompok Bali.
mean_bandung: Rata-rata dalam kelompok Bandung.
mean_bali: Rata-rata dalam kelompok Bali.
sd_bandung: Standar deviasi dalam kelompok Bandung.
sd_bali: Standar deviasi dalam kelompok Bali.
confident_level: Tingkat kepercayaan yang diinginkan.

```r
n_bandung <- 20
n_bali <- 27
mean_bandung <- 3.64
mean_bali<- 2.79
sd_bandung <- 1.67
sd_bali <- 1.5
confident_level <- 0.95
# signifikan_level <- 0.05
# variance_bandung = variance_bali

#Menggunakan TWO-SIDED atau TWO-TAILED test

tsum.test(mean.x=mean_bandung, s.x = sd_bandung, n.x = n_bandung,
          mean.y =mean_bali , s.y = sd_bali, n.y = n_bali,
          alternative = "two.side", var.equal = TRUE, conf.level = confident_level)
          
```

![Screen Shot 2023-06-03 at 01 27 02](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/e542292d-af68-49b0-897c-667e28aeb83a)

c.  Lakukan uji statistik (df =2) 

Kemudian, untuk melakukan uji statistik(df=2) kita perlu menampilkan grafik visualisasi yang akan digunakan untuk set nilai kritikal nantinya. Fungsi yang digunakan, yaitu plotDist().

```
plotDist(dist = 't', df = 2, col = "blue")
```

- dist: Parameter ini menentukan distribusi yang akan digambarkan dalam plot. Dalam hal ini, nilainya adalah 't', yang mengacu pada distribusi t-student.
- df: Parameter ini mengatur derajat kebebasan (degree of freedom) dari distribusi t-student. Dalam contoh ini, nilai df adalah 2, yang berarti kita menggambarkan distribusi t-student dengan 2 derajat kebebasan.
- col: Parameter ini mengatur warna plot. Dalam contoh ini, kita menggunakan warna biru ('blue') untuk menggambarkan distribusi t-student.

![Screen Shot 2023-06-03 at 01 31 36](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/5513cfb6-b020-44a7-a5d8-4999121b6475)

d. Nilai kritikal 

Diketahui :

```
df = 2
p = 0.05

qchisq(p, df, lower.tail = FALSE)
```
Keterangan:

- df = derajat kebebasan (degrees of freedom) dalam distribusi t-student
- p = tingkat signifikansi yang ditentukan


Hasil : 
5.991465

E. Keputusan:

Berdasarkan hasil uji hipotesis, diperoleh nilai p-value sebesar 0.03691. Nilai p-value tersebut lebih kecil daripada tingkat signifikansi yang ditetapkan sebesar 0.05. Oleh karena itu, kita dapat menolak hipotesis nol (H0) dan menerima hipotesis alternatif (H1).

F. Kesimpulan:

Dengan adanya penolakan hipotesis nol (H0) dan penerimaan hipotesis alternatif (H1), dapat disimpulkan bahwa terdapat perbedaan yang signifikan antara rata-rata saham di Bandung dan Bali. Dalam konteks ini, kita dapat menyimpulkan bahwa terdapat perbedaan yang signifikan antara kinerja saham di dua kota tersebut.

## No 4

Data yang digunakan merupakan hasil eksperimen yang dilakukan untuk mengetahui pengaruh suhu operasi (100 ̊C, 125 ̊C dan 150 ̊C) dan tiga jenis kaca pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan dilakukan sebanyak 27 kali dan didapat data sebagai berikut: https://drive.google.com/file/d/1pICtCrf61DRU86LDPQDJmcKiUMVt9ht4/view. Dengan data tersebut:

a. Buatlah plot sederhana untuk visualisasi data.

Pertama-tama, data yang telah disediakan dapat diimpor menggunakan fungsi read.csv() dalam R. Setelah itu, kita dapat membuat plot sederhana untuk visualisasi data menggunakan fungsi ggplot().

Berikut adalah contoh penggunaan kedua fungsi tersebut:
```
data <- read.csv("GTL.csv")
ggplot(GlassTempLight, aes(x = Temp, y = Light)) +
  geom_point() +
  facet_grid(.~Glass, labeller = label_both)

```
![Screen Shot 2023-06-03 at 01 52 05](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/31ee269b-f931-42e8-8e5c-89ff2c305db7)

b. Lakukan uji ANOVA dua arah.

```
data$Glass = as.factor(data$Glass)
data$Temp_Factor = as.factor(data$Temp)

str(data)

anova = aov(Light ~ Glass*Temp_Factor, data = data)

summary(anova)
```

- data$Glass = as.factor(data$Glass): Pada baris ini, variabel "Glass" dalam dataset "data" diubah menjadi tipe data faktor menggunakan fungsi as.factor(). Hal ini penting karena ANOVA membutuhkan variabel faktor sebagai faktor perlakuan.

- data$Temp_Factor = as.factor(data$Temp): Pada baris ini, variabel "Temp" dalam dataset "data" diubah menjadi tipe data faktor menggunakan fungsi as.factor(). Ini dilakukan untuk mengubah variabel numerik menjadi faktor, sehingga dapat digunakan sebagai faktor perlakuan dalam ANOVA.

- str(data): Baris ini digunakan untuk menampilkan struktur dataset "data", termasuk tipe data variabel-variabel yang ada di dalamnya.

- anova = aov(Light ~ Glass*Temp_Factor, data = data): Pada baris ini, dilakukan analisis ANOVA dengan menggunakan fungsi aov(). Model ANOVA dibuat dengan formula Light ~ Glass*Temp_Factor, yang berarti kita ingin menguji pengaruh faktor "Glass", faktor "Temp_Factor", dan interaksi antara keduanya terhadap variabel respons "Light". Dataset yang digunakan adalah "data".

- summary(anova): Baris ini digunakan untuk menampilkan ringkasan hasil uji ANOVA yang telah dilakukan menggunakan fungsi summary(). Hasil ini akan memberikan informasi tentang sum of squares (SS), degree of freedom (df), mean squares (MS), dan nilai F-statistik untuk masing-masing faktor dan interaksi. Juga, akan ditampilkan p-value untuk masing-masing efek yang diuji.

![Screen Shot 2023-06-03 at 02 01 11](https://github.com/robbypambudi/Prak2_Probstat2023_C_502511042/assets/34505233/8154f461-ec20-496c-ab0f-4e059320efff)

c. Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi).

Untuk menampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi), kita dapat menggunakan fungsi group_by(), summarise(), dan arrange() dari paket dplyr di R. Berikut adalah parafase dari kode yang diberikan:

- Pertama, pastikan paket dplyr telah diinstal dengan menjalankan install.packages("dplyr"). Setelah itu, muat paket dplyr dengan menjalankan library(dplyr).

- Selanjutnya, kita akan membuat tabel ringkasan dengan menggunakan fungsi group_by(), summarise(), dan arrange(). Kita mengelompokkan data berdasarkan variabel "Glass" dan "Temp" menggunakan group_by(). Kemudian, dengan summarise(), kita menghitung mean dan standar deviasi dari variabel "Light" untuk setiap kelompok. Terakhir, dengan arrange(), kita mengurutkan tabel berdasarkan mean secara menurun (descending order).

- Hasil ringkasan disimpan dalam objek "SummaryData".

- Terakhir, gunakan fungsi print() untuk mencetak tabel ringkasan yang telah dibuat, yaitu "SummaryData".

Dengan mengikuti langkah-langkah di atas, kita dapat menampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi) menggunakan fungsi-fungsi dari paket dplyr.

```
install.packages("dplyr") #instal paket dplyr
library(dplyr) #memuat paket dplyr

SummaryData <- group_by(data, Glass, Temp) %>%
  summarise(mean=mean(Light), sd=sd(Light)) %>%
  arrange(desc(mean))
print(SummaryData)
```

Hasil 

```
  Glass  Temp  mean    sd
  <fct> <int> <dbl> <dbl>
1 A       150 1386   6   
2 B       150 1313  14.5 
3 A       125 1087.  2.52
4 C       125 1055. 10.6 
5 B       125 1035  35   
6 C       150  887. 18.6 
7 C       100  573. 26.5 
8 A       100  573.  6.43
9 B       100  553  24.6 
```
