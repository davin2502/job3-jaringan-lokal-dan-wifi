Nama : Davin Marselon
NIM : 4.31.20.1.07
Kelas : TE-3B

Jobsheet 3 Topologi Jaringan Lokal dan WiFi
Pada jobsheet 3 terdapat 5 project yaitu scanning WiFi, WiFi station, WiFi auto-reconnect, hostname WiFi, dan mengirim data sensor ke database.

Alat dan Bahan
ESP32
Arduino IDE (Terinstal ESP32)
Library DHT, Adafruit unified sensor, ESPAsyncWebServer dan AsyncTCP
Tool Arduino ESP32 Filesystem Uploader (SPIIFS)
Sensor DHT
Instalasi ESP-32
Buka Arduino IDE
Masuk ke Preferences
Isikan board url dengan link : https://dl.espressif.com/dl/package_esp32_index.json dan simpan
Buka Tools > Board > Boards Manager
Cari ESP32, by Espressif. Kemudian instal
Pilih flash mode DIO/QIU menyesuaikan
Jalankan program .ino
Jika terdapat error saat uploading, tekan dan tahan tombol Boot pada ESP32 saat upload, hingga Connecting selesai
Nb. Proses instalasi dapat dilewati jika Arduino IDE sudah terintegrasi dengan ESP32. Atau download libraries dan upload pada direktori projek.

Instalasi DHT & Adafruit Libraries
Buka Arduino IDE
Buka Sketch > Include Library > Library Manager
Cari DHT sensor library by Adafruit. Kemudian instal.
Atau dapat melalui link DHT Library dan upload pada libraries di direktori projek. Rename direktori menjadi DHT_sensor_library.
Instal juga library Adafruit unified sensor by Adafruit
Atau dapat melalui link Adafruit Sensor dan upload pada libraries di direktori projek. Rename direktori menjadi Adafruit_Unified_Sensor.
Nb. Proses instalasi dapat dilewati jika libraries telah diinstal. Atau download libraries dan upload pada direktori projek.

Instalasi ESPAsyncWebServer dan AsyncTCP
Download melalui link ESPAsyncWebServer dan AsyncTCP.
Buka Arduino IDE
Buka Sketch > Include Library > Add .ZIP Library.
Cari kedua library kemudian install.
Atau ekstrak dan upload pada libraries di direktori projek. Rename direktori menjadi ESPAsyncWebServer dan AsyncTCP.
Nb. Proses instalasi dapat dilewati jika libraries telah diinstal. Atau download libraries dan upload pada direktori projek.

Instalasi Tool Arduino ESP32 Filesystem Uploader (SPIIFS)
Download ESP32FS melalui link ESP32FS.
Ekstrak dan upload pada direktori projek (sketchbook), contoh <Sketchbook-location>/tools/ESP32FS/tool/esp32fs.jar.
