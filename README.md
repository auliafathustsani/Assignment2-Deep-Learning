# Assignment 2 - Deep Learning

## MNIST Classification with Learning Strategies

Repository ini berisi implementasi Assignment 2 mata kuliah Deep Learning mengenai klasifikasi dataset MNIST menggunakan neural network serta beberapa learning strategy, yaitu L1 Regularization, L2 Regularization, Dropout, Early Stopping, dan kombinasi L1 Regularization + Dropout.

## Identity

- Name: Aulia Fathus Tsani
- NIM: 24/534388/PA/22661
- Course: Deep Learning
- Assignment: Assignment 2 - Learning Strategy

## Dataset

Dataset yang digunakan adalah MNIST Handwritten Digit Dataset yang terdiri dari gambar grayscale berukuran 28 × 28 piksel dengan 10 kelas digit, yaitu 0 sampai 9.

Tahapan preprocessing data:
- Reshape menjadi `(28, 28, 1)`
- Konversi tipe data menjadi `float32`
- Normalisasi nilai piksel ke rentang 0–1
- One-hot encoding pada label

## Baseline Model

Arsitektur dasar yang digunakan mengikuti contoh pada slide Learning Strategy:

```text
Input (28 × 28 × 1)
        ↓
Flatten
        ↓
Dense (64, ReLU)
        ↓
Dense (10, Softmax)
```

Konfigurasi training:
- Optimizer: Adam
- Loss Function: Categorical Crossentropy
- Batch Size: 100
- Epochs: 10

## Experiments

Lima skenario learning strategy diterapkan pada model MNIST.

### 1. L1 Regularization

L1 Regularization diterapkan pada Dense layer dengan:

```text
L1 rate = 0.0001
```

### 2. L2 Regularization

L2 Regularization diterapkan pada Dense layer dengan:

```text
L2 rate = 0.0001
```

### 3. Dropout

Dropout diterapkan setelah hidden layer dengan:

```text
Dropout rate = 0.3
```

### 4. Early Stopping

Early Stopping menggunakan konfigurasi:

```text
monitor = val_loss
patience = 2
restore_best_weights = True
maximum epochs = 30
```

### 5. L1 Regularization + Dropout

Eksperimen terakhir menggabungkan L1 Regularization dan Dropout dengan:

```text
L1 rate = 0.0001
Dropout rate = 0.3
```

## Experimental Results

| Scenario | Test Accuracy | Test Loss | Epochs |
|---|---:|---:|---:|
| Baseline | 97.45% | 0.0836 | 10 |
| L1 Regularization | 97.24% | 0.1972 | 10 |
| L2 Regularization | 97.31% | 0.1212 | 10 |
| Dropout | 97.19% | 0.0945 | 10 |
| Early Stopping | 97.65% | 0.0790 | 16 |
| L1 + Dropout | 96.92% | 0.2234 | 10 |

## Conclusion

Berdasarkan eksperimen yang dilakukan:

- Early Stopping menghasilkan test accuracy sebesar 97.65% dan test loss sebesar 0.0790, dengan pelatihan berhenti otomatis setelah 16 epoch berdasarkan perubahan validation loss.
- Baseline model menghasilkan test accuracy sebesar 97.45% dan test loss sebesar 0.0836 pada 10 epoch.
- L1 dan L2 Regularization tetap menghasilkan accuracy yang tinggi, tetapi nilai loss meningkat karena adanya penalty term pada objective function.
- Dropout dengan rate 0.3 menghasilkan test accuracy sebesar 97.19% dan test loss sebesar 0.0945.
- Kombinasi L1 + Dropout menghasilkan test accuracy sebesar 96.92% dan test loss sebesar 0.2234, sehingga pada eksperimen ini belum meningkatkan performa dibandingkan baseline model.

## Files

Repository ini berisi:
- Jupyter Notebook / Google Colab untuk implementasi dan eksperimen
- Python script hasil export dari Google Colab
- Model summary, performance, dan loss chart untuk setiap skenario

## Google Colab

Notebook dapat dijalankan melalui Google Colab:

https://colab.research.google.com/drive/1l60se7lpJ0Mjz4u0AZFoNo3uXg8iraZl?usp=sharing
