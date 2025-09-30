# ⚙️ Analisis Layout Profil Instagram: Bootstrap Responsive

Dokumen ini menjelaskan keputusan konfigurasi layout berbasis Bootstrap, strategi aksesibilitas tombol aksi di perangkat mobile, dan analisis skalabilitas galeri postingan.

---

## 1. Konfigurasi Kolom Header Profil Berdasarkan Breakpoint

Pembagian kolom (`col`) pada header profil dirancang untuk meniru tata letak Instagram yang memisahkan Foto Profil (kiri) dan Informasi Profil (kanan) dengan *whitespace* yang ideal.

| Elemen | Breakpoint | Konfigurasi Bootstrap | Rasionalisasi Desain |
| :--- | :--- | :--- | :--- |
| **Foto Profil** | Mobile (Default) | `col-4` | Mengambil **4 dari 12 kolom**. Ini memastikan foto profil berada di kiri dan ukurannya proporsional, tidak terlalu mendominasi area di layar kecil. |
| **Informasi Profil** | Mobile (Default) | `col-8` | Mengambil **8 dari 12 kolom**. Memastikan *username*, *stats*, dan *bio* memiliki ruang yang luas (**2/3 layar**) agar mudah dibaca di mobile. |
| **Foto Profil** | Desktop (`lg`) | `col-lg-4` | Tetap menggunakan **4 dari 12 kolom**. Di desktop, konfigurasi ini (bersama *padding* yang memadai) memberikan ruang kosong (*whitespace*) yang besar di sekeliling foto, meniru gaya Instagram Desktop yang minimalis dan rapi. |
| **Informasi Profil** | Desktop (`lg`) | `col-lg-8` | Tetap **8 dari 12 kolom**. Memanfaatkan lebar sisa layar yang besar untuk menempatkan *username* dengan font yang lebih besar, *stats* sejajar horizontal, dan blok *bio*. |

---

## 2. Strategi Aksesibilitas Tombol Aksi di Mobile

Pada perangkat mobile, tombol seperti **Edit Profil** dan **Bagikan Profil** harus berada di lokasi yang mudah dijangkau (*thumb zone*), biasanya tepat di bawah informasi profil.

### Pendekatan Layout yang Digunakan:

1.  **Visibilitas Eksklusif Mobile:** Blok tombol aksi hanya ditampilkan di layar $<992px$ (mobile/tablet) menggunakan kelas `d-lg-none`.
2.  **Sejajar dan Penuh Lebar:** Tombol ditempatkan dalam `$row$` dengan $`col-6`$.
    * Setiap tombol diberikan **50% lebar** dari wadahnya (`col-6`).
    * Menggunakan *gap* kecil (`gx-2`) untuk memisahkan kedua tombol.
3.  **Tujuan:** Ini menghasilkan dua tombol yang **berdampingan secara horizontal** dan menempati hampir seluruh lebar layar. Desain ini efisien, konsisten, dan sangat mudah diakses oleh ibu jari pengguna mobile.

```html
<div class="row mb-4 gx-2 d-lg-none">
    <div class="col-6"> 
        </div>
    <div class="col-6"> 
        </div>
</div>