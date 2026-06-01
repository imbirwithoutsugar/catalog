# HC-SR04P — Distance Sensor for Lilka 📡

The app measures the distance to an object using the HC-SR04P ultrasonic sensor and displays the result in centimeters on the Lilka screen. [Video](https://youtu.be/VYKjBa4ukvo).

## Wiring 🔌

| Lilka  | HC-SR04P |
|--------|----------|
| 3.3V   | VCC      |
| GND    | GND      |
| Pin 12 | Trig     |
| Pin 13 | Echo     |

## How It Works 🦇

The sensor sends an ultrasonic pulse and waits for the echo — like a bat. The farther the object, the longer the sound travels. The app measures this time and converts it to centimeters using the speed of sound formula.

## Solving the Microseconds Problem 🔧

The HC-SR04P requires a trigger pulse of at least 10 microseconds. Lua on Lilka has no built-in microsecond delay. The solution is simple: `util.sleep(0.001)` gives a 1 ms delay — 100 times more than the minimum 10 µs required, and completely stable. To read the sensor response, a `while` loop with `util.time()` is used — the program continuously checks the pin state and measures the sound travel time. A 100 ms timeout prevents hanging if there is no object.

## Reading Stability 📊

Raw sensor data can jump due to noise and reflections. The app uses three protection mechanisms:

- **Averaging** — the last 8 readings are stored, and the screen shows their average. The number changes smoothly 〰️
- **Outlier filter** — if a new value differs from the current one by more than 40 cm, it is ignored. No jumps to 800 cm 🚫
- **Disappearance delay** — if the sensor doesn't detect an object, the app holds the last known value and only shows the connection guide after a prolonged absence of signal

## Scale 📏

The horizontal bar on screen is calibrated for a **0–50 cm** range — a convenient range for hand-distance work. If the distance is greater, the bar stays full but the number shows the real value.
