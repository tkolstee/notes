Download and install Thonny IDE

In status bar select device to use as interpreter. This provides a REPL

To run editor content on device, use `%Run -c $EDITOR_CONTENT`

## Pin Control
```python
import machine
import utime

handle = machine.Pin('LED', machine.Pin.OUT)
for i in range(10):
    handle.toggle()
    utime.sleep(0.25)

handle.value(0)
```

## WLAN (Pico W)
Adapted from [GitHub pi3g/pico-w](https://github.com/pi3g/pico-w/blob/main/MicroPython/I%20Pico%20W%20LED%20web%20server/main.py)

```python
import rp2
import network
import ubinascii
import machine
import utime

ssid = 'my_ssid'
wifipw = 'my_network_password'

rp2.country('US')
wlan = network.WLAN(network.STA_IF)
wlan.active(True)

wlan.connect(ssid, wifipw)

timeout = 10
while timeout > 0:
    if wlan.status() < 0 or wlan.status() >= 3:
        break
    timeout -= 1
    print("Waiting for connection...")
    utime.sleep(1)

def blink_onboard_led(num_blinks):
    led = machine.Pin('LED', machine.Pin.OUT)
    for i in range(num_blinks):
        led.on()
        utime.sleep(.2)
        led.off()
        utime.sleep(.2)
    
# Handle connection error
# Error meanings
# 0  Link Down
# 1  Link Join
# 2  Link NoIp
# 3  Link Up
# -1 Link Fail
# -2 Link NoNet
# -3 Link BadAuth


mac = ubinascii.hexlify(network.WLAN().config('mac'), ':').decode()
print(f'mac = {mac}')
for val in [ 'channel', 'essid', 'txpower' ]:
    print(f"{val} = {wlan.config(val)}")
    
wlan_status = wlan.status()
blink_onboard_led(wlan_status)

if wlan_status != 3:
    raise RuntimeError('Wi-Fi Connection failed!')
else:
    print('Connected')
    status = wlan.ifconfig()
    print(f'ip = {status[0]}')
```
