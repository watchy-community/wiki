# Troubleshooting

## OSError: [Errno 19] ENODEV

This error indicates one of the hardware libraries you are using is trying to
access something that doesn't exist.

For example, a user with v2 hardware trying to load code for v1 hardware:

```bash
Traceback (most recent call last):
  File "main.py", line 13, in <module>
  File "uasyncio/core.py", line 1, in run
  File "uasyncio/core.py", line 1, in run_until_complete
  File "uasyncio/core.py", line 1, in run_until_complete
  File "main.py", line 10, in main
  File "watchy.py", line 45, in __init__
  File "lib/ds3231.py", line 211, in alarm1
OSError: [Errno 19] ENODEV
MicroPython v1.19.1 on 2022-06-18; ESP32 module with ESP32
```

> In the above code, v2 hardware doesn't use the DS3231 RTC.

Or v1 hardware loading code for v2 hardware:

```bash
Traceback (most recent call last):
  File "main.py", line 15, in <module>
  File "uasyncio/core.py", line 1, in run
  File "uasyncio/core.py", line 1, in run_until_complete
  File "uasyncio/core.py", line 1, in run_until_complete
  File "main.py", line 12, in main
  File "src/watchy.py", line 88, in __init__
  File "src/watchy.py", line 112, in handle_wakeup
  File "lib/pcf8563.py", line 95, in datetime
  File "lib/pcf8563.py", line 88, in year
  File "lib/pcf8563.py", line 51, in __read_byte
OSError: [Errno 19] ENODEV
MicroPython v1.19.1 on 2022-06-18; ESP32 module with ESP32
```

> Here's the same issue, v1 hardware doesn't use the PCF8563 RTC.
