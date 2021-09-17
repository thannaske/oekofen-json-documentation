# Ökofen JSON Documentation
This is an attempt to publicy document the fields and features of the Ökofen JSON API as it lacks documentation from the vendorside. Please feel free to file pull requests in case you have any additions or corrections. Most of the field descriptions are the result of trial and error.

## Accessing the API
After enabling the JSON API you need to configure the port and password within the heater's settings menu. Afterwards the JSON API should be exposed and reachable. You are able to access all metrics by hitting the `all` endpoint of the API.

```
http://{$ip}:{$port}/{$password}/all
```

## Used Abbreviations

| Abbreviation | Meaning |
| ------------ | ----------- |
| hk{$n}       | Heating circuit #{$n} |
| pu{$n}       | Buffer tank #{$n} |
| ww{$n}       | Hot-water circuit #{$n} |
| sk{$n}       | Solar thermal collector circuit #{$n} |
| pe{$n}       | Pellematic heater #{$n} |
| se{$n}       | Solar gain data #{$n} |
| circ{$n}     | Hot-water circulation pump #{$n} |

## Fields
The name of the fields are described with the dot-notation syntax. For the field `json_data['system']['L_ambient']` the field name in this documentation would be `system.L_ambient`.

### system.L_ambient
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
Temperature that was reported by the ambient temperature sensor. You'll need to multiply the value by the given factor to get the actual temperature in degree celsius als floating point value.

### system.L_errors
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| None | 1      | int  | -32768 to 32767 |

**Description (Help Wanted)**  
Unclear if it's an error counter that is equal to the amount of errors that were detected or if the integer value that is reported by the API represents a specific error code or bitflag.

### system.L_usb_stick
| Unit | Factor | Type | Range  |
| ---- | ------ | ---- | ------ |
| None | None   | bool | 0 or 1 |

**Description (Unsure)**  
Whether an USB-stick is connected to the Pellematic heater or not.

### weather.L_temp
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
Current temperature that was reported by the online weather service (see `weather.L_source` for information about the configured weather provider).

### weather.L_clouds
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| %    | 1      | int  | -32768 to 32767 |

**Description**  
How cloudy it currently should be according to the configured online weather service (see `weather.L_source` for information about the configured weather provider).

### weather.L_forecast_temp

### weather.L_forecast_clouds

### weather.L_forecast_today

### weather.L_starttime

### weather.L_endtime

### weather.L_source

### weather.L_location

### weather.cloud_limit

### weather.hysteresys

### weather.offtemp

### weather.lead

### weather.refresh

### weather.oekomode

### forecast.L_w_{0-24}

### hk{$n}.L_roomtemp_act
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
The current air temperature that was reported from a sensor that is installed inside a room that is heated by the used heating circuit. This value is zero (0) if there is no sensor installed for the given heating circuit.

### hk{$n}.L_roomtemp_set
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
The target air temperature that is set by the user for the selected heating circuit. This value can be ignored if there is no sensor installed for the given heating circuit.

### hk{$n}.L_flowtemp_act
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
The current flow temperature ("Vorlauftemperatur") of the heating system for the selected heating circuit.

### hk{$n}.L_flowtemp_set
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**  
The target flow temperature ("Vorlauftemperatur") of the heating system for the selected heating circuit.

### hk{$n}.L_state

### hk{$n}.L_statetext

### hk{$n}.remote_override
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| K    | 0.1    | int  | -32768 to 32767 |

**Description**
Influences the target room temperature. Basis is the datapoint temp_heat. This datapoint sets the wanted target to +X or -Y relative to the basis of temp_heat. For example, temp_heat is set to 22 degree and remote_override is set to +2 the real target for the heating system is 24 degree.

### hk{$n}.mode_auto
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| number | 1    | int  | 0 to 3          |

**Description**
The current mode of the heating circuit. 0: Off, 1: Auto, 2: Heating, 3: Setback

### hk{$n}.time_prg
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| number | 1    | int  | 0 to 1          |

