# Classify-Crop-Detected-Images
Model dibuat menggunakan domain computer vision dengan algoritma Yolov8. Hasil akhir dari pelatihan model mendapatkan mAP=54%, Recall=60%, Precission=40%

------------------------------
**1. Data Akuisisi**
Dataset yang digunakan terdiri dari 39 gambar buah apel, yang mencakup tiga jenis warna: merah, kuning, dan hijau. Masing-masing jenis warna memiliki 10 gambar yang berbeda.

Proses pelabelan dilakukan menggunakan Roboflow, dengan menetapkan 3 kelas bounding box, yaitu:

    Red (apel merah)
    Yellow (apel kuning)
    Green (apel hijau).
    
**2. Data Exploration**

pada tahap ini, image kami atur scalenya menjadi 640x640 piksel.

Langkah ini dilakukan dengan tujuan:  
1. **Konsistensi Data:** Mengatur semua gambar pada skala yang sama memastikan keseragaman dalam dimensi input model, sehingga model dapat diproses dengan lebih efisien.  
2. **Efisiensi Pemrosesan:** Ukuran gambar yang terlalu besar dapat meningkatkan beban komputasi, sementara ukuran yang terlalu kecil dapat mengurangi kualitas informasi yang diperoleh. Ukuran 640x640 dipilih untuk mencapai keseimbangan antara resolusi yang cukup tinggi dan efisiensi pemrosesan.  
3. **Menghindari Distorsi:** Dalam proses scaling, kami menggunakan metode yang menjaga rasio aspek asli dari gambar sehingga tidak terjadi distorsi atau deformasi.  

Proses eksplorasi ini tidak hanya terbatas pada pengaturan skala gambar, tetapi juga melibatkan:  
- **Pemeriksaan Kualitas Gambar:** Memastikan tidak ada gambar yang rusak, buram, atau mengandung noise yang signifikan.  
- **Pemeriksaan Distribusi Data:** Memastikan distribusi data seimbang, terutama jika gambar diklasifikasikan ke dalam beberapa kelas (categories).  
- **Augmentasi Data (Opsional):** Menambahkan variasi pada dataset, seperti rotasi, flipping, atau pengaturan pencahayaan, untuk meningkatkan ketahanan model terhadap variasi data di dunia nyata.
Berikut adalah penjelasan yang lebih terstruktur dan terperinci mengenai tahap **Modeling** yang Anda lakukan, dengan disesuaikan pada tahapan pembuatan model AI:

---

### **3. Modeling**

#### **3.1 Pelatihan Model**
Model dilatih menggunakan algoritma YOLOv8 pada dataset yang telah dipersiapkan sebelumnya. Selama proses pelatihan, beberapa parameter disesuaikan untuk mencapai performa terbaik, seperti:
- **Confidence Threshold (conf):** 0.5, yang berarti model hanya menganggap deteksi valid jika tingkat kepercayaannya lebih dari 50%.
- **Model Output:** Setelah pelatihan selesai, model terbaik disimpan sebagai file `best.pt`. File ini mewakili bobot terbaik yang diperoleh selama proses pelatihan.

#### **4. Evaluasi Model**
Model yang telah dilatih diuji performanya menggunakan metrik Mean Average Precision (mAP). Pada pengujian awal, dengan **confidence threshold** 0.5, model menghasilkan nilai **mAP sebesar 54%**. Nilai ini menunjukkan tingkat akurasi model dalam mendeteksi dan mengklasifikasikan objek pada dataset pengujian.

Berikut Grafik visualisasi dari hasil evaluasi model:

![results(1)](https://github.com/user-attachments/assets/123a6cfe-23b7-4896-97ef-ddf98067e535)

![R_curve(1)](https://github.com/user-attachments/assets/8ee6134a-0c75-49a9-aa34-36208fa36347)

![P_curve(1)](https://github.com/user-attachments/assets/d36b365c-5a3d-46bf-8ebe-91f53794de41)

![PR_curve](https://github.com/user-attachments/assets/ecad4700-a47d-42d2-93a0-7ba18537f4f0)


#### **5. Analisis Hasil**
Hasil inferensi menunjukkan bahwa model mampu mendeteksi objek sesuai dengan kelasnya dan menghasilkan gambar potongan objek yang terdeteksi. Penggunaan nilai confidence threshold 0.5 memastikan hanya deteksi yang cukup meyakinkan yang dipertimbangkan. Proses ini membantu dalam mengevaluasi model secara visual dan mengidentifikasi area yang memerlukan peningkatan performa.

![train_batch1](https://github.com/user-attachments/assets/d192456d-23da-4b63-9eef-3aa094e25cdc)

![val_batch0_labels](https://github.com/user-attachments/assets/02d21efd-f599-4594-ab3d-c4671e21d157)


---
Output Classify Crop Detected Images.

![red_1](https://github.com/user-attachments/assets/b9010384-e6c6-44e1-aa75-849ca8c50ee8)

![green_1](https://github.com/user-attachments/assets/ea82b498-4efc-472d-b34b-aff2041c7055)

![yellow_1](https://github.com/user-attachments/assets/692a3a93-dadf-4d16-83c1-2d4f85989d21)
