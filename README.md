# HerbaFuzzy — Website Demo (offline)

## Cara menjalankan
1. Buka file `index.html` dengan Chrome, Edge, atau browser modern lainnya. Tidak perlu server, Python, internet, maupun instalasi tambahan.
2. Pilih **indikasi** lalu **bahan herbal utama**, klik **Analisis resep**.
3. Website mencari resep yang cocok persis dengan indikasi yang telah dinormalisasi dalam dataset, memilih resep termudah untuk herbal tersebut, dan menampilkan 5 alternatif herbal yang berbeda untuk indikasi sama.

## Cara hitung
Data skor telah dihitung menggunakan fungsi-fungsi langsung dari `notebook_sumber.ipynb` dan diverifikasi ulang memakai `fuzzy_core.py`: C-FCM k=3, m=2, 30 multi-start; Mamdani AND=min, implikasi=min, agregasi=max, centroid 2001 titik; kalibrasi monoton prefix-maximum di domain integer.

`recipes.json` menyimpan hasil per resep; `model_config.json` parameter model; `dataset_asli.csv` sumber data; `fuzzy_core.py` fungsi kalkulasi yang dapat direproduksi. Skor yang lebih kecil berarti tingkat kesulitan lebih rendah, bukan persentase mudah. Website memakai hasil prekomputasi agar dapat dipakai tanpa backend; perubahan dataset/model memerlukan regenerasi data hasil.

## Batasan
Ini penelitian tingkat **kompleksitas pembuatan**, bukan verifikasi keamanan, efektivitas, atau kecocokan klinis resep. Ranking dibuat hanya dari resep pada dataset yang benar-benar mencantumkan indikasi terkait. Ranking mendiversifikasi berdasarkan herbal utama: diambil skor terbaik per herbal agar top 5 tidak berisi herbal yang sama berulang kali.
