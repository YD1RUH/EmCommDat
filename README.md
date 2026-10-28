# EmCommDat

<p align="center">
  <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/logo.png" alt="Logo EmCommDat" width="200">
</p>

## Android Audio Modem for data communication
Aplikasi Android untuk **mengirim pesan teks dan berbagi posisi lewat radio, tanpa internet dan tanpa pulsa**. Pesan diubah menjadi nada audio (modulasi MFSK), dikirim lewat HT atau rig, lalu diterjemahkan kembali menjadi teks oleh HP penerima.

Dengan aplikasi ini, HP Anda berfungsi seperti modem data sederhana untuk radio: ketik pesan, kirim lewat radio, dan penerima langsung membacanya di layar HP.

> **Catatan:** aplikasi ini memakai MFSK versi sederhana buatan sendiri dan **belum kompatibel dengan fldigi** atau aplikasi MFSK lain. Kedua pihak harus memakai aplikasi ini dengan mode yang sama.

## Apa yang bisa dilakukan

- **Kirim dan terima pesan teks** lewat radio, lengkap dengan pengirim, tujuan, dan pengecekan kesalahan (CRC) agar pesan rusak tidak ditampilkan sebagai pesan valid.
- **Pilih kecepatan** sesuai kondisi: MFSK8, MFSK16, MFSK32, atau MFSK64. Mode lebih lambat butuh waktu lebih lama, mode lebih cepat mengirim lebih singkat.
- **Monitor sinyal masuk** dengan tampilan spektrum dan log penerimaan realtime.
- **Inbox** untuk menyimpan pesan yang sudah diterima.
- **Beacon posisi:** kirim lokasi GPS Anda secara berkala dalam format derajat, menit, detik (DMS).
- **Radar penunjuk arah:** lihat arah dan jarak ke teman yang mengirim beacon, bergerak mengikuti arah HP Anda.
- **Mode uji (Loopback):** coba semua fitur tanpa radio, cukup dengan satu HP.

## Pemanfaatan

Beberapa contoh penggunaan:

- **Komunikasi cadangan** saat sinyal seluler atau internet tidak tersedia, misalnya di gunung, hutan, laut, atau area bencana.
- **Kegiatan outdoor dan komunitas radio:** pendakian, touring, konvoi, dan SAR, di mana anggota tim perlu saling tahu posisi.
- **Berbagi posisi tim** tanpa internet: setiap anggota mengirim beacon, lalu radar menunjukkan ke arah mana dan seberapa jauh teman Anda.
- **Latihan dan eksperimen** komunikasi digital di radio amatir.
- **Belajar** bagaimana data teks dikirim lewat audio dan radio.

## Tampilan

| Gambar | Deskripsi |
|---|---|
| <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/compose.jpeg" alt="Compose" width="250"> | **Compose** – tulis pesan (From, To, Message), pilih mode, lalu tekan Send. Estimasi lama pengiriman ditampilkan. Tersedia tombol Paste, Clear, dan Loopback untuk uji. |
| <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/rx.jpeg" alt="Monitor RX" width="250"> | **Monitor RX** – tekan Start RX untuk mendengarkan. Spektrum menunjukkan sinyal yang masuk, dan hasil terjemahan tampil realtime di bawahnya. |
| <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/inbox_detail.jpeg" alt="Inbox" width="250"> | **Inbox** – daftar pesan masuk lengkap dengan waktu terima. Ketuk untuk membaca isinya. |
| <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/beacon_radar.jpeg" alt="Position" width="250"> | **Position** – atur beacon (durasi dan ID callsign), pilih station dari daftar, dan mulai tracking. |
| <img src="https://raw.githubusercontent.com/YD1RUH/EmCommDat/main/Picture/beacon_radar.jpeg" alt="Radar" width="250"> | **Radar** – pusat adalah posisi Anda. Garis menunjuk ke station terpilih beserta jaraknya (M atau KM). Bila belum ada station dipilih, tujuan bawaannya adalah Monumen Nasional, Jakarta. |

## Persyaratan

- HP Android 8.1 atau lebih baru.
- Izin **Mikrofon** (untuk menerima) dan **Lokasi – Tepat/Precise** (untuk fitur Position).
- Radio (HT atau rig) bila ingin dipakai lewat gelombang radio.

## Cara Penggunaan

Aturan umum untuk kedua cara:

1. Pengirim dan penerima memakai **mode yang sama**.
2. Aplikasi bekerja **bergantian** (half-duplex): saat mengirim, penerimaan berhenti sementara, lalu lanjut sendiri setelah selesai.
3. Aplikasi **tidak mengendalikan PTT**. PTT ditekan manual, atau memakai VOX di radio/interface Anda.

