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
| se{$n}       | ? |
| circ{$n}     | Hot-water circulation pump #{$n} |

## Fields
The name of the fields are described with the dot-notation syntax. For the field `json_data['system']['L_ambient']` the field name in this documentation would be `system.L_ambient`.

### system.L_ambient

### system.L_errors

### system.L_usb_stick

### weather.L_temp

### weather.L_clouds

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

### hk{$n}.L_roomtemp_set

### hk{$n}.L_flowtemp_act

### hk{$n}.L_flowtemp_set

### hk{$n}.L_state

### hk{$n}.L_statetext

### hk{$n}.mode_auto

### hk{$n}.time_prg

### hk{$n}.temp_setback

### hk{$n}.temp_heat

### hk{$n}.temp_vacation

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

### ww{$n}.L_ontemp_act

### ww{$n}.L_offtemp_act

### ww{$n}.L_pump

### ww{$n}.L_state

### ww{$n}.L_statetext

### ww{$n}.time_prg

### ww{$n}.sensor_on

### ww{$n}.sensor_off

### ww{$n}.mode_auto

### ww{$n}.mode_dhw

### ww{$n}.heat_once

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
