# 📁 PetaPrakiraan_GerakanTanah_Bulanan

**Deskripsi:**  
Folder utama proyek *Peta Prakiraan Gerakan Tanah Bulanan*.  
Berisi seluruh komponen penting mulai dari *tools*, data input, hasil pemrosesan, layout peta, hingga output akhir dan dokumentasi.  
Struktur ini dibuat untuk menjaga keteraturan, memudahkan otomasi, dan mempercepat pembaruan peta bulanan.

---
## ⚙️ File Eksekusi Otomatis (.bat)
Berisi skrip batch untuk menjalankan proses otomatis proyek secara keseluruhan tanpa harus membuka ArcGIS Pro atau Python secara manual.

- `accept_conda_tos.bat` — Untuk menyetujui Terms of Service (TOS) dari Miniconda.
- `setup.bat` — Memperbarui data curah hujan dan ZKGT secara otomatis.  
- `Prakiraan_Gertan_Launcher_App.bat` — Mengekspor seluruh hasil peta dan laporan ke folder Output.

---

## 📁 01_Tools
Folder ini berisi semua alat teknis (*tools*) yang digunakan dalam proses pembuatan peta, seperti proyek ArcGIS, *Model Builder*, dan skrip Python.

### 📁 01_ArcGIS_Projects
Berisi proyek-proyek ArcGIS Pro yang digunakan untuk proses *digitasi*, *overlay*, dan pembuatan peta.

- 📁 **Digitasi_Overlay**  
  Folder untuk menyimpan proyek digitasi, overlay, dan *split* SHP di ArcGIS Pro.  

- 📁 **Model Builder**  
  Folder untuk menyimpan *Model Builder* dan skrip yang digunakan untuk pembuatan Peta Prakiraan Gerakan Tanah Bulanan.

  **Daftar Model Builder:**
  - `01_Auto Digitize Peta Prediksi Curah Hujan_Pro`  
    Model Builder untuk *digitasi otomatis* raster peta prediksi curah hujan bulanan menjadi SHP Curah Hujan seluruh Indonesia, baik untuk semua kelas maupun hanya kelas tinggi.
  **Output**:
  * CH_All.shp
  * CH_Tinggi.shp

  - `02_Overlay Normal Pro_fix`  
    Model Builder untuk meng-*overlay* ZKGT (Zona Kerentanan Gerakan Tanah) dengan SHP Curah Hujan Tinggi.  
    **Output:**
    * Zonasi_Overlay.shp  
    * PotensiBanjirBandang.shp
    * Split SHP Zonasi_Overlay.shp Per Provinsi dan Per Kabupaten

  - `03_Indonesia_Update_Data`  
    Skrip untuk memperbarui Peta Prediksi Curah Hujan dan Peta Prakiraan Gerakan Tanah se-Indonesia, serta mengekspor kedua peta tersebut dalam format JPEG.
    **Output:**
    * Peta Prakiraan Gerakan Tanah Bulanan se Indonesia format JPEG  
  - `04_Provinsi_Update_Data`  
    Skrip untuk memperbarui Peta Prakiraan Gerakan Tanah per provinsi, termasuk ekspor hasil dalam format JPEG.
    **Output:**
    * Peta Prakiraan Gerakan Tanah Bulanan Per Provinsi format JPEG 
  - `05_Kabupaten_Update_Data`  
    Skrip untuk memperbarui Peta Prakiraan Gerakan Tanah per kabupaten/kota, termasuk ekspor hasilnya.
    **Output:**
    * Peta Prakiraan Gerakan Tanah Bulanan Per Provinsi format JPEG
---

### 📁 02_Script_Python
Berisi seluruh skrip Python yang digunakan untuk otomasi proses, pembuatan laporan, serta pengarsipan peta.

- `Dashboard_Run.py`  
  🐍 Skrip utama untuk menjalankan seluruh proses pembuatan Prakiraan Gerakan Tanah Bulanan dan menampilkannya dalam bentuk *dashboard*.

- 📁 **old_version**  
  Berisi file lama yang disimpan sebagai arsip referensi.

- 📁 **PerKabupaten**  
  Berisi skrip Python untuk membuat laporan dan arsip berdasarkan kabupaten/kota.  
  * PerKabupaten_Script_Export_Docx_PDF.py 
    Script untuk export laporan dalam bentuk docx dan pdf.
  * PerKabupaten_Script_LaporanPeta_Archived.py 
    Script untuk mengarsipkan laporan dan peta dalam bentuk zip.
  * PerKabupaten_Script_SHP_RAR.py 
    Script untuk mengarsipkan shp zonasi overlay dalam bentuk zip.

