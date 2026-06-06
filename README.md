### PETERNAKAN IOT ###

Sistem ini menggunakan mikrokontroler ESP32 sebagai pusat kendali yang terhubung dengan sensor DHT11, sensor ultrasonik HC-SR04, buzzer, dan motor servo. Setiap komponen dihubungkan ke pin GPIO ESP32 sesuai dengan fungsinya.

1. **Sensor DHT11**

   * Pin VCC DHT11 dihubungkan ke pin 3.3V ESP32.
   * Pin GND DHT11 dihubungkan ke GND ESP32.
   * Pin DATA DHT11 dihubungkan ke GPIO 4 ESP32.

   Sensor DHT11 berfungsi untuk mengukur suhu dan kelembapan lingkungan.

2. **Sensor Ultrasonik HC-SR04**

   * Pin VCC HC-SR04 dihubungkan ke pin 5V ESP32.
   * Pin GND HC-SR04 dihubungkan ke GND ESP32.
   * Pin TRIG dihubungkan ke GPIO 5 ESP32.
   * Pin ECHO dihubungkan ke GPIO 18 ESP32.

   Sensor ultrasonik digunakan untuk mengukur jarak antara sensor dan permukaan pakan guna mengetahui ketersediaan pakan dalam wadah.

3. **Buzzer**

   * Pin positif (+) buzzer dihubungkan ke GPIO 12 ESP32.
   * Pin negatif (-) buzzer dihubungkan ke GND ESP32.

   Buzzer berfungsi sebagai alarm ketika suhu lingkungan melebihi batas yang telah ditentukan.

   **Buzzer (Program 2)**
* Pin positif (+) buzzer dihubungkan ke GPIO 12 ESP32.
* Pin negatif (-) buzzer dihubungkan ke GND ESP32.
atau jika menggunakan modul buzzer:

* VCC → 3.3V/5V
* GND → GND
* SIG → GPIO 12

Pada Program 2, buzzer dikendalikan menggunakan logika digital HIGH dan LOW melalui fungsi digitalWrite(). Ketika suhu yang terdeteksi sensor DHT11 melebihi 32°C, ESP32 memberikan sinyal HIGH sehingga buzzer menyala. Sebaliknya, jika suhu berada pada kondisi normal, ESP32 memberikan sinyal LOW sehingga buzzer mati.

5. **Motor Servo**

   * Kabel VCC (merah) servo dihubungkan ke pin 5V ESP32.
   * Kabel GND (cokelat/hitam) servo dihubungkan ke GND ESP32.
   * Kabel sinyal (oranye/kuning) servo dihubungkan ke GPIO 13 ESP32.

   Motor servo digunakan untuk membuka dan menutup mekanisme penyaluran pakan secara otomatis ketika pakan terdeteksi hampir habis.

6. **ESP32**

   * ESP32 berfungsi sebagai pengendali utama sistem, membaca data dari sensor, mengontrol aktuator, serta mengirimkan data suhu, kelembapan, dan level pakan ke aplikasi Blynk melalui koneksi WiFi.

### RUMAH PINTAR ###

#### 1. Sensor LDR Digital

* Pin VCC sensor LDR dihubungkan ke pin 5V Arduino.
* Pin GND sensor LDR dihubungkan ke GND Arduino.
* Pin OUT sensor LDR dihubungkan ke pin digital 4 Arduino.

Sensor LDR digunakan untuk mendeteksi intensitas cahaya di lingkungan. Ketika kondisi lingkungan gelap, sensor akan memberikan sinyal HIGH sehingga lampu LED dinyalakan secara otomatis. Sebaliknya, ketika kondisi terang, LED akan dimatikan.

#### 2. LED

* Kaki anoda (+) LED dihubungkan ke pin digital 3 Arduino melalui resistor 220Ω.
* Kaki katoda (-) LED dihubungkan ke GND Arduino.

LED berfungsi sebagai simulasi lampu ruangan yang akan menyala saat kondisi gelap dan mati saat kondisi terang berdasarkan pembacaan sensor LDR.

#### 3. Sensor Hujan (Raindrop Sensor)

