 
# PENGOLAHAN CITRA DIGITAL 
## Filtering Citra pada gambar.
    RATU ADISYA FAMELA 
    202231105
    PROJECT UAS PENGOLAHAN CITRA DIGITAL C
# Penjelasan : 
penjelasan yang dapat saya tarik dari coodingan yang saya tuliskan yaitu, kode yang saya tampilkan menggunakan pustaka OpenCV (`cv2`), NumPy (`np`), dan Matplotlib (`plt`) untuk memproses dan memvisualisasikan citra digital. Pertama, pustaka-pustaka tersebut diimpor untuk memudahkan manipulasi gambar dan plot data. Gambar yang diinginkan dimuat menggunakan fungsi `cv2.imread('fotoratuu.jpg')`, yang mengembalikan gambar dalam bentuk array NumPy. Gambar ini kemudian disimpan dalam variabel `img`. Untuk menampilkan gambar asli, fungsi `plt.imshow` digunakan setelah mengonversi gambar dari format BGR (standar OpenCV) ke format RGB (standar yang digunakan oleh Matplotlib) menggunakan `cv2.cvtColor(img, cv2.COLOR_BGR2RGB)`. Subplot pertama dari grid 2x2 dibuat menggunakan `plt.subplot(2, 2, 1)`, dan judul "Citra Asli" ditambahkan dengan `plt.title('Citra Asli')`.

Selanjutnya, gambar asli kembali ditampilkan di subplot kedua dengan judul "After Filter Median". Meskipun belum ada filter yang diterapkan, ini mungkin kesalahan kecil dalam kode. Konversi gambar dari format BGR ke grayscale dilakukan dengan `cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)`, dan hasilnya disimpan dalam variabel `gray`. Filter median diterapkan pada gambar grayscale menggunakan `cv2.medianBlur(gray, 5)`, yang menggunakan kernel ukuran 5x5 untuk mereduksi noise pada gambar. Hasil dari proses ini disimpan dalam variabel `median` dan ditampilkan di subplot ketiga dengan judul "Original Image".

Untuk menerapkan filter rata-rata, kernel 5x5 didefinisikan dengan nilai yang sama (1/25) di setiap elemen menggunakan `kernel = np.ones((5, 5), np.float32) / 25`. Proses penerapan filter rata-rata dilakukan secara manual melalui fungsi `mean_filter_manual(image, kernel)`, yang menerima gambar dan kernel sebagai input. Fungsi ini menambahkan padding pada gambar untuk menghindari masalah pada tepi gambar, dan kemudian menghitung nilai rata-rata untuk setiap piksel dengan menjumlahkan hasil perkalian elemen-elemen dalam kernel dan nilai piksel yang bersesuaian. Hasil dari proses ini disimpan dalam variabel `mean`.

Akhirnya, gambar yang telah difilter rata-rata ditampilkan di subplot keempat dengan judul "Mean Filtered Image". Semua subplot yang telah didefinisikan kemudian ditampilkan menggunakan `plt.show()`. Dengan demikian, kode ini memuat gambar asli, menampilkannya, mengonversinya ke grayscale, menerapkan filter median dan rata-rata, serta menampilkan hasil dari setiap langkah tersebut dalam subplot yang terorganisir dengan baik.

### Kesimpulan
Kode ini memberikan demonstrasi dasar mengenai bagaimana gambar dapat diproses menggunakan berbagai teknik filtering. Filter median efektif untuk mengurangi noise pada gambar tanpa memberi filter buram pada tepi, sementara filter rata-rata memberikan efek penghalusan yang lebih umum namun dapat memberi filter buram secara  detail. Melalui penggunaan OpenCV dan NumPy untuk manipulasi citra dan Matplotlib untuk visualisasi, kode ini menunjukkan bagaimana teknik-teknik ini dapat diterapkan untuk meningkatkan kualitas gambar.
