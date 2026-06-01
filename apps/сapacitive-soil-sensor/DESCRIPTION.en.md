# Soil Moisture Sensor on Lilka 🌱

The app measures soil moisture using the Capacitive Soil Moisture Sensor v1.2 and displays the result as a percentage on the Lilka screen.

## Two Types of Soil Moisture Sensors

Resistive sensors (e.g. YL-69 or FC-28) measure resistance between metal probes — they are cheap but rust within weeks. Capacitive sensors (e.g. Capacitive Soil Moisture Sensor v1.2) measure the dielectric permittivity of the soil without direct metal-to-moisture contact — so they last much longer 🌿

## How It Works

The sensor returns an ADC value from 0 to 4095. Capacitive sensors have inverted logic: the **lower** the number, the **higher** the moisture. Conversion formula:

moisture (%) = (DRY - ADC) × 100 / (DRY - WET)

where `DRY` = ADC value in dry air (0%), `WET` = ADC value in water (100%).

## Calibration

The `DRY` and `WET` values are calibrated for each individual sensor. Hold the sensor in air and note the ADC value → put it in the `DRY` constant. Submerge in water for `WET`.

## Wiring 🔌

| Lilka  | Sensor v1.2 |
|--------|-------------|
| 3.3V   | VCC         |
| GND    | GND         |
| Pin 13 | AOUT        |

Pin 13 is chosen intentionally — only pins 12, 13 and 14 on Lilka support analog reading via ADC.

## Reading Stability 📊

The app averages the last 8 readings — values change smoothly without sudden jumps.
