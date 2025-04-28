# Klasifikasi Gambar Beras Menggunakan Convolutional Neural Network (CNN)

## Ringkasan Proyek
Proyek ini bertujuan untuk mengembangkan model klasifikasi gambar berbasis **Convolutional Neural Network (CNN)** guna mengidentifikasi lima jenis beras, yaitu:
- Karacadag
- Basmati
- Jasmine
- Arborio
- Ipsala

Dataset dapat diakses pada link berikut: https://www.kaggle.com/datasets/muratkokludataset/rice-image-dataset 

Model ini dibangun menggunakan framework **TensorFlow** dan **Keras**, serta menerapkan teknik regularisasi untuk mengurangi risiko overfitting.

## Struktur Dataset
Dataset disusun dalam dua direktori utama:
- `train/`: Data untuk proses pelatihan model
- `validation/`: Data untuk proses validasi model

Setiap jenis beras memiliki subfolder tersendiri yang berisi gambar-gambar sesuai kelasnya.

## Arsitektur Model
Model CNN yang dikembangkan memiliki struktur sebagai berikut:
- **Convolutional Block 1**
  - Conv2D (32 filters, 3x3 kernel, padding='same', activation='relu')
  - Batch Normalization
  - Max Pooling (2x2)
- **Convolutional Block 2**
  - Conv2D (32 filters, 3x3 kernel, padding='same', activation='relu')
  - Batch Normalization
  - Max Pooling (2x2)
- **Convolutional Block 3**
  - Conv2D (64 filters, 5x5 kernel, padding='same', activation='relu')
  - Batch Normalization
  - Max Pooling (2x2)
- **Fully Connected Layers**
  - Flatten
  - Dense (64 units, activation='relu')
  - Dropout (rate=0.3)
  - Output Dense (5 units, activation='softmax')

## Strategi Training
- **Loss Function**: `categorical_crossentropy` (multi-class classification)
- **Optimizer**: `Adam` dengan learning rate 0.0003
- **Class Weighting**: Menggunakan perhitungan bobot kelas untuk mengatasi ketidakseimbangan data.
- **Callbacks**:
  - **Custom Early Stopping**: Menghentikan training jika akurasi training mencapai 96%.
  - **ReduceLROnPlateau**: Menurunkan learning rate secara dinamis ketika `val_loss` stagnan.
  - **Model Checkpoint**: Menyimpan model terbaik berdasarkan `val_accuracy`.

## Instalasi dan Persiapan
Pastikan environment telah memiliki dependensi berikut:
- tensorflow
- tensorflowjs
- keras
- scikit-learn
- opencv-python
- Pillow
- scikit-image
- tqdm
- matplotlib
- seaborn
- pandas
- numpy
