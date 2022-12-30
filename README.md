Davin Marselon/4.31.20.1.07/TE-3B

# Job 3 Topologi Jaringan Lokal dan WiFi
Pada jobsheet 3 terdapat 5 project yaitu scanning WiFi, WiFi station, WiFi auto-reconnect, hostname WiFi, dan mengirim data sensor ke database.

## Alat dan Bahan
  - ESP32
  - Arduino IDE (Terinstal ESP32)
  - Library DHT, Adafruit unified sensor, ESPAsyncWebServer dan AsyncTCP
  - Tool Arduino ESP32 Filesystem Uploader (SPIIFS)
  - Sensor DHT
  
## Instalasi ESP-32
  1. Buka Arduino IDE
     - Masuk ke Preferences
     - Isikan board url dengan link : https://dl.espressif.com/dl/package_esp32_index.json dan simpan
     - Buka Tools > Board > Boards Manager
     - Cari ESP32, by Espressif. Kemudian instal
     - Pilih flash mode DIO/QIU menyesuaikan
  2. Jalankan program .ino
  3. Jika terdapat error saat uploading, tekan dan tahan tombol Boot pada ESP32 saat upload, hingga Connecting selesai

## Instalasi DHT & Adafruit Libraries
  1. Buka Arduino IDE
  2. Buka Sketch > Include Library > Library Manager
  3. Cari DHT sensor library by Adafruit,k emudian instal. Atau dapat melalui link DHT Library dan upload pada libraries di direktori projek. Rename direktori menjadi DHT_sensor_library.
  4. Instal juga library Adafruit unified sensor by Adafruit. Atau dapat melalui link Adafruit Sensor dan upload pada libraries di direktori projek. Rename direktori menjadi Adafruit_Unified_Sensor.

## Instalasi ESPAsyncWebServer dan AsyncTCP
  1. Download melalui link ESPAsyncWebServer dan AsyncTCP.
  2. Buka Arduino IDE
  3. Buka Sketch > Include Library > Add .ZIP Library.
  4. Cari kedua library kemudian install.
  5. Atau ekstrak dan upload pada libraries di direktori projek. Rename direktori menjadi ESPAsyncWebServer dan AsyncTCP.

## Instalasi Tool Arduino ESP32 Filesystem Uploader (SPIIFS)
  1. Download ESP32FS melalui link ESP32FS.
  2. Ekstrak dan upload pada direktori projek (sketchbook), contoh <Sketchbook-location>/tools/ESP32FS/tool/esp32fs.jar.

## Project A - WiFi Modes and Scanning
### Rangkaian & Instalasi
  1. Siapkan ESP32 dan hubungkan ke Arduino IDE.
  2. Download dan jalankan kode dari source code sesuai project.
  
Keluaran
  
<img src="https://user-images.githubusercontent.com/49542850/209751678-d4ecb7f4-fd5e-45da-9896-5907d4c60878.png" width=600px>
<img src="" width=600px>

WiFi adapter pada ESP32 yang diset sebagai station akan melakukan scanning jaringan WiFi disekitar. Radius scan dan kekuatan sinyal dapat bervariasi untuk setiap modul mulai dari 1-10 meter. Pada kasus ini, saya menggunakan ESP32U Dev4 + Antena 3dB, sehingga sinyal yang didapat lebih bagus dibandingkan adapter ESP32 standar dengan antena internal.
  
ESP akan melakukan scanning dan memunculkan hasilnya pada serial monitor jaringan WiFi beserta kekuatan sinyal yang didapat. Jika tidak ada jaringan maka akan tertulis "No Networks Found". Scanning akan diulang setiap 5 detik karena terdapat delay(5000) dan lebih baik tidak dilakukan terlalu cepat (spam).
