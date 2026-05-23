# Implementasi Mikrokontroler dengan Bluetooth HC-05

## 📌 Deskripsi Proyek
Proyek ini merupakan implementasi sistem kendali nirkabel berbasis **Bluetooth HC-05** menggunakan mikrokontroler **ESP32**. Sistem dirancang untuk mengontrol LED melalui koneksi Bluetooth menggunakan smartphone Android secara real-time.

ESP32 berfungsi sebagai pengendali utama yang menerima data dari perangkat Android melalui komunikasi Bluetooth serial. Ketika perintah diterima, ESP32 akan mengontrol kondisi LED sebagai output. Proyek ini membantu memahami konsep dasar komunikasi wireless, kontrol perangkat jarak dekat, serta integrasi antara mikrokontroler dan perangkat mobile pada embedded system.

---

## 🖼️ Dokumentasi Sistem

<img width="205" height="140" alt="image" src="https://github.com/user-attachments/assets/0953bf12-b8a1-4d42-948e-85998a9b6948" />

---

## 🛠️ Alat dan Komponen
- ESP32 Dev Module  
- Modul Bluetooth HC-05  
- LED  
- Resistor  
- Breadboard  
- Kabel Jumper  
- Smartphone Android  
- Kabel USB Data  

---

## 🔌 Konfigurasi Pin

| Komponen | ESP32 |
|-----------|--------|
| LED Anoda (+) | GPIO4 |
| LED Katoda (-) | Resistor → GND |
| HC-05 VCC | 5V |
| HC-05 GND | GND |
| HC-05 TX | RX ESP32 |
| HC-05 RX | TX ESP32 |

---

## ⚙️ Langkah Implementasi

1. Siapkan seluruh alat dan komponen.  
2. Rangkai komponen sesuai skema rangkaian.  
3. Sambungkan kaki anoda LED ke GPIO4 pada ESP32.  
4. Sambungkan kaki katoda LED ke resistor lalu ke GND ESP32.  
5. Hubungkan modul Bluetooth HC-05 ke ESP32.  
6. Buka **Arduino IDE**.  
7. Install library:
   - `BluetoothSerial`

8. Pilih board:
   `Tools → Board → ESP32 Arduino → ESP32 Dev Module`

9. Pilih port ESP32:
   `Tools → Port → COM ESP32`

10. Gunakan nama Bluetooth:
   `ESP32_LED`

11. Upload program ke ESP32 hingga muncul status **Done Uploading**.

---

## 💻 Program Arduino

```cpp
#include "BluetoothSerial.h"

BluetoothSerial SerialBT;

// Pin LED
const int ledPin = 4;

void setup() {
  Serial.begin(115200);

  // Memulai Bluetooth dengan nama ESP32_LED
  SerialBT.begin("ESP32_LED");

  pinMode(ledPin, OUTPUT);

  Serial.println("Bluetooth siap digunakan...");
}

void loop() {

  // Cek apakah ada data Bluetooth masuk
  if (SerialBT.available()) {

    char data = SerialBT.read();

    // Jika menerima karakter '1'
    if (data == '1') {
      digitalWrite(ledPin, HIGH);
      Serial.println("LED ON");
    }

    // Jika menerima karakter '0'
    else if (data == '0') {
      digitalWrite(ledPin, LOW);
      Serial.println("LED OFF");
    }
  }
}
```

---

## 🔍 Cara Kerja Sistem
- ESP32 membuat koneksi Bluetooth dengan nama **ESP32_LED**.  
- Smartphone Android dapat terhubung ke ESP32 menggunakan aplikasi Bluetooth Terminal atau aplikasi kontrol Bluetooth lainnya.  
- Ketika pengguna mengirim:
  - Karakter `1` → LED menyala  
  - Karakter `0` → LED mati  

- ESP32 membaca data yang diterima melalui Bluetooth Serial dan mengontrol LED sesuai perintah yang diberikan.

---

## 📊 Hasil Pengujian
Implementasi mikrokontroler dengan Bluetooth HC-05 berhasil diterapkan sebagai sistem kendali nirkabel sederhana yang efektif dan ekonomis. Sistem mampu menghubungkan ESP32 dengan smartphone Android secara real-time dengan respons yang cepat dan mudah digunakan.

Selain untuk pengendalian LED, sistem ini dapat dikembangkan lebih lanjut untuk mengontrol berbagai perangkat seperti motor, relay, sensor, maupun sistem otomasi lainnya. Meskipun jangkauan Bluetooth terbatas dan sensitif terhadap penghalang, teknologi ini tetap fleksibel dan praktis untuk diterapkan pada bidang edukasi, otomasi rumah, dan robotika.

---

## 💻 Teknologi yang Digunakan
- Arduino IDE  
- ESP32  
- Bluetooth HC-05  
- Bluetooth Serial Communication  
- Embedded System Programming  

---

## 📚 Tujuan Pembelajaran
- Memahami komunikasi Bluetooth pada ESP32  
- Mengontrol output digital secara wireless  
- Menghubungkan mikrokontroler dengan smartphone Android  
- Mengimplementasikan sistem kendali nirkabel sederhana  

---

## 👨‍💻 Author
**Puspita**  
Computer Engineering Student — IPB University
