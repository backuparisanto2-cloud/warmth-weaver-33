# Perbaiki Denah Interaktif dengan Denah Riil

Mengganti 4 gambar denah sementara (hasil AI) dengan denah arsitektur asli yang baru diunggah, lalu menyetel ulang seluruh area klik agar pas di atas kamar dan fasilitas yang sebenarnya.

## Yang akan dikerjakan

1. **Unggah 4 denah asli** (Lantai 1, 2, 3, Rooftop) ke penyimpanan gambar project dan pakai sebagai sumber denah interaktif, menggantikan gambar placeholder.
2. **Setel ulang area klik (hotspot)** untuk tiap lantai berdasarkan posisi kamar di denah asli:
   - Lantai 1: 10 kamar + Lobby, Selasar, Dapur/KMD, Tangga
   - Lantai 2: 11 kamar + Selasar, Balkon, Dapur/KMD, Tangga
   - Lantai 3: 10 kamar + Lobby, Selasar, Balkon, Dapur/KMD, Tangga
   - Rooftop: area Dak Atap, Atap Kamar, Tangga/Turun, Rooftop (tengah & timur), Cuci Jemur
3. **Sesuaikan pemotongan gambar (crop) dan rasio** tiap denah supaya gambar tampil penuh tanpa ruang putih berlebih, baik di ponsel maupun desktop.
4. **Verifikasi visual**: buka halaman Denah, ambil tangkapan layar tiap lantai, dan pastikan setiap kotak kamar benar-benar menempel pada ruangannya serta klik kamar membuka detail inventaris yang tepat.

## Catatan penomoran kamar

Nomor kamar di denah asli tidak tertulis (hanya "KAMAR"), jadi penomoran mengikuti data yang sudah ada di database (001–010 lantai 1, 011–021 lantai 2, 022–031 lantai 3) dengan urutan kiri → kanan, baris atas dulu lalu baris bawah. Jika urutan sebenarnya berbeda, tinggal beri tahu dan saya geser pemetaannya.

## Detail teknis

- Denah asli disimpan sebagai CDN asset (`lovable-assets create`) dan pointer `.asset.json` di `src/assets/` diperbarui.
- `src/lib/floorplan.ts`: hotspot ditulis ulang dengan koordinat persen baru; `FLOOR_CROP` / `ROOFTOP_CROP` dan `aspect` disesuaikan dengan dimensi gambar asli (denah lantai 1024×1024, rooftop 1160×933 — akan diukur ulang dari file yang diunggah).
- Tidak ada perubahan skema database atau logika data; hanya lapisan tampilan denah.

## Ditunda

Impor ulang data lama dari project sumber dikerjakan belakangan, saat file ekspor datanya siap.
