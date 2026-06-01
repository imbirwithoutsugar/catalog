# Li'l Video (C/C++)

Little video player for the [Lilka](https://github.com/and3rson/lilka) board that allows playback of specially prepared videos with sound (MJPEG + AAC) from the Video folder on the SD card.

[Demo video](https://youtu.be/Hq1uq1eL9xs)

## Building

The project is built with [PlatformIO](https://platformio.org/). Clone or download this repository:

```
git clone https://github.com/noisedsn/lilvideo
```

Open in PlatformIO and click Build. Or simply download the prebuilt [player.bin](https://github.com/noisedsn/lilvideo/blob/main/player.bin).

## Installation and Adding Videos

Create a Video directory in the root of the SD card. Place the player.bin binary inside it.

Videos must be converted into two separate files: `288_30fps.mjpeg` and `44100.aac`. You'll need [ffmpeg](https://www.ffmpeg.org/) for conversion:

```bash
ffmpeg -i input.mp4 -vf "fps=30,scale=-1:240:flags=lanczos,crop=288:in_h:(in_w-288)/2:0" -q:v 11 288_30fps.mjpeg

ffmpeg -i input.mp4 -ar 44100 -ac 1 -ab 36k -filter:a normalize -filter:a "volume=-6dB" 44100.aac
```

where input.mp4 is your source video file. Adjust video quality with `-q:v 11` (2 = best quality, 31 = smallest file). Audio bitrate can be changed with `-ab 36k` (don't go below 24k).

Video folder structure:

```
Video/
├── Video 1
│   ├── 288_30fps.mjpeg
│   └── 44100.aac
├── Video 2
│   ├── 288_30fps.mjpeg
│   └── 44100.aac
└── player.bin
```

## Controls

Navigate to the Video folder in the SD Card Browser and launch player.bin. Select a video using up/down buttons, press A to play.

During playback, up/down buttons control volume; pressing A closes the player and returns to Keira OS.
