# Setup

## Windows

- After Watchy has been connected to your PC, adjust the COM port settings:
  - Change the Port Settings -> Bits per Second to `115200`
- Open command prompt (or powershell) as Administrator
- Install ESPTool, if you don't have it
- Try running `python -m esptool --port COM# --chip esp32 flash_id`
  - Replace the # in `COM#` with your COM number, ie COM3, COM4, etc

If the `flash_id` command works, you should get a response similar to:

![](https://github.com/watchy-community/wiki/raw/main/docs/_media/esptool_windows_flashid.png)

- Once you can connect, run `python -m esptool --port COM# --chip esp32 erase_flash`
  - I ran this several times and it would fail with "Invalid head of packet (0x5B)..."
  - After letting the board sit a couple minutes, then the flash command ran without issue
- Download the MicroPython stable build from [here](https://micropython.org/download/esp32/).
- Flash MicroPython, run `python -m esptool --port COM# --chip esp32 write_flash -z 0x1000 C:\Users\yourname\Downloads\esp32-<builddate>-v<buildnumber>.bin`
- After MicroPython is flashed, you should be able to connect to the COM port using a serial emulator such as PuTTY.
  - Use baud 115200 to connect.

![](https://github.com/watchy-community/wiki/raw/main/docs/_media/esp32_windows_putty.png)
