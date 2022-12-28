# Setup

## Windows

- After Watchy has been connected to your PC, adjust the COM port settings:
  - Change the Port Settings -> Bits per Second to `115200`
- Open command prompt (or powershell) as Administrator
- Install ESPTool, if you don't have it
- Try running `python -m esptool --port COM# --baud 115200 flash_id`
  - Replace the # in `COM#` with your COM number, ie COM3, COM4, etc

If the `flash_id` command works, you should get a response similar to:

![](https://github.com/watchy-community/wiki/raw/main/docs/_media/esptool_windows_flashid.png)