**Description**
Defines the current active time program. Value 0 means "time program 1" and value 1 means "time program 2".

### hk{$n}.temp_setback
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**
The current setback ("Absenktemperatur") temperature. Relevant if either the time program defines that current the setback time is active or if the circuit is set to mode 3.

### hk{$n}.temp_heat
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**
The target temperature for the LED room thermostate. This temperature is the target if the remote is set to "middle" position. Relevant for the data point remote_override

### hk{$n}.temp_vacation
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**
The target temperature while the heating system is in vacation mode. The vacation mode is set for a period of time on the touch (remote) control panel or through the app.

### hk{$n}.name

### hk{$n}.oekomode

### pu{$n}.L_tpo_act

### pu{$n}.L_tpo_set

### pu{$n}.L_tpm_act

### pu{$n}.L_tpm_set

### pu{$n}.L_pump_release

### pu{$n}.L_pump

### pu{$n}.L_state

### pu{$n}.L_statetext

### pu{$n}.mintemp_off

### pu{$n}.mintemp_on

### pu{$n}.ext_mintemp_off

### pu{$n}.ext_mintemp_on

### ww{$n}.L_temp_set
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| °C   | 0.1    | int  | -32768 to 32767 |

**Description**
The target temperature of the hot water boiler.

### ww{$n}.L_ontemp_act

### ww{$n}.L_offtemp_act

### ww{$n}.L_pump
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| num  | 1      | int  | 0 or 1          |

**Description**
Indicates if the pump for the water heater is currently running or not. 0 means off, 1 means on.

### ww{$n}.L_state

### ww{$n}.L_statetext

### ww{$n}.time_prg
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| number | 1    | int  | 0 to 1          |

**Description**
Defines the current active time program. Value 0 means "time program 1" and value 1 means "time program 2".


### ww{$n}.sensor_on

### ww{$n}.sensor_off

### ww{$n}.mode_auto

### ww{$n}.mode_dhw

### ww{$n}.heat_once
| Unit | Factor | Type | Range           |
| ---- | ------ | ---- | --------------- |
| num  | 1      | int  | 0 or 1          |

**Description**
If the time program normally would not allow the system to heat the water boiler, this value overrides the behaviour and allows the water to be heated once. This mode is set back after the hot water boiler reaching the target temperature.

### ww{$n}.temp_min_set

### ww{$n}.temp_max_set

### ww{$n}.name

### ww{$n}.smartstart

### ww{$n}.use_boiler_heat

### ww{$n}.oekomode

### sk{$n}.L_koll_temp

### sk{$n}.L_spu

### sk{$n}.L_pump

### sk{$n}.L_state

### sk{$n}.L_statetext

### sk{$n}.mode

### sk{$n}.cooling

### sk{$n}.spu_max

### sk{$n}.name

### se{$n}.L_flow_temp

### se{$n}.L_ret_temp

### se{$n}.L_flow

### se{$n}.L_pwr

### se{$n}.L_counter

### se{$n}.L_total

### se{$n}.L_day

### se{$n}.L_yesterday

### circ{$n}.L_pump

### circ{$n}.L_ret_temp

### circ{$n}.L_release_temp

### circ{$n}.time_prg

### circ{$n}.mode

### circ{$n}.pump_release

### circ{$n}.return_set

### circ{$n}.name

### pe{$n}.L_temp_act

### pe{$n}.L_temp_set

### pe{$n}.L_ext_temp

### pe{$n}.L_frt_temp_act

### pe{$n}.L_frt_temp_set

### pe{$n}.L_br

### pe{$n}.L_ak

### pe{$n}.L_not

### pe{$n}.L_stb

### pe{$n}.L_modulation

### pe{$n}.L_uw_speed

### pe{$n}.L_state

### pe{$n}.L_statetext

### pe{$n}.L_type

### pe{$n}.L_starts

### pe{$n}.L_runtime

### pe{$n}.L_avg_runtime

### pe{$n}.L_uw_release

### pe{$n}.L_uw

### pe{$n}.mode

### error
