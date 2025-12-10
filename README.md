# PROJECT_SO_ANDRI!

---

# 1. Buat Struktur Direktori**

```bash
mkdir -p documents images archives logs
```

---

# 2. Buat 20+ File Sample**

Berikut contoh pembuatan 20+ file dengan berbagai ekstensi:

```bash
# File dokumen
touch sample1.txt sample2.txt report.doc notes.md info.pdf
echo "Ini file txt" > sample1.txt
echo "Ini laporan dokumen" > report.doc

# File gambar
touch img1.jpg img2.png img3.jpeg
echo "binary image placeholder" > img1.jpg

# File arsip
touch backup1.zip backup2.tar.gz data.rar

# File log
touch log1.log log2.log system.log

# File acak
touch script.sh data1.csv data2.csv config.yaml unknown.tmp
```

---

# 3. Script Organisasi File Otomatis**

Script berikut akan memindahkan file berdasarkan ekstensi ke folder yang sesuai:

> **save as:** `organize_files.sh`

```bash
#!/bin/bash

echo "Mengorganisasi file..."

# Dokumen
find . -maxdepth 1 -type f \( -name "*.txt" -o -name "*.doc" -o -name "*.md" -o -name "*.pdf" \) \
    -exec mv {} documents/ \;

# Gambar
find . -maxdepth 1 -type f \( -name "*.jpg" -o -name "*.png" -o -name "*.jpeg" \) \
    -exec mv {} images/ \;

# Arsip
find . -maxdepth 1 -type f \( -name "*.zip" -o -name "*.tar.gz" -o -name "*.rar" \) \
    -exec mv {} archives/ \;

# Log
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

echo "Selesai!"
```

Jalankan:

```bash
chmod +x organize_files.sh
./organize_files.sh
```

---

# 4. Fungsi Pencarian File**

Script berikut menyediakan 3 fungsi pencarian:

> **save as:** `search_tools.sh`

```bash
#!/bin/bash

search_by_name() {
    echo "Mencari file dengan nama: $1"
    find . -type f -name "*$1*"
}

search_by_size() {
    echo "Mencari file lebih besar dari $1"
    find . -type f -size +"$1"
}

search_by_content() {
    echo "Mencari konten dalam file: $1"
    grep -Rni "$1" .
}

echo "Pilih fungsi: "
echo "1) Cari berdasarkan nama"
echo "2) Cari berdasarkan ukuran"
echo "3) Cari berdasarkan konten"

read -p "Masukkan pilihan (1/2/3): " choice

case $choice in
    1)
        read -p "Masukkan nama: " nm
        search_by_name "$nm"
        ;;
    2)
        read -p "Ukuran contoh +10k, +1M: " sz
        search_by_size "$sz"
        ;;
    3)
        read -p "Masukkan keyword konten: " kw
        search_by_content "$kw"
        ;;
    *)
        echo "Pilihan tidak valid"
        ;;
esac
```

Jalankan:

```bash
chmod +x search_tools.sh
./search_tools.sh
```

---

# 5. Generate Laporan Sistem File**

Gunakan `ls`, `wc`, `du`, piping, dan redirect output ke `report.txt`.

> **save as:** `generate_report.sh`

```bash
#!/bin/bash

echo "===== LAPORAN SISTEM FILE =====" > report.txt

echo -e "\nJumlah file dalam direktori kerja:" >> report.txt
ls -1 | wc -l >> report.txt

echo -e "\nList file:" >> report.txt
ls -lh >> report.txt

echo -e "\nUkuran total per folder:" >> report.txt
du -sh * >> report.txt

echo -e "\nJumlah baris di semua file teks:" >> report.txt
find . -type f -name "*.txt" -exec wc -l {} \; >> report.txt

echo -e "\nLaporan selesai dibuat pada $(date)" >> report.txt
```

Jalankan:

```bash
chmod +x generate_report.sh
./generate_report.sh
```

---

#  **Semua tugas proyek selesai!**

