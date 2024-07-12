**Filtering citra** dalam pengolahan citra digital adalah proses manipulasi atau transformasi citra untuk mengubah karakteristik visual dari citra tersebut. Tujuan utama dari filtering citra adalah untuk meningkatkan kualitas citra, menghilangkan gangguan atau noise, memperjelas fitur-fitur penting, atau menyesuaikan citra sesuai dengan kebutuhan aplikasi tertentu. Beberapa contoh filtering citra yang umum digunakan dalam pengolahan citra digital adalah Filtering Perataan (Smoothing Filters) yang dimana filter ini berfungsi untuk mengurangi noise atau gangguan pada citra.
Contoh: *Filter Gaussian, Filter Median, Filter Rata-rata*.

Berikut ini contoh penggunaan Filter Median, Filter Rata-rata dalam python:

import cv2  
import matplotlib.pyplot as plt  
import numpy as np

Secara umum, kode ini menunjukkan bahwa kita akan menggunakan library OpenCV untuk membaca dan memproses citra, dan library Matplotlib ini akan menampilkan citra, dan library NumPy untuk melakukan operasi numerik pada citra.

img = cv2.imread("leoni.jpg")  
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

Setelah menjalankan kedua baris kode ini, hasil dari pembacaan citra akan disimpan dalam variabel img dari file "leoni.jpg" dan dikonversi ke ruang warna RGB dengan code cv2.COLOR_BGR2RGB

### *Membuat Filter Median*
img_median = img.copy()  
img_median = cv2.cvtColor(img_median, cv2. COLOR_BGR2RGB)  
img_median_after=cv2.medianBlur(img_median,5)  
fig, axis = plt.subplots(1,2, figsize=(10,10))  
ax = axis.ravel()  
ax[0].imshow(img, cmap='gray')
ax[0].set_title('Gambar asli')
ax[1].imshow(img_median_after, cmap='gray')
ax[1].set_title('Gambar Filter Median')  
plt.show()

Kode ini membuat salinan citra asli,dengan  menerapkan filter median pada salinan tersebut.Filter median adalah salah satu jenis filtering perataan (smoothing) yang berfungsi untuk mengurangi noise pada citra. Parameter 5 ini  akan menentukan ukuran kernel filter median yang digunakan. Lalu Membuat subplot dengan 1 baris dan 2 kolom menggunakan Matplotlib.
Ukuran subplot diatur menjadi 10x10 inci dan kemudian menampilkan citra asli dan citra yang telah difilter dalam satu tampilan subplot menggunakan Matplotlib.

img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
copyImg1 = img.copy().astype(float)  
m1, n1 = copyImg1.shape  
output1 = np.empty([m1,n1])  
print("Shape copy citra 1    : ", copyImg1.shape)
print("Shape coutput citra 1 : ", output1.shape)  
print('m1 : ', m1)  
print('n1 : ', n1)

Dalam kode ini akan melakukan beberapa hal, yaitu:
1. Mengubah ruang warna citra img menjadi grayscale.
2. Membuat salinan citra img dengan tipe data float dan menyimpannya dalam variabel copyImg1. 
3. Mendapatkan dimensi (tinggi dan lebar) citra copyImg1 dan menyimpannya dalam variabel m1 dan n1.
4. Membuat array kosong dengan dimensi yang sama dengan copyImg1 dan menyimpannya dalam variabel output1.
5. Mencetak dimensi (tinggi dan lebar) dari copyImg1 dan output1, serta nilai m1 dan n1.

### *Membuat Filter Rata-rata*
for baris in range(0, m1-1):
    for kolom in range(0, n1-1):
        a1 = baris
        b1 = kolom 
        jumlah = copyImg1[a1-1,b1-1] + copyImg1[a1-1,b1+1] +\
        copyImg1[a1,b1-1] + copyImg1[a1,b1] + copyImg1[a1,b1+1] +\
        copyImg1[a1+1,b1-1] + copyImg1[a1+1,b1] + copyImg1[a1+1,b1+1]
        output1[a1, b1] = 1/9*jumlah

Kode ini menerapkan filter rata-rata (mean filter) pada citra copyImg1 dan menyimpan hasilnya dalam array output1. Filter rata-rata adalah salah satu jenis filtering perataan (smoothing) yang berfungsi untuk mengurangi noise pada citra. Proses ini dilakukan dengan mengiterasi setiap piksel dalam citra, menghitung nilai rata-rata dari 8 piksel tetangga, dan menyimpan hasil tersebut dalam array output1. kemudian hasil dari proses ini adalah citra yang telah dihaluskan (smoothed) menggunakan filter rata-rata

  fig, axis = plt.subplots(1,2, figsize=(10,10))  
  ax = axis.ravel()  
  ax[0].imshow(img, cmap='gray')
  ax[0].set_title('Original Image')
  ax[1].imshow(output1, cmap='gray')
  ax[1].set_title('Mean Filter Image')
  plt.show()**

Tujuan dari kode ini adalah untuk memvisualisasikan perbedaan antara citra asli dan citra yang telah diproses dengan filter rata-rata. Lalu terdapat ax = axis.ravel()yang berguna untuk mengubah array 2D axis menjadi array 1D ax agar dapat diakses secara lebih mudah.Hal ini dapat membantu dalam memahami efek dari filter rata-rata pada citra, seperti penghalusan (smoothing) dan pengurangan noise.Dengan melihat kedua subplot, kita dapat membandingkan dan menganalisis perbedaan antara citra asli dan citra yang telah difilter
