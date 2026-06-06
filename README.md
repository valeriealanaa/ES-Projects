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

### Rumah Pintar ###

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

