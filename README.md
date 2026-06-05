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

4. **Motor Servo**

   * Kabel VCC (merah) servo dihubungkan ke pin 5V ESP32.
   * Kabel GND (cokelat/hitam) servo dihubungkan ke GND ESP32.
   * Kabel sinyal (oranye/kuning) servo dihubungkan ke GPIO 13 ESP32.

   Motor servo digunakan untuk membuka dan menutup mekanisme penyaluran pakan secara otomatis ketika pakan terdeteksi hampir habis.

5. **ESP32**

   * ESP32 berfungsi sebagai pengendali utama sistem, membaca data dari sensor, mengontrol aktuator, serta mengirimkan data suhu, kelembapan, dan level pakan ke aplikasi Blynk melalui koneksi WiFi.
