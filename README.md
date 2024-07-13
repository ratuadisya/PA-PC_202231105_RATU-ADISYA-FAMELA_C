  
# PENGOLAHAN CITRA DIGITAL 
## Filtering Citra pada gambar.
    RATU ADISYA FAMELA 
    202231105
    PROJECT UAS PENGOLAHAN CITRA DIGITAL C
# Penjelasan : 
 Kode yang saya tuliskan menggunakan pustaka OpenCV ([cv2]), NumPy (np), dan Matplotlib ([plt]) untuk memproses dan memvisualisasikan citra digital. Pada awalnya, pustaka-pustaka tersebut diimpor untuk memudahkan manipulasi gambar dan plot data. Gambar yang diinginkan dimuat menggunakan fungsi cv2.imread('[fotoratuu.jpg]'), yang mengembalikan gambar dalam bentuk array NumPy. Gambar ini kemudian disimpan dalam variabel img. Untuk menampilkan gambar asli, fungsi plt.imshow digunakan setelah mengonversi gambar dari format BGR (standar OpenCV) ke format RGB (standar yang digunakan oleh Matplotlib) menggunakan cv2.cvtColor(img, cv2.COLOR_BGR2RGB). Subplot pertama dari grid 2x2 dibuat menggunakan plt.subplot(2, 2, 1), dan judul "Citra Asli" ditambahkan dengan plt.title('Citra Asli').

Selanjutnya, gambar asli kembali ditampilkan di subplot kedua dengan judul "After Filter Median". Meskipun belum ada filter yang diterapkan, ini mungkin kesalahan kecil dalam kode. Konversi gambar dari format BGR ke grayscale dilakukan dengan cv2.cvtColor(img, cv2.COLOR_BGR2GRAY), dan hasilnya disimpan dalam variabel gray. Filter median diterapkan pada gambar grayscale menggunakan cv2.medianBlur(gray, 5), yang menggunakan kernel ukuran 5x5 untuk mereduksi noise pada gambar. Hasil dari proses ini disimpan dalam variabel median dan ditampilkan di subplot ketiga dengan judul "Original Image".

Untuk menerapkan filter rata-rata, kernel 5x5 didefinisikan dengan nilai yang sama (1/25) di setiap elemen menggunakan kernel = np.ones((5, 5), np.float32) / 25. Proses penerapan filter rata-rata dilakukan secara manual melalui fungsi mean_filter_manual(image, kernel), yang menerima gambar dan kernel sebagai input. Fungsi ini menambahkan padding pada gambar untuk menghindari masalah pada tepi gambar, dan kemudian menghitung nilai rata-rata untuk setiap piksel dengan menjumlahkan hasil perkalian elemen-elemen dalam kernel dan nilai piksel yang bersesuaian. Hasil dari proses ini disimpan dalam variabel mean.

Akhirnya, gambar yang telah difilter rata-rata ditampilkan di subplot keempat dengan judul "Mean Filtered Image". Semua subplot yang telah didefinisikan kemudian ditampilkan menggunakan plt.show(). Dengan demikian, kode ini memuat gambar asli, menampilkannya, mengonversinya ke grayscale, menerapkan filter median dan rata-rata, serta menampilkan hasil dari setiap langkah tersebut dalam subplot yang terorganisir dengan baik.

# Penjelasan query 
penjelasan untuk setiap bagian dari query (kode) yang digunakan dalam proses filtering citra:

### Baca Gambar
```python
image = cv2.imread('nanas.jpg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
- **`cv2.imread('nanas.jpg')`**: Membaca gambar dari file `'nanas.jpg'` menggunakan OpenCV.
- **`cv2.cvtColor(image, cv2.COLOR_BGR2RGB)`**: Mengonversi format warna gambar dari BGR (default OpenCV) ke RGB (untuk ditampilkan dengan benar di Matplotlib).

### Tampilkan Citra Asli
```python
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(image_rgb)
plt.title('Citra Asli')
```
- **`plt.figure(figsize=(15, 5))`**: Membuat figure baru dengan ukuran 15x5 inci.
- **`plt.subplot(1, 3, 1)`**: Menyiapkan subplot pertama dari tiga subplot dalam satu baris.
- **`plt.imshow(image_rgb)`**: Menampilkan gambar asli dalam format RGB.
- **`plt.title('Citra Asli')`**: Memberi judul pada subplot sebagai "Citra Asli".

### Median Filtering
```python
median_filtered = cv2.medianBlur(image, 5)
median_filtered_rgb = cv2.cvtColor(median_filtered, cv2.COLOR_BGR2RGB)

