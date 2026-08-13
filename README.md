# bsp-ucm-imx8m-plus

Platform board support for the **CompuLab UCM-iMX8M-Plus** i.MX8M Plus SOM.

This is the SOM BSP: it installs the kernel modules the SOM's on-module and
i.MX8MP hardware uses (NXP CAAM crypto, SAI/ASRC + HDMI audio, HDMI CEC, the
HiFi4 DSP remoteproc, the on-module AT24 EEPROM, zram, device-mapper, NFS),
plus the i.MX SDMA firmware. The module list is the trimmed `lsmod` set
observed on a booted SOM (not the `kernel-modules` catch-all).

Carrier-specific support layers on top of this:

- **`bsp-iot-gate-imx8plus`** — IOT-GATE-iMX8PLUS gateway carrier (CAN, cellular
  modem, GPS, selects the `iot-gate-imx8plus` device tree).

## Using this extension

```yaml
default_target: ucm-imx8m-plus

extensions:
  avocado-bsp-ucm-imx8m-plus:
    source:
      type: package
      version: "*"

runtimes:
  som:
    extensions:
      - avocado-bsp-ucm-imx8m-plus
```

For the gateway, add `avocado-bsp-iot-gate-imx8plus` to the runtime alongside
this one.

## Notes

- No WiFi/BT modules are listed — none were loaded in the captured `lsmod`. Add
  the Intel AX (`iwlwifi`) / Marvell modules here once a card is exercised
  (firmware is already delivered via `MACHINE_FIRMWARE`).
