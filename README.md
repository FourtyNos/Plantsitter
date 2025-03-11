# Plantsitter

Welcome,
This is an code for a D1mini which measure how moist the soil is. 

This integrates with Homeassistent and also has the atributes set to use for example HACS integration.

also Designed a Custom Case so it a little more childproof and more pretty.

[Esp-Plantsitter on Printables](https://www.printables.com/model/1219805)

![Cover](esp-plantsitter_Cover.png#)

#Code
```
# Sensoren
sensor:

# Wetness
- platform: adc
  pin:
    number: A0
    allow_other_uses: true
  id: "adcMoisture"
  accuracy_decimals: 2
  unit_of_measurement: '%'
  icon: "mdi:flower-outline"
  device_class: "moisture"
  state_class: "measurement"
  filters:
    - calibrate_linear:
      - 0.30273 -> 100.0 # <--- Those 2 values has to be set yourself. (0.6 and 0.3)
      - 0.65137 -> 0     # <--- you need to calibrate it with your own sensor (completly dry and completly wet)
  name: "Soil Moisture"
  update_interval: 30s
  
# Voltage
- platform: adc
  pin:
    number: A0
    allow_other_uses: true
  id: "adcRaw_Sensor_Data"
  accuracy_decimals: 5
  name: "Sensor Voltage"
  update_interval: 30s

# Wifilevel
- platform: wifi_signal
  name: "WiFi Signal"
  update_interval: 30s

```
