# Praktikum Big Data

Repositori ini mendokumentasikan modul materi, dataset, latihan mandiri, dan laporan tugas praktikum untuk mata kuliah **Big Data**.

---

## 📌 Catatan Penggunaan Lingkungan (Environment Note)

> [!NOTE]
> Pada praktikum ini, terdapat sedikit penyesuaian dari modul resmi:
> Alih-alih menggunakan **Anaconda / Conda**, repositori ini menggunakan **[`uv`](https://github.com/astral-sh/uv)** sebagai Python package & environment manager.
> 
> Penggunaan `uv` dipilih karena performanya yang jauh lebih cepat, konsumsi resource memori yang ringan, serta kompatibilitas langsung dengan virtual environment standar Python (`.venv`).

### Menyiapkan Environment dengan `uv`

1. **Membuat virtual environment**:
   ```bash
   uv venv
   ```

2. **Mengaktifkan virtual environment**:
   ```bash
   source .venv/bin/activate
   ```

3. **Menginstal paket / library utama**:
   ```bash
   uv pip install pyspark==3.5.9 jupyter pandas numpy matplotlib
   ```

4. **Menjalankan Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

---

## 🚀 Panduan Menjalankan Hadoop & YARN

Sebelum menjalankan praktikum yang melibatkan penyimpanan HDFS atau komputasi terdistribusi, pastikan service Hadoop sudah berjalan dengan langkah-langkah berikut:

### 1. Menjalankan HDFS (Hadoop Distributed File System)
Jalankan perintah berikut di terminal:
```bash
start-dfs.sh
```
Perintah ini akan memulai daemon `NameNode`, `DataNode`, dan `SecondaryNameNode`.

### 2. Menjalankan YARN (Yet Another Resource Negotiator)
Jalankan perintah berikut:
```bash
start-yarn.sh
```
Perintah ini akan memulai daemon `ResourceManager` dan `NodeManager`.

### 3. Verifikasi Status Layanan dengan `jps`
Gunakan perintah `jps` untuk memverifikasi bahwa seluruh proses Java Hadoop berjalan dengan benar:
```bash
jps
```

Pastikan setidaknya **5 proses daemon Hadoop** berikut muncul pada output:
```text
xxxxx NameNode
xxxxx DataNode
xxxxx SecondaryNameNode
xxxxx ResourceManager
xxxxx NodeManager
xxxxx Jps
```

### 4. Akses Web UI
Jika daemon telah berjalan, antarmuka web monitoring dapat diakses melalui browser:
- **HDFS NameNode UI**: [http://localhost:9870](http://localhost:9870)
- **YARN Resource Manager UI**: [http://localhost:8088](http://localhost:8088)
- **Spark Job UI** *(saat SparkSession aktif)*: [http://localhost:4040](http://localhost:4040)

### 5. Menghentikan Layanan Hadoop
Jika praktikum telah selesai, matikan layanan secara bertahap:
```bash
stop-yarn.sh
stop-dfs.sh
```

---

## 📂 Struktur Direktori

Setiap folder pertemuan menggabungkan modul praktikum, tugas, dan file dataset terkait:

```text
praktikum-bigdata/
├── pertemuan-02/      # Pengenalan Environment, Python Dasar & Pandas Eksplorasi
├── pertemuan-03/      # HDFS CLI, Unggah/Unduh Data & Pemrosesan Data Terdistribusi
├── pertemuan-04/      # Apache Spark & PySpark DataFrame Operations
├── pertemuan-05/      # PySpark DataFrame Lanjutan: Join, Window Function & Spark SQL
├── .gitignore         # Mengabaikan checkpoint jupyter & temporary files
└── README.md          # Dokumentasi repositori dan panduan eksekusi
```
