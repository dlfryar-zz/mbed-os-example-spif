# Getting started with spif-driver on Mbed OS

This guide reviews the steps required to get spif-driver working on an Mbed OS platform.

Please install [mbed CLI](https://github.com/ARMmbed/mbed-cli#installing-mbed-cli).

## Import the example application

From the command-line, import the example:

```
mbed import mbed-os-example-spif
cd mbed-os-example-spif
```

### Now compile

Invoke `mbed compile`, and specify the name of your platform and your favorite toolchain (`GCC_ARM`, `ARM`, `IAR`). For example, the ARM_GCC compiler:

```
mbed compile --target NRF52840_DK --toolchain GCC_ARM
```

Your PC may take a few minutes to compile your code. At the end, you see the following result:

```
[snip]
+-------------------------------+--------+-------+-------+
| Module                        |  .text | .data |  .bss |
+-------------------------------+--------+-------+-------+
| [fill]                        |    268 |     0 |    60 |
| [lib]/c.a                     |  29301 |  2472 |    89 |
| [lib]/cc_310_core.a           |  39134 |     0 |     0 |
| [lib]/cc_310_ext.a            |    644 |     0 |    24 |
| [lib]/cc_310_trng.a           |    315 |     0 |     0 |
| [lib]/gcc.a                   |   3168 |     0 |     0 |
| [lib]/misc                    |    252 |    12 |    28 |
| [lib]/nosys.a                 |     32 |     0 |     0 |
| [lib]/stdc++.a                |      1 |     0 |     0 |
| main.o                        |    476 |     4 |   168 |
| mbed-os/drivers               |   1279 |     0 |    44 |
| mbed-os/features              |  63960 |    12 |  8422 |
| mbed-os/hal                   |   1742 |     8 |   130 |
| mbed-os/platform              |   4144 |   260 |   345 |
| mbed-os/rtos                  |  10371 |   168 |  6133 |
| mbed-os/targets               |  16351 |    60 |  1065 |
| spif-driver/SPIFBlockDevice.o |   1734 |     0 |     0 |
| Subtotals                     | 173172 |  2996 | 16508 |
+-------------------------------+--------+-------+-------+
Total Static RAM memory (data + bss): 19504 bytes
Total Flash memory (text + data): 176168 bytes

Image: ./BUILD/NRF52840_DK/GCC_ARM/mbed-os-example-spif.hex
*note: this build also includes the Nordic softdevice
       resulting in a larger combined final binary
```

### Program your board

1. Connect your Mbed device to the computer over USB.
1. Copy the binary file to the Mbed device.
1. Start your terminal program `sudo minicom -D /dev/ttyACM0 -b 115200`
1. Press the reset button to start the program.
1. Observe reading and writing flash

The first block on your flash part has 'Hello World' written to it.

<code>
spif test<br>
spif size: 8388608<br>
spif read size: 1<br>
spif program size: 1<br>
spif erase size: 4096<br>
Hello World!&#8267;
</code>

## Troubleshooting

If you have problems, you can review the [documentation](https://os.mbed.com/docs/latest/tutorials/debugging.html) for suggestions on what could be wrong and how to fix it.

