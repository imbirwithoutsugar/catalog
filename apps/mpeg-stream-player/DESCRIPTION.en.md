# Mpeg Video Streaming

Stream your computer screen to the [Lilka](https://lilka.dev) device over WiFi using MJPEG.

## How It Works

```
┌─────────────┐    GStreamer     ┌──────────────┐    TCP/MJPEG    ┌─────────────┐
│   Screen    │ ──────────────►  │  stream.sh   │ ──────────────► │   Lilka     │
│  Capture    │   JPEG encode    │  (280x240)   │    WiFi         │  (ESP32-S3) │
└─────────────┘                  └──────────────┘                 └─────────────┘
```

1. **GStreamer** captures the screen, scales to 280x240, encodes as MJPEG
2. **TCP stream** sends JPEG frames to Lilka over WiFi
3. **TJpgDec** library on ESP32-S3 decodes JPEG in real time
4. **Arduino_GFX** renders frames on the ST7789 display

## Hardware Requirements

- **Board**: Lilka v2 (ESP32-S3 based)
- **Display**: 1.69" ST7789 TFT LCD (280x240 pixels)
- **OS**: KeiraOS (for WiFi configuration)
- Linux (X11 or PipeWire) or macOS with GStreamer 1.0

## Installing GStreamer

**Linux (Debian/Ubuntu):**
```bash
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-base
```

**macOS:**
```bash
brew install gstreamer gst-plugins-good gst-plugins-base gst-plugins-bad
```

## Setup Instructions

### 1. Configure WiFi in KeiraOS

Go to **Settings → WiFi** and connect to your network.

### 2. Build and Flash

```bash
git clone https://github.com/lilka-dev/mpeg_stream_player
cd mpeg_stream_player
pio run --target upload
```

**Or** copy `.pio/build/lilka_v2/firmware.bin` to the SD card and flash via KeiraOS.

### 3. Note the IP Address

After connecting to WiFi, the display will show the IP address and port (8090).

### 4. Start Streaming

```bash
./stream.sh <LILKA_IP>
```

## Usage

```bash
# Stream with default settings (15 FPS, quality 50)
./stream.sh 192.168.88.239

# Custom settings
./stream.sh <IP> [PORT] [FPS] [QUALITY]
```

## Performance

| Quality | FPS | Bandwidth | Decode time |
|---------|-----|-----------|-------------|
| 30 | 20-25 | ~200 kbps | ~15ms |
| 50 | 15-20 | ~350 kbps | ~20ms |
| 80 | 10-15 | ~600 kbps | ~30ms |

## License

MIT License