* Pin VCC sensor hujan dihubungkan ke pin 5V Arduino.
* Pin GND sensor hujan dihubungkan ke GND Arduino.
* Pin DO (Digital Output) sensor hujan dihubungkan ke pin digital 2 Arduino.

Sensor hujan digunakan untuk mendeteksi adanya air hujan. Ketika permukaan sensor terkena air, sensor akan memberikan sinyal LOW yang digunakan sebagai indikator kondisi hujan.

#### 4. Motor Servo

* Kabel VCC (merah) servo dihubungkan ke pin 5V Arduino.
* Kabel GND (cokelat/hitam) servo dihubungkan ke GND Arduino.
* Kabel sinyal (oranye/kuning) servo dihubungkan ke pin digital 9 Arduino.

Motor servo berfungsi sebagai simulasi atap atau jendela otomatis. Saat sensor hujan mendeteksi hujan, servo akan bergerak ke posisi 90° untuk menutup atap. Ketika cuaca cerah, servo akan kembali ke posisi 0° sehingga atap terbuka.

#### 5. Arduino Uno

Arduino Uno berfungsi sebagai pusat pengendali sistem. Arduino membaca data dari sensor LDR dan sensor hujan, kemudian mengendalikan LED dan motor servo sesuai kondisi lingkungan yang terdeteksi.

### KUALITAS LINGKUNGAN KEBAKARAN HUTAN ###

Sistem ini dapat diimplementasikan menggunakan NodeMCU ESP8266 maupun Arduino Uno sebagai mikrokontroler utama. Perbedaan utama hanya terletak pada jenis board dan pin yang digunakan, sedangkan fungsi setiap komponen tetap sama.

#### 1. Sensor DHT11

* VCC DHT11 dihubungkan ke pin 3.3V (NodeMCU) atau 5V (Arduino Uno).
* GND DHT11 dihubungkan ke GND mikrokontroler.
* Pin DATA DHT11 dihubungkan ke pin D1 (NodeMCU) atau pin digital 2 (Arduino Uno).

Sensor DHT11 berfungsi untuk mengukur suhu dan kelembapan lingkungan. Data suhu digunakan sebagai indikator peringatan dini apabila suhu melebihi batas yang telah ditentukan, yaitu 35°C.

#### 2. Sensor Api (Flame Sensor)

* VCC sensor api dihubungkan ke pin 3.3V/5V mikrokontroler.
* GND sensor api dihubungkan ke GND mikrokontroler.
* Pin DO (Digital Output) sensor api dihubungkan ke pin D2 (NodeMCU) atau pin digital 3 (Arduino Uno).

Sensor api digunakan untuk mendeteksi keberadaan nyala api. Ketika api terdeteksi, sensor akan mengirimkan sinyal LOW ke mikrokontroler sehingga sistem mengaktifkan alarm kebakaran.

#### 3. Buzzer

* Pin positif (+) buzzer dihubungkan ke pin D5 (NodeMCU) atau pin digital 4 (Arduino Uno).
* Pin negatif (-) buzzer dihubungkan ke GND mikrokontroler.

Buzzer berfungsi sebagai alarm suara yang akan aktif ketika sensor api mendeteksi adanya nyala api. Alarm digunakan untuk memberikan peringatan kepada pengguna mengenai kondisi darurat kebakaran.

#### 4. LED Merah

* Kaki anoda (+) LED merah dihubungkan ke pin D6 (NodeMCU) atau pin digital 5 (Arduino Uno) melalui resistor 220Ω.
* Kaki katoda (-) LED merah dihubungkan ke GND.

LED merah berfungsi sebagai indikator bahaya dan akan menyala ketika sistem mendeteksi adanya api.

#### 5. LED Kuning

* Kaki anoda (+) LED kuning dihubungkan ke pin D7 (NodeMCU) atau pin digital 6 (Arduino Uno) melalui resistor 220Ω.
* Kaki katoda (-) LED kuning dihubungkan ke GND.

LED kuning berfungsi sebagai indikator peringatan suhu tinggi ketika suhu lingkungan melebihi 35°C.

#### 6. LED Hijau

