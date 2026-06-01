## Description
A simple app that displays the current time and temperature for a given city.

## Usage
Requires a `JSON` [parser](https://github.com/rxi/json.lua). It must be stored in the same directory as `weather.lua` and named `json.lua`. If you rename it, update the name in `weather.lua` in the `local json = require("$file_name")` field.

You need to register and generate an API key at [OpenWeather](https://home.openweathermap.org/api_keys).
In `weather.lua`, insert your key in the `api_key` field.
In `weather.lua`, set the city name in the `city_name` field.

The script updates data every 5 minutes. You can also refresh manually by pressing the `C` button.