- 📁 **PerProvinsi**  
Berisi skrip Python untuk membuat laporan dan arsip berdasarkan tingkat provinsi.  
  * PerProvinsi_Merge_Peta_Laporan_PDF.py
    Script untuk merge jadi satu file dari peta dan laporan seluruh provinsi di Indonesia.
  * PerProvinsi_Script_Export_Docx_PDF.py
    Script untuk meng-export laporan per provinsi menjadi format docx dan pdf.
  * PerProvinsi_Script_LaporanPeta_Archived.py
    Script untuk mengarsipkan laporan dan peta dalam bentuk zip.
  * PerProvinsi_Script_SHP_RAR.py
    Script untuk mengarsipkan file SHP zonasi overlay per provinsi dalam bentuk zip.

---

## 📁 02_Data_Input
Folder berisi semua data sumber yang digunakan untuk analisis dan pembuatan peta prakiraan.

### 📁 Basemaps
Berisi data spasial dasar yang digunakan dalam proses pemetaan.
- 📁 **Indonesia** — SHP batas administrasi, garis pantai, pulau, dan titik samudra seluruh Indonesia.  
- 📁 **Kabupaten** — SHP referensi untuk layout peta per kabupaten/kota.  
- 📁 **Layer File (.lyrx)** — Template simbolisasi layer untuk layout project di ArcGIS Pro.  
- 📁 **National** — Data referensi tingkat nasional berdasarkan per provinsi.

### 📁 Model Builder
Berisi data dan file pendukung *Model Builder* ArcGIS.
- 📁 **Classifier Definition File (.ecd)** — Data sampel untuk *classifier* raster peta curah hujan.  
- 📁 **Symbology Template** — Template simbolisasi hasil peta.

---

## 📁 03_Data_Processed
Berisi hasil olahan dari *Model Builder* dan skrip Python.

- 📁 **01_CurahHujan_SHP**  
Hasil dari `01_Auto Digitize Peta Prediksi Curah Hujan_Pro`.  
Berisi SHP Curah Hujan semua kelas dan kelas tinggi.

- 📁 **02_Tabel_Prakiraan**  
File hasil proses `02_Overlay Normal Pro_fix`.

- 📁 **03_Zonasi_Overlay**  
File hasil model builder `02_Overlay Normal Pro_fix`

- 📁 **04_ZKGT**  
Berisi data Zona Kerentanan Gerakan Tanah se-Indonesia (update 2021).

---

## 📁 04_Layouts
Folder layout proyek ArcGIS Pro untuk peta akhir.

- 📁 **Indonesia**  
Prakiraan_CurahHujan_GerakanTanah_Indonesia.aprx

- 📁 **PerKabupaten**  
PerKabupaten.aprx

- 📁 **PerProvinsi**  
PerProvinsi.aprx

---

## 📁 05_Output
Berisi hasil akhir berupa peta, laporan, dan arsip.

### 📁 Indonesia
- 📁 **01_Peta**
Peta_Prediksi_Curah_Hujan_Indonesia.jpg
Peta_Prakiraan_Gerakan_Tanah_Indonesia.jpg

### 📁 PerKabupaten
- 📁 01_Kabukota_Laporan_Word — Berisi file laporan dalam format docx per provinsi di Pulau Jawa.
- 📁 02_Kabukota_Peta_JPG — Berisi file peta per kabupaten se provinsi di Pulau Jawa
- 📁 03_Kabukota_Nomor_Halaman — Berisi file csv dengan informasi berupa nomor halaman laporan mulai, selesai, jumlah halaman, dan mulai halaman peta.
- 📁 04_Kabukota_Arsip_Laporan — Berisi file peta dan laporan dalam format zip
- 📁 05_Kabukota_Laporan_PDF —  Berisi file laporan dalam bentuk pdf
- 📁 06_Kabukota_SHP_Zonasi_Overlay — Berisi file SHP zonasi overlay per kabupaten se provinsi di Pulau Jawa
- 📁 Logs — Berisi log pengerjaan

### 📁 PerProvinsi
- 📁 01_Provinsi_Laporan_Word — Berisi file laporan prakiraan per provinsi dalam format docx.
- 📁 02_Provinsi_Peta_JPG — Berisi file peta prakiraan per provinsi dalam format JPEG.
- 📁 03_Provinsi_Nomor_Halaman — Berisi file csv yang memuat informasi nomor halaman laporan dan peta prakiraan per provinsi.
- 📁 04_Provinsi_Laporan_PDF — Berisi file laporan prakiraan per provinsi dalam format pdf.
- 📁 05_PerProvinsi_Prakiraan_SHP — Berisi arsip SHP Zonasi Overlay per provinsi dalam bentuk zip.
- 📁 06_Arsip_PerProvinsi_Laporan&Peta — Berisi arsip yang memuat laporan dan petanya dalam bentuk zip.
- 📁 07_Merged_PDF — Berisi 1 file yang memuat seluruh peta dan laporan per provinsi se Indonesia.

---

## 📁 06_Documentation
Berisi dokumentasi proyek:
- Panduan teknis dan tutorial penggunaan skrip serta Model Builder.   
- Dokumen pendukung seperti manual pengguna dan penjelasan filenya

---