* Kaki anoda (+) LED hijau dihubungkan ke pin D8 (NodeMCU) atau pin digital 7 (Arduino Uno) melalui resistor 220Ω.
* Kaki katoda (-) LED hijau dihubungkan ke GND.

LED hijau berfungsi sebagai indikator kondisi aman ketika tidak ada api yang terdeteksi dan suhu masih berada dalam batas normal.

#### 7. Mikrokontroler (NodeMCU ESP8266 / Arduino Uno)

Mikrokontroler berfungsi sebagai pusat pengendali sistem. Perangkat ini membaca data dari sensor DHT11 dan flame sensor, kemudian mengendalikan LED indikator dan buzzer sesuai kondisi yang terdeteksi. Sistem akan memberikan informasi kondisi aman, peringatan suhu tinggi, maupun kondisi darurat kebakaran secara otomatis.

### Cara Kerja Sistem

* LED hijau menyala saat kondisi lingkungan aman.
* LED kuning menyala saat suhu melebihi 35°C sebagai peringatan dini.
* LED merah dan buzzer aktif saat sensor api mendeteksi adanya nyala api.
* Sistem melakukan pemantauan suhu, kelembapan, dan keberadaan api secara terus-menerus untuk memberikan peringatan secara real-time.

### PERTANIAN ###

Sistem ini menggunakan ESP32 sebagai mikrokontroler utama yang terhubung dengan sensor kelembapan tanah (soil moisture), sensor suhu dan kelembapan udara DHT11/DHT22, modul relay, pompa air, dan buzzer sebagai indikator peringatan.

#### 1. Sensor Soil Moisture

* Pin VCC sensor dihubungkan ke pin 3.3V ESP32.
* Pin GND sensor dihubungkan ke GND ESP32.
* Pin AO (Analog Output) sensor dihubungkan ke GPIO 34 ESP32.

Sensor soil moisture digunakan untuk mengukur tingkat kelembapan tanah. Nilai analog yang dihasilkan akan digunakan untuk menentukan apakah kondisi tanah kering, normal, atau basah.

#### 2. Sensor DHT11 / DHT22

* Pin VCC sensor dihubungkan ke pin 3.3V ESP32.
* Pin GND sensor dihubungkan ke GND ESP32.
* Pin DATA sensor dihubungkan ke GPIO 4 ESP32.

Sensor DHT11/DHT22 digunakan untuk mengukur suhu dan kelembapan udara di sekitar tanaman. Data ini digunakan sebagai parameter tambahan untuk menentukan kebutuhan penyiraman.

#### 3. Modul Relay

* Pin VCC relay dihubungkan ke pin 5V ESP32 atau sumber daya eksternal.
* Pin GND relay dihubungkan ke GND ESP32.
* Pin IN relay dihubungkan ke GPIO 26 ESP32.

Modul relay berfungsi sebagai sakelar elektronik yang menghubungkan dan memutus aliran listrik ke pompa air. Relay akan aktif ketika sistem mendeteksi kondisi tanah kering atau suhu udara tinggi dengan kelembapan udara rendah.

#### 4. Pompa Air

* Salah satu kabel pompa dihubungkan ke terminal NO (Normally Open) relay.
* Kabel lainnya dihubungkan ke sumber daya pompa.
* Terminal COM relay dihubungkan ke sumber tegangan pompa.

Pompa air berfungsi untuk menyiram tanaman secara otomatis ketika sistem mendeteksi bahwa tanaman membutuhkan air.

#### 5. Buzzer (Versi Program dengan Buzzer)

* Pin positif (+) buzzer dihubungkan ke GPIO 25 ESP32.
* Pin negatif (-) buzzer dihubungkan ke GND ESP32.

Buzzer digunakan sebagai indikator suara yang akan aktif bersamaan dengan pompa ketika sistem mendeteksi kondisi tanah kering atau udara panas dan kering. Buzzer akan mati ketika kondisi tanah sudah kembali basah.

#### 6. ESP32

ESP32 berfungsi sebagai pusat pengendali sistem. Mikrokontroler ini membaca data dari sensor soil moisture dan DHT11/DHT22, kemudian mengontrol relay, pompa air, dan buzzer sesuai kondisi lingkungan yang terdeteksi.

