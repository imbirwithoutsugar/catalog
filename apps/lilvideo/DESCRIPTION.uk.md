# Li'l Video (C/C++)

Маленький відеоплеєр для [Лілки](https://github.com/and3rson/lilka). Дозволяє відтворювати відео зі звуком (MJPEG + AAC), спеціально підготовлене та складене в папку Video на SD-карті.

[Демо відео](https://youtu.be/Hq1uq1eL9xs)

## Збирання

Проєкт створено для [PlatformIO](https://platformio.org/). Клонуйте або скачайте цей репозиторій:

```
git clone https://github.com/noisedsn/lilvideo
```

Відкрийте у PlatformIO та натисніть Build. Або просто скачайте готовий файл [player.bin](https://github.com/noisedsn/lilvideo/blob/main/player.bin).

## Встановлення та додавання відео

В корені SD-карти створіть директорію Video. Помістіть в неї бінарник player.bin.

Відео повинні бути сконвертовані в два окремих файли: `288_30fps.mjpeg` та `44100.aac`. Для конвертації потрібен [ffmpeg](https://www.ffmpeg.org/):

```bash
ffmpeg -i input.mp4 -vf "fps=30,scale=-1:240:flags=lanczos,crop=288:in_h:(in_w-288)/2:0" -q:v 11 288_30fps.mjpeg

ffmpeg -i input.mp4 -ar 44100 -ac 1 -ab 36k -filter:a normalize -filter:a "volume=-6dB" 44100.aac
```

де input.mp4 — вхідний відеофайл. Параметром `-q:v 11` можна змінювати якість (2 — найкраща, 31 — найменший файл). Бітрейт аудіо змінюється параметром `-ab 36k` (не нижче 24k).

Структура папки Video:

```
Video/
├── Ролик 1
│   ├── 288_30fps.mjpeg
│   └── 44100.aac
├── Ролик 2
│   ├── 288_30fps.mjpeg
│   └── 44100.aac
└── player.bin
```

## Керування

Заходьте через Браузер SD-карти в папку Video та запускайте player.bin. Вибір відео — кнопки вгору/вниз, запуск — кнопка А.

Під час відтворення кнопками вгору/вниз регулюється гучність; кнопка А — закриє плеєр та поверне в Keira OS.
