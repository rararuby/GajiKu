## 👥 Anggota Kelompok

1. Mochamad Naufal Hanif
2. Inka Dayu Ningtyas
3. Rahmadina Jogi Siregar

# GajiKu – Sistem Informasi Penggajian Karyawan

## ERD
<img width="1244" height="694" alt="image" src="https://github.com/user-attachments/assets/17207718-f31f-4c81-b1fc-86949ab71a04" />

## 🗂️ Struktur Entitas

### 1. Users

* IdUser (PK)
* Username
* Password
* Role

---

### 2. Karyawan

* IdKaryawan (PK)
* Nama
* Alamat
* NoHP
* IdJabatan

---

### 3. Jabatan

* IdJabatan (PK)
* NamaJabatan
* GajiPokok

---

### 4. Lembur

* IdLembur (PK)
* IdKaryawan
* Tanggal
* Jam

---

### 5. Rekap_Absen

* IdRekap (PK)
* Bulan
* Hadir
* Izin
* Sakit
* Alpha
* Cuti

---

### 6. Gaji

* IdGaji (PK)
* IdRekap
* IdLembur
* Bulan
* GajiPokok
* TotalLembur
* Potongan
* TotalGaji
* Status

---

# ⚙️ Trigger pada Sistem

## 🔥 1. Trigger Perhitungan Gaji

### Nama

`trg_HitungGaji`

### Tabel

`gaji`

### Event

`AFTER INSERT`

### Fungsi

Menghitung gaji secara otomatis saat data gaji ditambahkan.

### Proses

* Mengambil gaji pokok dari jabatan
* Menghitung total lembur
* Menghitung potongan dari absensi
* Menghasilkan total gaji

---

## 🔐 2. Trigger Validasi Gaji

### Nama

`trg_ValidasiGaji`

### Tabel

`gaji`

### Event

`AFTER INSERT`

### Fungsi

Memastikan data gaji valid.

### Aturan

* Total gaji tidak boleh bernilai negatif

---

## 🔄 3. Trigger Update Status Gaji

### Nama

`trg_UpdateStatusGaji`

### Tabel

`gaji`

### Event

`UPDATE`

### Fungsi

Mengontrol proses persetujuan gaji.

### Aturan

* Gaji tidak bisa langsung "Dibayar"
* Harus melalui status "Disetujui" terlebih dahulu

---

## 🔁 4. Trigger Update dari Lembur (Opsional)

### Nama

`trg_UpdateGajiSetelahLembur`

### Tabel

`lembur`

### Event

`AFTER INSERT`

### Fungsi

Memperbarui data gaji jika terdapat tambahan lembur.

---
