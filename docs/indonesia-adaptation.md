# Adaptasi standar Indonesia

Fork ini menyesuaikan Arch Studio untuk proyek di Indonesia (awalnya untuk proyek rumah sakit). Konten berstandar Amerika Serikat dihapus atau diganti, dan setiap rujukan regulasi diberi status verifikasi. Status di bawah berlaku per 24 November 2026.

## Yang dihapus

- Tujuh skill khusus New York City: `nyc-acris`, `nyc-bsa`, `nyc-dob-permits`, `nyc-dob-violations`, `nyc-hpd`, `nyc-landmarks`, `nyc-property-report`. Tidak ada padanan Indonesia yang bisa diakses dengan cara yang sama (data izin dan properti tingkat kabupaten/kota tidak tersedia sebagai API publik yang seragam).
- Sumber data AS (NYC Open Data, Census, FEMA, NOAA US, USGS US, EPA, HUD, BLS, MTA, FAA, AIA, CSI, NIBS, ASTM, Walk Score) dari katalog sumber.
- Default satuan imperial dan rujukan IBC.

## Yang diganti

| Sebelumnya | Sekarang |
|---|---|
| `zoning-analysis-nyc` (Zoning Resolution, PLUTO, FAR) | `zoning-analysis-id` (RDTR/peraturan zonasi, ITBX, KDB, KLB, KDH, KTB, GSB, KRK, KKPR, PBG) |
| agen `nyc-zoning-expert` | agen `indonesia-zoning-expert` |
| `occupancy-calculator` dengan IBC Table 1004.5 | Permen PU 26/PRT/M/2008 dan SNI 03-1746-2000, tanpa tabel bawaan |
| `spec-writer` dengan CSI MasterFormat | RKS teknis dengan rujukan SNI; MasterFormat hanya bila template klien memintanya |
| `architecture-knowledge` (AIA, CSI, NCS) | UU Arsitek, STRA, IAI, jasa konstruksi, pengadaan (LKPP) |
| Riset tapak dengan FEMA/NOAA/Census | BMKG, InaRISK/DIBI (BNPB), SNI 1726 (gempa), BIG, BPS, Kemenhub, Registrasi Nasional Cagar Budaya, AMDALNET |
| Satuan imperial, USD | SI (m, mm, m², °C) dan Rupiah (IDR) |
| Yurisdiksi `us`, `us-ny`, `us-ny-nyc`, `us-nj` | `id` (Indonesia), `id-jk`, `id-jb`, `id-bt` (contoh provinsi); kabupaten/kota di bawahnya |

## Status verifikasi rujukan

**Terverifikasi** berarti naskah resmi sudah dibuka dan isi yang dikutip dicocokkan. **Perlu verifikasi** berarti nomor dan judul dikenal tetapi naskah belum dibuka dalam pekerjaan ini, atau statusnya (masih berlaku, diubah, dicabut) belum dipastikan.

| Rujukan | Status | Catatan |
|---|---|---|
| Permenkes 6/2026 tentang Rumah Sakit | Terverifikasi sebagian | Naskah JDIH Kemenkes dibaca sampai Pasal 43. Pasal 8 (lokasi, tata ruang, satu area terintegrasi), Pasal 9 (persyaratan teknis sarana/prasarana didelegasikan ke peraturan perundang-undangan), Pasal 10 (minimal 50 TT untuk PMDN), Pasal 12 (klasifikasi paripurna/utama/madya/dasar per kelompok pelayanan), Pasal 15 ayat 6 (wajib perawatan isolasi). Masa transisi dua tahun menurut berita Ditjen Kesehatan Lanjutan, 25 Juni 2026. |
| Pencabutan Permenkes 3/2020 dan 40/2022 oleh Permenkes 6/2026 | Perlu verifikasi | Daftar Pasal 84 hanya terbaca lewat ringkasan, belum kata per kata. |
| Permenkes 40/2022 tentang Persyaratan Teknis Bangunan, Prasarana, dan Peralatan Kesehatan RS | Terverifikasi (judul, tanggal) | Ditetapkan 21 Desember 2022, diundangkan 22 Desember 2022 (BN 2022 No. 1309). Tidak memuat pasal pencabutan, jadi tidak secara tegas mencabut Permenkes 24/2016. Lampiran berupa gambar hasil pindai. |
| Permenkes 24/2016 | Perlu verifikasi | Status berlakunya belum dapat dipastikan. Tidak dirujuk sebagai standar yang berlaku. |
| Permen PU 26/PRT/M/2008 (proteksi kebakaran) | Perlu verifikasi | Tabel faktor beban hunian (termasuk baris pelayanan kesehatan) terlihat di modul ITB yang mengutipnya, belum dari naskah resmi. Cek apakah sudah diganti peraturan PU yang lebih baru. |
| SNI 03-1746-2000 (sarana jalan ke luar) | Perlu verifikasi | Cek edisi terbaru di BSN. |
| PP 16/2021 (bangunan gedung, PBG/SLF/KRK) | Perlu verifikasi | |
| UU 26/2007 dan PP 21/2021 (penataan ruang, RDTR, KKPR) | Perlu verifikasi | |
| SNI 1726:2019 (ketahanan gempa) | Perlu verifikasi | Cek edisi terbaru. |
| PP 22/2021 (persetujuan lingkungan, AMDAL/UKL-UPL) | Perlu verifikasi | |
| UU 11/2010 (cagar budaya) | Perlu verifikasi | |
| UU 6/2017 (arsitek), UU 2/2017 (jasa konstruksi) | Perlu verifikasi | Peraturan pelaksananya sudah beberapa kali diubah. |
| URL katalog sumber baru | Belum dicek otomatis | Semua entri baru memakai `checked_at: null`. Jalankan `node tools/integrations/source-health.mjs --check source:...` untuk memeriksa. URL `rsa.ciptakarya.pu.go.id/2021/` paling perlu dicek. |

Semua skill tetap mewajibkan pengambilan naskah asli sebelum menyimpulkan angka regulasi. Tidak ada tabel KDB/KLB/GSB atau faktor beban hunian yang dibundel.
