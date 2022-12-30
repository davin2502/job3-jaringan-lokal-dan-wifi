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

WiFi adapter pada ESP32 yang diset sebagai station akan melakukan scanning jaringan WiFi disekitar. Radius scan dan kekuatan sinyal dapat bervariasi untuk setiap modul mulai dari 1-10 meter. Pada kasus ini, saya menggunakan ESP32U Dev4 + Antena 3dB, sehingga sinyal yang didapat lebih bagus dibandingkan adapter ESP32 standar dengan antena internal.
  
ESP akan melakukan scanning dan memunculkan hasilnya pada serial monitor jaringan WiFi beserta kekuatan sinyal yang didapat. Jika tidak ada jaringan maka akan tertulis "No Networks Found". Scanning akan diulang setiap 5 detik karena terdapat delay(5000) dan lebih baik tidak dilakukan terlalu cepat (spam).
  
## Project B - Menghubungkan ESP32 dengan jaringan WiFi (station mode)
### Rangkaian & Instalasi
  1. Siapkan ESP32 dan hubungkan ke Arduino IDE.
  2. Download dan jalankan kode dari source code sesuai project.
  
  Keluaran

  <img src="https://user-images.githubusercontent.com/49542850/209751686-633fa28c-7613-41eb-8faf-0c9a9c9a6895.png" width=600px>

ESP bertindak sebagai station atau client dari sebuah jaringan/AP yang ada. Sehingga SSID dan password dari jaringan harus diketahui agar ESP dapat terhubung. Pada kode dilakukan looping untuk pengecekan apakah ESP sudah terkoneksi dengan jaringan. Bila sudah, maka akan muncul IP address yang didapatkan ESP, pada contoh yaitu 192.168.108.88.

## Project C - Menghubungkan Kembali (Re-connect) ESP32 dengan Jaringan Wi-Fi
### Rangkaian & Instalasi
  1. Siapkan ESP32 dan hubungkan ke Arduino IDE.
  2. Download dan jalankan kode dari source code sesuai project.
  
  Keluaran

  <img src="https://user-images.githubusercontent.com/49542850/209751687-e587400d-f344-44f2-9af5-bb3d57ce774a.png" width=600px>
  
Sistem auto reconnect adalah pengembangan dari sistem konek pada sebelumnya. Perbedaanya terdapat perkondisian untuk mendeteksi jaringan di dalam fungsi loop. Setelah dideteksi ESP terputus dari jaringan, maka setiap beberapa "jeda waktu", maka ESP akan mencoba melakukan konek ulang ke jaringan yang sebelumnya telah terhubung, dalam hal ini telah ditulis SSID dan password pada tahap sebelumnya.

## Project D - Mengganti Hostname ESP32
### Rangkaian & Instalasi
  1. Siapkan ESP32 dan hubungkan ke Arduino IDE.
  2. Download dan jalankan kode dari source code sesuai project.
  
  Keluaran

  <img src="https://user-images.githubusercontent.com/49542850/209751688-e2743c94-5c77-405e-aedf-d990f45fa9d2.jpeg" width=600px>

Hostname merupakan identitas perangkat yang dipakai oleh ESP32. Hostname akan muncul ketika ESP terhubung ke suatu jaringan, maka pemilik jaringan tersebut (AP) dapat melihat identitas dari perangkat yang terhubung, dalam hal ini adalah hostname dari ESP. ESP harus mendeklarasikan hostnamenya dengan perintah WiFi.setHostname() sebelum melakukan koneksi ke jaringan.

## Project E - Mengirim Data Sensor ke Database
### Rangkaian & Instalasi
  1. Siapkan ESP32 dan hubungkan ke Arduino IDE.
  2. Buat rangkaian berikut.
  
  <img src="https://camo.githubusercontent.com/aeb8b907f26bfb37d2f21b09f8a41f684a1bc1096c1a1041af71357f6c697b2a/68747470733a2f2f63646e2e646973636f72646170702e636f6d2f6174746163686d656e74732f313034333436323531393333363939363839342f313035313434313135343130323637333436392f422e5f52616e676b6169616e5f4448542e706e67" width=600px>

  3. Download dan jalankan kode dari source code sesuai project.
  4. Pastikan library DHT dan Adafruit sudah terinstal.
  5. Pastikan library AsyncTCP dan ESPAsyncWebServer sudah terinstal.
  
  Keluaran

  <img src="https://user-images.githubusercontent.com/49542850/209751690-5897da3c-f8aa-4e34-90ed-a9ca76194402.png" width=600px>
  <img src="https://user-images.githubusercontent.com/49542850/209751694-7465347a-596b-48b6-88a8-8efaabae92a9.png" width=600px>
  
