# Mpeg Video Streaming

Стрімінг відео на [Лілку](https://lilka.dev) через WiFi за допомогою MJPEG.

## Як це працює

```
┌─────────────┐    GStreamer     ┌──────────────┐    TCP/MJPEG    ┌─────────────┐
│   Screen    │ ──────────────►  │  stream.sh   │ ──────────────► │   Lilka     │
│  Capture    │   JPEG encode    │  (280x240)   │    WiFi         │  (ESP32-S3) │
└─────────────┘                  └──────────────┘                 └─────────────┘
```

1. **GStreamer** захоплює екран, масштабує до 280x240, кодує як MJPEG
2. **TCP stream** надсилає JPEG-кадри на Лілку через WiFi
3. **TJpgDec** бібліотека на ESP32-S3 декодує JPEG в реальному часі
4. **Arduino_GFX** рендерить кадри на ST7789 дисплей

## Вимоги до обладнання

- **Плата**: Lilka v2 (на базі ESP32-S3)
- **Дисплей**: 1.69" ST7789 TFT LCD (280x240 пікселів)
- **Операційна система**: KeiraOS (для налаштування WiFi)
- Linux (X11 або PipeWire) або macOS з GStreamer 1.0

## Встановлення GStreamer

**Linux (Debian/Ubuntu):**
```bash
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-base
```

**macOS:**
```bash
brew install gstreamer gst-plugins-good gst-plugins-base gst-plugins-bad
```

## Інструкція з налаштування

### 1. Налаштуйте WiFi в KeiraOS

Перейдіть до **Налаштування → WiFi** та підключіться до вашої мережі.

### 2. Зберіть та прошийте

```bash
git clone https://github.com/lilka-dev/mpeg_stream_player
cd mpeg_stream_player
pio run --target upload
```

**Або** скопіюйте `.pio/build/lilka_v2/firmware.bin` на SD-картку та завантажте через KeiraOS.

### 3. Запам'ятайте IP-адресу

Після підключення до WiFi на дисплеї з'явиться IP-адреса та порт (8090).

### 4. Запустіть стрімінг

```bash
./stream.sh <LILKA_IP>
```

## Використання

```bash
# Стрімінг з налаштуваннями за замовчуванням (15 FPS, якість 50)
./stream.sh 192.168.88.239

# Власні налаштування
./stream.sh <IP> [PORT] [FPS] [QUALITY]
```

## Продуктивність

| Якість | FPS | Пропускна здатність | Час декодування |
|--------|-----|---------------------|-----------------|
| 30 | 20-25 | ~200 kbps | ~15ms |
| 50 | 15-20 | ~350 kbps | ~20ms |
| 80 | 10-15 | ~600 kbps | ~30ms |

## Ліцензія

MIT License
