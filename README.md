**Tutorial Pemrograman Lanjut (Advanced Programming) 2024/2025 Genap**
* Nama    : Muhammad Almerazka Yocendra
* NPM     : 2306241745
* Kelas   : Pemrograman Lanjut - A

<details>
    <summary><strong> Reflection 💡 </strong></summary>
  
### Perbedaan JMeter dan Intellij Profiler
Perbedaan pendekatan antara pengujian performa dengan **JMeter** dan **profiling** dengan **IntelliJ Profiler** dalam optimasi aplikasi terletak pada fokus dan tujuan masing-masing alat.
- **JMeter** digunakan untuk mengukur performa aplikasi dengan mensimulasikan banyak pengguna yang mengakses sistem secara bersamaan. Pengujian ini membantu mengevaluasi _latency_, _response time_, _throughput_, serta kemampuan aplikasi dalam menangani beban kerja tinggi. Jadi 
-  Sementara itu, **IntelliJ Profiler** berfungsi untuk menganalisis proses internal aplikasi guna mengidentifikasi _bottleneck_ yang menyebabkan penurunan performa menjadi lebih lambat, seperti penggunaan CPU, alokasi memori, dan waktu eksekusi metode.
  
Jadi intinya  **JMeter** memberikan gambaran umum mengenai performa sistem di bawah tekanan/beban kerja tinggi dan mengukur dampak perubahan, sedangkan **IntelliJ Profiler** memberikan wawasan mendalam terkait efisiensi kode seperti membantu menemukan serta memperbaiki bagian kode yang memperlambat aplikasi.

### Peran Profiling dalam Mengidentifikasi Kelemahan Aplikasi
**Profiling** sendiri memainkan peran penting dalam mengidentifikasi dan memahami titik lemah dalam aplikasi dengan menganalisis penggunaan CPU, memori, dan eksekusi kode. Proses ini membantu kita untuk menemukan _bottleneck_ yang menyebabkan aplikasi berjalan lambat, seperti algoritma yang tidak efisien, operasi yang berlebihan, atau kebocoran memori. Dengan _profiling_, saya bisa melihat fungsi mana yang memakan banyak sumber daya, bagaimana _garbage collection_ bekerja, serta bagaimana _thread_ dan proses berjalan secara bersamaan. Intinya, dengan _profiling_, kita bisa melakukan perbaikan performa aplikasi dengan cara yang lebih akurat, bukan cuma sekadar coba-coba.

### Efektivitas IntelliJ Profiler
Menurut saya, **IntelliJ Profiler** sangat efektif dalam membantu menganalisis dan mengidentifikasi _bottleneck_ dalam kode aplikasi. Dengan alat ini, saya bisa melihat penggunaan CPU, alokasi memori, serta waktu eksekusi setiap metode, sehingga lebih mudah menemukan bagian kode yang menyebabkan perlambatan. Fitur _flame graph_ membantu memahami jalur eksekusi kode, sementara _Method List_ memberikan gambaran rinci performa metode. Selain itu, perbandingan sebelum dan sesudah optimasi memudahkan evaluasi tanpa perhitungan manual. Dengan visualisasi yang jelas, optimasi dapat dilakukan lebih terarah dan efisien.

### Tantangan dalam Pengujian Kinerja dan Profiling
Tantangan utama dalam melakukan _performance testing_ dan _profiling_  adalah memahami dan menganalisis hasil yang diperoleh dengan tepat. Data yang dihasilkan sering kali kompleks, sehingga memerlukan interpretasi yang cermat untuk menemukan _bottleneck_ dalam aplikasi. Selain itu, setelah menemukan masalah, tantangan berikutnya adalah melakukan optimasi yang efektif tanpa mengorbankan fungsionalitas aplikasi. Saya mengatasi hal ini dengan membandingkan hasil sebelum dan sesudah optimasi, menerapkan _refactoring_ yang tepat, serta menjalankan pengujian berulang di lingkungan yang konsisten agar hasilnya lebih akurat dan perbaikan lebih efektif.

### Manfaat IntelliJ Profiler
Salah satu keuntungan utama menggunakan **IntelliJ Profiler** adalah kemudahannya karena sudah terintegrasi langsung dalam **IntelliJ IDEA**, sehingga saya tidak perlu menggunakan aplikasi pihak ketiga atau melakukan konfigurasi tambahan yang rumit. Selain itu, profiler ini memberikan analisis mendalam tentang penggunaan CPU, alokasi memori, dan eksekusi metode, yang membantu saya dalam mengidentifikasi dan memperbaiki _bottleneck_ dengan lebih cepat. Dengan tampilan visual yang intuitif dan integrasi langsung ke dalam IDE, proses analisis, debugging, dan optimasi performa dapat dilakukan dengan lebih cepat dan efektif.

