
# Online Retail II

**Bahasa**: Python
**Dataset**: `online_retail_II.xlsx`  

## Tujuan
1. Memahami struktur data dan kualitas data.
2. EDA penjualan: KPI dasar (orders, customers, products, revenue), top produk, top negara, tren waktu bulanan.
3. RFM untuk segmentasi pelanggan.

## Algoritma & Alasan
1. Data Cleaning(Missing Value Handling dan Outlier Removal.) 
    -Mengganti Description yang kosong dengan "Unknown".
    -Menghapus baris dengan Customer ID kosong.
    -Menghapus transaksi pembatalan/refund (Invoice diawali "C" atau Quantity <= 0).
Alasan: Data bersih sangat penting supaya analisis tidak bias. Misalnya, jika Customer ID kosong tetap dihitung, analisis perilaku pelanggan tidak valid.

2. Feature Engineering(Rule-based Transformation.)
    -Membuat kolom total_price = Quantity * Price.
Alasan: Menentukan revenue dari setiap transaksi, yang akan menjadi dasar untuk analisis RFM & agregasi penjualan.

3. Time-series Aggregation(Resampling bulanan (Pandas Time-series Resample))
    -Menggunakan frekuensi MS (Month Start) untuk menghitung tren bulanan.
Alasan: Penjualan e-commerce biasanya dipengaruhi faktor waktu (musiman/seasonal). Resampling membantu melihat pola dan tren jangka panjang.

4. RFM Analysis(Recency, Frequency, Monetary)
    -Recency = selisih hari terakhir transaksi dengan tanggal akhir dataset.
    -Frequency = jumlah transaksi.
    -Monetary = total nilai transaksi.
Alasan: RFM adalah algoritma klasik dalam Customer Relationship Management (CRM) untuk mengukur loyalitas pelanggan dan segmentasi berbasis perilaku. Dengan ini kita bisa bedakan pelanggan “loyal”, “baru”, atau “tidak aktif”.

5. Visualization(Matplotlib Charting)
Alasan: Memberikan insight visual yang lebih mudah dipahami oleh stakeholder dibanding hanya tabel angka.