### Cara 1 – Speaker HP didekatkan ke mic HT (tanpa kabel)

Cara paling sederhana, tidak butuh perangkat tambahan.

**Mengirim**

1. Buka **Compose**, pilih mode, lalu tulis pesan.
2. Dekatkan **speaker HP** ke **mikrofon HT**.
3. **Tekan dan tahan PTT** di HT, lalu tekan **Send**.
4. **Tahan PTT sampai pengiriman selesai** (progress penuh dan status "Terkirim"), baru lepas.

**Menerima**

1. Buka **Monitor RX**, pilih mode yang sama dengan pengirim, lalu tekan **Start RX**.
2. Dekatkan **speaker HT** ke **mikrofon HP**.
3. Atur volume HT sampai spektrum bergerak jelas saat ada sinyal.
4. Pesan yang sukses diterima masuk ke **Inbox**.

Tips: pilih tempat yang tenang, jangan menyentuh HP atau HT selama transmisi, dan atur volume secukupnya (terlalu keras justru membuat suara pecah).

> Cara ini kurang praktis untuk beacon posisi berkala, karena PTT harus ditahan di setiap pengiriman. Untuk beacon, gunakan Cara 2.

### Cara 2 – Kabel soundcard (audio langsung)

Lebih stabil dan tidak terganggu noise ruangan. Audio HP disambungkan langsung ke radio.

**Yang dibutuhkan**

- Adaptor atau sound card yang dikenali HP Android (USB atau jack audio), serta kabel ke jack mic dan speaker/data radio Anda.
- Disarankan memakai **atenuator** pada jalur audio HP ke mic radio, dan **isolator audio** untuk mencegah dengung.

**Sambungan**

| Dari | Ke |
|---|---|
| Output audio HP | Input mic atau data radio |
| Output speaker atau data radio | Input mic HP (atau input sound card) |

**Mengirim**

1. Sambungkan kabel dan atur volume HP mulai dari kecil agar tidak berlebihan masuk ke radio.
2. Aktifkan **VOX** di radio, atau pakai interface yang memicu PTT dari audio.
3. Kirim dari **Compose**, atau nyalakan **Start Beacon** di **Position** untuk beacon berkala.

**Menerima**

1. Buka **Monitor RX**, pilih mode yang sama, tekan **Start RX**.
2. Atur volume keluaran radio sampai spektrum menunjukkan puncak yang jelas.

Tips: uji dulu dengan **Loopback** untuk memastikan aplikasi berfungsi, lalu uji sambungan kabel dengan daya rendah sebelum dipakai sungguhan.

## Fitur Position

**Mengirim beacon**

1. Buka menu **Position**.
2. Isi **durasi** (jarak waktu antar beacon, dalam detik) dan **ID callsign** (maksimal 6 huruf/angka).
3. Tekan **Start Beacon**. Lokasi GPS Anda dikirim, lalu diulang sesuai durasi. Tekan tombol yang sama untuk berhenti.

**Melihat posisi teman**

1. Jalankan **Start RX** di Monitor RX agar beacon dari teman bisa diterima.
2. Di **Position**, pilih ID teman dari dropdown (hanya ID yang posisinya berhasil terbaca yang muncul).
3. Tekan **Start Tracking**. Radar menampilkan arah dan jarak ke teman Anda, dan ikut berputar saat HP Anda diputar.

**Uji tanpa radio:** centang **Loopback** di halaman Position, lalu Start Beacon. Beacon Anda sendiri akan terbaca di Monitor RX dan ID Anda muncul di dropdown.

**Catatan:**

- Beacon dan tracking **berhenti otomatis saat layar mati atau aplikasi ke background**, jadi biarkan aplikasi tetap tampil di layar.
- Pilih izin lokasi **Tepat (Precise)**, bukan Perkiraan.
- Bila ketinggian (altitude) tidak tersedia dari GPS, nilai yang dikirim adalah 0.

## Peringatan

- Pemakaian lewat radio harus mengikuti **aturan dan perizinan frekuensi** di negara Anda (misalnya wajib punya callsign/izin radio amatir).
- Beacon **menyiarkan lokasi Anda ke siapa pun** yang bisa mendengar frekuensi tersebut. Gunakan dengan bijak.
- Ini adalah proyek eksperimen dan tidak ada jaminan apa pun. Jangan jadikan satu-satunya alat komunikasi pada situasi yang menyangkut keselamatan.

## Download APK

- Click EmCommDat.apk: [Download](https://github.com/YD1RUH/EmCommDat/releases/download/Beta-V1.0.0/EmCommDat.apk) 

## Lisensi dan Kredit

- Lisensi proyek: (lisensi MIT)
- Antarmuka memakai [Dear ImGui](https://github.com/ocornut/imgui) (lisensi MIT).