### Inkonsistensi IntelliJ Profiler dan JMeter
Jika hasil dari **IntelliJ Profiler** dan **JMeter** tidak sepenuhnya konsisten, saya akan mengevaluasi kembali skenario pengujian, memastikan bahwa beban kerja, lingkungan, dan parameter uji yang digunakan sesuai. Saya juga akan membandingkan metrik dari kedua alat untuk mengidentifikasi faktor yang menyebabkan perbedaan, seperti latensi jaringan, keterbatasan database, atau proses latar belakang yang memengaruhi performa. Jika ketidakkonsistenan masih terjadi, saya mungkin akan menjalankan ulang pengujian dalam kondisi yang lebih terkontrol dan mencari referensi atau berdiskusi dengan rekan untuk mendapatkan perspektif tambahan dalam analisisnya.

### Strategi Optimisasi Kode Aplikasi
Setelah menganalisis hasil _performance testing_ dan _profiling_, saya menerapkan beberapa strategi optimasi, seperti:

**1. Optimasi Algoritma dan Struktur Data**

Saya mengidentifikasi bagian kode yang tidak efisien dan menggantinya dengan algoritma yang lebih optimal atau menggunakan struktur data yang lebih sesuai untuk meningkatkan kinerja.

**2. Mengurangi Pemanggilan Fungsi yang Tidak Perlu**

Saya mengevaluasi kembali pemanggilan fungsi yang berulang atau tidak diperlukan untuk mengurangi overhead eksekusi.

**3. Optimasi Penggunaan Memori**

Saya mengurangi alokasi memori yang berlebihan, menghindari kebocoran memori (_memory leaks_), serta memanfaatkan object pooling jika diperlukan.

**4. Parallel Processing dan Caching**

Untuk meningkatkan kecepatan eksekusi, saya menerapkan teknik _multithreading_ atau _asynchronous processing_ jika memungkinkan. Saya juga menggunakan _caching_ untuk mengurangi akses ke _database_ atau operasi mahal lainnya.

### Contoh dalam kode saya
**1. Mengurangi Redundansi Query Database** – Saya mengganti _query_ yang tidak efisien dengan _batch processing_ atau _lazy loading_ untuk mengurangi beban _database_.
```java
public Optional<Student> findStudentWithHighestGpa() {
    List<Student> students = studentRepository.findAll();
    Student highestGpaStudent = null;
    ....
```
Sebelumnya saya mengambil semua data mahasiswa dan melakukan iterasi manual untuk menemukan mahasiswa dengan GPA tertinggi. Namun hal ini kurang efisien sehingga saya menggunakan metode `findTopByOrderByGpaDesc()` langsung dari _repository_ untuk mengambil mahasiswa dengan GPA tertinggi tanpa perlu memuat semua data ke memori.
```java
public Optional<Student> findStudentWithHighestGpa() {
    return studentRepository.findTopByOrderByGpaDesc();
}
```

**2. Optimasi Memory Usage dengan StringBuilder** – Saya meminimalkan penggunaan objek yang tidak perlu dan menggunakan _StringBuilder_ daripada _String_ saat menggabungkan teks dalam loop.
```java
public String joinStudentNames() {
    List<Student> students = studentRepository.findAll();
    String result = "";
    ....
}
```
Pada metode `joinStudentNames()`, string _concatenation_ dilakukan menggunakan + di dalam _loop_. Setiap kali `result += student.getName()`, objek _String_ baru dibuat karena _String_ bersifat _immutable_. Hal ini menyebabkan konsumsi memori tinggi dan menurunkan performa sehingga saya menggunakan _StringBuilder_ untuk menghindari pembuatan objek String yang berulang.
```java
public String joinStudentNames() {
    List<Student> students = studentRepository.findAll();
    StringBuilder result = new StringBuilder();
    ....
}
```

**3.  Menghindari Looping Berlebihan**

Pada metode `getAllStudentsWithCourses()`, dilakukan _looping_ untuk mengambil data mahasiswa dan kemudian _looping_ lagi untuk mengambil daftar kursus dari setiap mahasiswa sehingga berdampak buruk pada performa. Saya disini menggunakan `findAll()` langsung dari _studentCourseRepository_ untuk menghindari _looping_ manual.
```java
public List<StudentCourse> getAllStudentsWithCourses() {
    return studentCourseRepository.findAll();
}
```
</details>

<details> 
  <summary><strong> JMeter Report and Test Results 📊 </strong></summary>
  
