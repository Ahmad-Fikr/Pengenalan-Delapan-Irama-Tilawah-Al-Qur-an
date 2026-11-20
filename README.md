# Pengenalan Delapan Irama Tilawah Al-Qur'an (Deep Learning)

Repository ini berisi kode eksperimen, evaluasi model, dan dataset pengujian untuk penelitian skripsi:
**"Pengenalan Delapan Irama Tilawah Al-Qur'an Menggunakan Deep Learning"**

---

## 📁 Struktur Repository

```text
├── Referensi/
│   └── Notebook referensi publik awal (sebelum perbaikan)
│
├── Percobaan MFCC-SDCC/
│   ├── nb01_preprocessing/           # Deduplikasi, split 80:10:10, augmentasi & ekstraksi MFCC/SDCC
│   ├── nb02_cnn2d_mfcc/              # Baseline 2D CNN dengan fitur MFCC (Akurasi: 42.54%)
│   ├── nb03_cnn2d_sdcc/              # 2D CNN dengan fitur SDCC (Akurasi: 42.25%)
│   ├── nb04_crnn_hybrid/             # Model Hibrida CNN + BiGRU (Akurasi: 51.69%)
│   └── nb05_final_evaluation/        # Evaluasi gabungan, visualisasi kurva, Confusion Matrix & CSV
│
├── Percobaan Referensi/
│   ├── referensi-fixed-cnn-bilstm.ipynb  # Replikasi model referensi bebas data leakage (Akurasi: 78.96%)
│   └── outputs/                          # Confusion Matrix & kurva evaluasi
│
└── sample_uji_tambahan/
    └── Rekaman tilawah eksternal (MP3) untuk pengujian mandiri di luar dataset
```

---

## 🎯 Ringkasan Eksperimen

1. **Eksperimen MFCC & SDCC (Folder `Percobaan MFCC-SDCC`):**
   - Menguji fitur spektral MFCC dan dinamika temporal SDCC pada arsitektur CNN 2D dan CRNN.
   - Hasil menunjukkan fitur MFCC cenderung merepresentasikan karakteristik warna vokal (*timbre*) qari sehingga akurasi pada data *unseen* berkisar di ~51.69%.

2. **Eksperimen Model Pitch Contours (Folder `Percobaan Referensi`):**
   - Memperbaiki kelemahan metodologis riset terdahulu (*data leakage* augmentasi sebelum split).
   - Ekstraksi kontur nada dasar ($F_0$) via `librosa.piptrack` (358 frequency bins $\times$ 60 windows).
   - Arsitektur: 2D CNN + Bidirectional LSTM.
   - **Hasil Validasi Murni (Unseen Test Set):** Akurasi **78.96%** dan Weighted F1-Score **78.16%**.

---

## 📊 Dataset
Dataset yang digunakan merujuk pada dataset publik Kaggle:  
`murtadhanajim/maqam-in-holy-quran-dataset` (3.869 file audio terbagi dalam 8 kelas maqam: *Ajam, Bayat, Hijaz, Kurd, Nahawand, Rast, Saba, Seka*).
