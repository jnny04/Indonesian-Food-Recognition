# Indonesian Food Recognition & Nutrition Analysis using YOLOv8

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/Model-YOLOv8-green)
![Status](https://img.shields.io/badge/Status-Active-success)

## Tentang Proyek
Repository ini berisi model *Computer Vision* berbasis **YOLOv8** yang dilatih khusus untuk mendeteksi berbagai jenis **makanan Indonesia** (seperti Nasi Goreng, Rendang, Sate, dll). 

Selain mendeteksi jenis makanan, sistem ini juga terintegrasi dengan database nutrisi untuk memberikan estimasi informasi gizi (Kalori, Protein, Lemak, Karbohidrat) dari makanan yang terdeteksi.

Proyek ini merupakan bagian dari *backend engine* untuk aplikasi mobile **"EatWell"** (Android).

## Fitur Utama
* **Deteksi Akurat:** Menggunakan arsitektur YOLOv8 (You Only Look Once) untuk deteksi real-time.
* **Analisis Nutrisi:** *Mapping* otomatis dari label deteksi ke database nutrisi (`nutrition_data.csv`).
* **Kategori Makanan:** Melatih model pada `16` kelas makanan Indonesia, termasuk:cakwe, dadar gulung, ikan goreng, klepon, lontong sayur, martabak manis, mie goreng, nasi padang, rendang, risol, rujak buah, sayur asem, soto ayam, nasi goreng, rawon, sate


## Struktur Folder
```text
├── data/               # Sampel gambar & database nutrisi (csv)
├── models/             # File model hasil training (.pt)
├── notebooks/          # Jupyter Notebook untuk training & eksperimen
├── src/                # Source code untuk inferensi & utilitas
├── app/                # Script deployment (Gradio/HuggingFace)
└── requirements.txt    # Daftar library yang dibutuhkan
```

## Performa Model
| Stage | Precision | Recall | mAP50 |
| :--- | :---: | :---: | ---: |
| Phase I | 0.89 | 0.81 | 0.81 |
| Phase II | 0.86 | 0.84 | 0.81 |
| Test Set | 0.88 | 0.84 | 0.89 |

## Implementasi & Deployment

Sistem ini dirancang dengan arsitektur **Client-Server**. Model YOLOv8 di-hosting di cloud, sementara aplikasi Android bertindak sebagai client yang mengirim gambar.

### 1. Arsitektur Sistem
```mermaid
graph LR
    A[Android App (EatWell)] -- POST Image --> B((Hugging Face Space))
    B -- 1. Detect Object --> C[YOLOv8 Model]
    C -- 2. Map Nutrition --> D[Nutrition DB]
    D -- Return JSON (Label & Nutrition) --> A
```
### 2. Deployment Platform
Model dideploy menggunakan Hugging Face Spaces dengan antarmuka Gradio. Ini memungkinkan model diakses baik melalui Web Interface maupun melalui API endpoint.
- Platform: Hugging Face Spaces
- Interface: Gradio SDK
- Status: Running 🟢
- Demo URL: (https://huggingface.co/spaces/Jenny0412/api-nutrisi-makanan)

---
Created by Ratu Rinjanhei Macinnes - Informatics Student