ESP akan melakukan inisialisasi awal untuk WiFi, dht, serial monitor, serta web server. ESP akan melakukan hosting web server menggunakan localhost sebagai servernya. Web server ini dapat diakses menggunakan IP address dari ESP setelah terhubung dengan jaringan WiFi.

ESP akan membaca data dari sensor berupa suhu dan kelembaban yang kemudian disimpan dalam variabel. Data dari variabel kemudian dikirim melalui link yang sudah disediakan menggunakan method POST via javascript. Hasil dari sensor kemudian akan muncul pada web sebagaimana contoh.

## Tugas
  1. Pastikan library SPIIFS, AsyncTCP dan ESPAsyncWebServer sudah terinstal.
  2. Buka program pada source code. Serta siapkan folder data di folder program (.ino).
  3. Pastikan file web server (html dan js) sudah siap.
  4. Pilih Tools > ESP32 Sketch Data Upload untuk mengupload folder data. Jika terjadi connecting, maka tekan tombol boot pada board.
  5. Upload program seperti biasa.
  
Pada tahap awal, ESP akan membuat beberapa file teks untuk menyimpan data berupa ssid, password, IP, dan gateway. Kemudian ESP akan mengubah mode jaringan menjadi AP agar user dapat terkoneksi dan melakukan konfigurasi. ESP juga memulai service web server nya pada alamat localnya. Tampilan dari web server dibuat pada file terpisah yaitu html, js, dan css seperti web pada umumnya. File tersebut diimport pada ESP untuk dilakukan routing ke address.

Pada tampilan halaman awal akan disajikan kolom SSID, Password, IP, dan Gateway. Secara default, bila hanya mengisi SSID dan Password, maka konfigurasi akan berupa DHCP sedangkan jika diisi IP maupun gateway akan menggunakan alamat tersebut (statik).

Setelah melakukan submit, ESP akan menyimpan data pada form dan melakukan koneksi ke jaringan tersebut. Jika jaringan terputus, maka user dapat melakukan restart dan konfigurasi ulang ESP. Sehingga user tidak perlu mengubah koding dan hanya perlu mengakses IP address dari ESP saja.
  
  ![1](https://user-images.githubusercontent.com/118702169/210025541-9a81d24a-a18c-4b88-a145-b8a3ea31b1ef.png)
  ![2](https://user-images.githubusercontent.com/118702169/210025543-74591a3a-6e17-4c14-a370-66672e4019d2.png)
  ![3](https://user-images.githubusercontent.com/118702169/210025545-0a49156f-0547-4e26-913d-1b402d1da420.png)
  ![4](https://user-images.githubusercontent.com/118702169/210025550-942b290c-8379-4633-a16d-f21acd13c152.png)

    <img src="https://user-images.githubusercontent.com/49542850/209770990-41050f3a-48ef-459f-b0f3-0883ce2f3bab.png" width=600px>
    <img src="https://user-images.githubusercontent.com/49542850/209770995-4659bd1e-d14f-4a07-8e4f-89b2efee8040.png" width=600px>
    <img src="https://user-images.githubusercontent.com/49542850/209770996-6436cddc-9382-4621-bb08-e0b1676be455.png" width=600px>
    <img src="https://user-images.githubusercontent.com/49542850/209770997-eba93b10-d34d-4cf5-8336-41cfd63cfba4.png" width=600px>

## Kesimpulan
  - ESP32 memiliki adapter WiFi internal yang dapat digunakan sebagaimana access point, yaitu sebagai AP, sebagai station, atau hybrid.
  - Koneksi WiFi pada ESP dapat dilakukan auto reconnecting dengan mengecek status boolean WL_CONNECTED dan menambahkan perintah WiFi.reconnect()
  - Nama dari ESP (hostname) dapat diganti dengan perintah WiFi.setHostname() untuk mempermudah dalam membedakan ESP pada jaringan.
  - Untuk membuat suatu web server, ESP membutuhkan library salah satunya adalah AsyncTCP dan ESPWebServerAsync. Library ini memungkinkan ESP melakukan hosting pada local address. Kelemahanya adalah kode html, css, maupun javascript akan menumpuk dalam kodingan ESP.ino.
  - Untuk mengirimkan data dari variabel menuju web server, dapat digunakan salah satu metode yaitu POST melalui javascript.
  - Tool SPIIFS memungkinkan user untuk mengimport file eksternal ke dalam ESP, sehingga mempermudah dalam pembuatan contohnya web server.
  - Dalam pemrograman, fleksibilitas dan user experience adalah hal utama, sehingga pada tugas dibuat suatu sistem WiFi client yang dapat dihubungkan ke AP manapun tanpa perlu mengubah kode di dalamnya (tidak hard coded).