### Endpoint /all-student

#### Before Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-13 222625](https://github.com/user-attachments/assets/eba6797c-649a-4dac-b308-d0a6d37277cd)
**[JTL]** 
![Screenshot 2025-03-13 223207](https://github.com/user-attachments/assets/068cad46-1490-4fe6-8e11-8399680efcac)

#### After Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-14 095351](https://github.com/user-attachments/assets/f5530be7-063b-421f-ac90-cf08000636c2)
**[JTL]** 
![Screenshot 2025-03-14 095908](https://github.com/user-attachments/assets/f7f06610-9cb8-4351-be40-03390313f464)

| Metric | Before | After  | Diff Percentage |
|-----------|--------|--------| -- |
| **Waktu respons rata-rata (elapsed)** | 52,768 ms | 3,739 ms | 92,91% |
| **Latency** | 52,755 ms | 3,720 ms | 92,94% |

### Endpoint /all-student-names

#### Before Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-13 221049](https://github.com/user-attachments/assets/1cc4572a-b894-4932-aff1-1ef97822f6a3)
**[JTL]** 
![Screenshot 2025-03-13 221817](https://github.com/user-attachments/assets/3cd6b6da-575e-45ac-8677-2398e29157ca)

#### After Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-14 102901](https://github.com/user-attachments/assets/29e288b3-ff7a-4379-8657-fc2835fa2ed3)
**[JTL]** 
![Screenshot 2025-03-14 102935](https://github.com/user-attachments/assets/bc04be39-b341-4967-b4ab-38cbf254940a)

| Metric | Before | After  | Diff Percentage |
|-----------|--------|--------| -- |
| **Waktu respons rata-rata (elapsed)** | 2,091 ms | 65,9 ms | 96,85% |
| **Latency** | 2,088 ms | 64,3 ms | 96,92% |

### Endpoint /highest-gpa
#### Before Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-13 221259](https://github.com/user-attachments/assets/337f6be0-ebed-4d19-97ea-87d0d58a2291)
**[JTL]** 
![Screenshot 2025-03-13 221348](https://github.com/user-attachments/assets/37d5bcd2-9069-4bd8-a52f-c66e9d00b2e7)

#### After Optimization JMeter :
**[GUI]** 
![Screenshot 2025-03-14 103851](https://github.com/user-attachments/assets/62c64dab-cb65-48e2-aaaa-16c1df0db656)
**[JTL]** 
![Screenshot 2025-03-14 103946](https://github.com/user-attachments/assets/c25283cb-c9a0-4310-a21e-9700eb15e14b)

| Metric | Before | After  | Diff Percentage |
|-----------|--------|--------| -- |
| **Waktu respons rata-rata (elapsed)** | 101,3 ms | 9,9 ms | 90,23% |
| **Latency** | 100,7 ms | 9,3 ms | 90,76% |

</details>

<details>
<summary><strong> Conclusion ✅ </strong></summary>
    
> Berdasarkan hasil pengujian menggunakan **JMeter**, terlihat bahwa optimasi yang dilakukan pada kode aplikasi memberikan peningkatan signifikan dalam performa, terutama dalam hal waktu _response_ dan _latency_.

> **1. Endpoint /all-student**
> - Waktu _response_ rata-rata berkurang dari 52.768 ms menjadi 3.739 ms (92,91% lebih cepat).
> - _Latency_ berkurang dari 52.755 ms menjadi 3.720 ms (92,94% lebih cepat).
    
> **2. Endpoint /all-student-names**
> - Waktu _response_ rata-rata berkurang dari 2.091 ms menjadi 65,9 ms (96,85% lebih cepat).
> - _Latency_ berkurang dari 2.088 ms menjadi 64,3 ms (96,92% lebih cepat).
    
> **3. Endpoint /highest-gpa**
> - Waktu _response_ rata-rata berkurang dari 101,3 ms menjadi 9,9 ms (90,23% lebih cepat).
> - _Latency_ berkurang dari 100,7 ms menjadi 9,3 ms (90,76% lebih cepat).

> Sehingga optimasi yang saya lakukan berhasil mengurangi beban dan meningkatkan efisiensi kode, terutama dengan penggunaan _query database_ yang lebih optimal, yang berdampak besar dalam mengurangi waktu _response_. Selain itu, penerapan _StringBuilder_ dan _query_ langsung pada _repository_ turut berkontribusi dalam peningkatan kinerja. Perubahan ini tidak hanya membuat proses lebih cepat, tetapi juga mengurangi konsumsi sumber daya server, sehingga aplikasi menjadi lebih efisien dan _scalable_.
</details>
