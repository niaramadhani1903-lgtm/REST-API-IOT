REST API IoT – Monitoring Suhu dan Kelembapan

Deskripsi Proyek
Proyek ini merupakan implementasi REST API berbasis Node-RED untuk memantau suhu dan kelembapan menggunakan simulasi sensor ESP32 melalui protokol MQTT. Data sensor ditampilkan pada dashboard berbasis HTML, CSS, dan JavaScript.

Fitur Utama
1. Monitoring suhu dan kelembapan secara real-time.
2. REST API untuk mengambil data sensor.
3. Endpoint PUT `/api/threshold` untuk mengatur batas suhu.
4. Notifikasi melalui Debug Node-RED ketika suhu melewati batas.
5. Grafik real-time menggunakan Chart.js.
6. Autentikasi API Key melalui header `X-API-Key` pada endpoint threshold.
7. WebSocket untuk menerima pembaruan data sensor.
8. Penyimpanan riwayat sensor menggunakan database SQLite.
9. Kontrol lampu melalui dashboard.

Teknologi yang Digunakan
- Node.js
- Node-RED
- MQTT Mosquitto
- Python
- HTML, CSS, dan JavaScript
- Chart.js
- WebSocket
- SQLite

Struktur File
- `dashboard.html` – Tampilan dashboard monitoring.
- `simulasi_esp32.py` – Program simulasi sensor ESP32.
- `flows.json` – Flow Node-RED.
- `sensor_iot.db` – Database penyimpanan riwayat sensor.

Cara Menjalankan
1. Pastikan Node.js, Node-RED, Python, dan Mosquitto sudah terpasang.
2. Jalankan layanan Mosquitto.
3. Jalankan Node-RED.
4. Import file `flows.json` ke Node-RED.
5. Pastikan lokasi database SQLite pada konfigurasi Node-RED sudah sesuai.
6. Instal library Python dengan perintah:

   `pip install paho-mqtt`

7. Jalankan simulasi sensor:

   `python simulasi_esp32.py`

8. Buka file `dashboard.html` melalui browser.


Endpoint API

| Method | Endpoint | Fungsi |
|---|---|---|
| GET | `/api/suhu` | Mengambil data sensor |
| GET | `/api/history` | Mengambil riwayat sensor |
| PUT | `/api/threshold` | Mengubah batas suhu |
| POST | `/api/kontrol` | Mengontrol lampu |

Contoh Pengaturan Threshold
Endpoint: `PUT /api/threshold`

Header:
- `Content-Type: application/json`
- `X-API-Key: NIA_IOT_2026`

Body:
```json
{
  "threshold": 35
}
```

Catatan: API Key tersebut merupakan kunci demonstrasi untuk praktikum, bukan untuk penggunaan produksi. Autentikasi API Key diterapkan pada endpoint `/api/threshold`.

WebSocket
WebSocket digunakan untuk mengirim pembaruan data sensor secara langsung melalui alamat:

`ws://127.0.0.1:1880/ws/sensor`

Dashboard juga masih menggunakan REST API sebagai mekanisme pendukung untuk mengambil data tertentu.

Database
Data riwayat sensor disimpan dalam SQLite pada tabel `sensor_history`, dengan kolom:
- `id`
- `suhu`
- `kelembaban`
- `timestamp`
- `received`

Pengembang
Proyek ini dibuat untuk memenuhi tugas praktikum REST API dan Internet of Things (IoT).