plt.subplot(1, 3, 2)
plt.imshow(median_filtered_rgb)
plt.title('Median Filtering')
```
- **`cv2.medianBlur(image, 5)`**: Menerapkan median filtering dengan kernel ukuran 5 pada gambar.
- **`cv2.cvtColor(median_filtered, cv2.COLOR_BGR2RGB)`**: Mengonversi gambar yang telah difilter dari BGR ke RGB.
- **`plt.subplot(1, 3, 2)`**: Menyiapkan subplot kedua dari tiga subplot dalam satu baris.
- **`plt.imshow(median_filtered_rgb)`**: Menampilkan gambar hasil median filtering dalam format RGB.
- **`plt.title('Median Filtering')`**: Memberi judul pada subplot sebagai "Median Filtering".

### Mean Filtering (Manual)
#### Definisi Fungsi Mean Filtering
```python
def mean_filtering(image, kernel_size=3):
    kernel = np.ones((kernel_size, kernel_size), np.float32) / (kernel_size**2)
    mean_filtered = cv2.filter2D(image, -1, kernel)
    return mean_filtered
```
- **`def mean_filtering(image, kernel_size=3):`**: Mendefinisikan fungsi `mean_filtering` dengan parameter `image` dan `kernel_size` (default 3).
- **`kernel = np.ones((kernel_size, kernel_size), np.float32) / (kernel_size**2)`**: Membuat kernel (matriks) berukuran `kernel_size x kernel_size` yang diisi dengan nilai rata-rata (1/9 untuk ukuran 3x3).
- **`mean_filtered = cv2.filter2D(image, -1, kernel)`**: Menerapkan konvolusi 2D dengan kernel pada gambar.
- **`return mean_filtered`**: Mengembalikan gambar yang telah difilter.

#### Menggunakan Fungsi Mean Filtering
```python
mean_filtered = mean_filtering(image, 3)
mean_filtered_rgb = cv2.cvtColor(mean_filtered, cv2.COLOR_BGR2RGB)

plt.subplot(1, 3, 3)
plt.imshow(mean_filtered_rgb)
plt.title('Mean Filtering (Manual)')
```
- **`mean_filtered = mean_filtering(image, 3)`**: Menerapkan fungsi `mean_filtering` pada gambar dengan kernel ukuran 3x3.
- **`cv2.cvtColor(mean_filtered, cv2.COLOR_BGR2RGB)`**: Mengonversi gambar yang telah difilter dari BGR ke RGB.
- **`plt.subplot(1, 3, 3)`**: Menyiapkan subplot ketiga dari tiga subplot dalam satu baris.
- **`plt.imshow(mean_filtered_rgb)`**: Menampilkan gambar hasil mean filtering dalam format RGB.
- **`plt.title('Mean Filtering (Manual)')`**: Memberi judul pada subplot sebagai "Mean Filtering (Manual)".

### Menampilkan Semua Subplot
```python
plt.tight_layout()
plt.show()
```
- **`plt.tight_layout()`**: Menyusun layout subplot agar tidak tumpang tindih dan terlihat rapi.
- **`plt.show()`**: Menampilkan semua subplot dalam satu figure.


# Kesimpulan
1. **Citra Asli**: Menampilkan gambar asli.
2. **Median Filtering**: Menggunakan median filter untuk menghaluskan gambar dengan mengurangi noise.
3. **Mean Filtering (Manual)**: Menggunakan mean filter (rata-rata) untuk menghaluskan gambar dengan mengurangi noise secara manual.
Atau pun Kode ini memberikan demonstrasi dasar mengenai bagaimana gambar dapat diproses menggunakan berbagai teknik filtering. Filter median efektif untuk mengurangi noise pada gambar tanpa memberi filter buram pada tepi, sementara filter rata-rata memberikan efek penghalusan yang lebih umum namun dapat memberi filter buram secara detail. Melalui penggunaan OpenCV dan NumPy untuk manipulasi citra dan Matplotlib untuk visualisasi, kode ini menunjukkan bagaimana teknik-teknik ini dapat diterapkan untuk meningkatkan kualitas gambar.
