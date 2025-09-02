# CH552/CH554

- [CH552/CH554](#ch552ch554)
  - [CH552G/CH554G Pinout](#ch552gch554g-pinout)
  - [Set Up Development Environment](#set-up-development-environment)
    - [Set Up SDCC on macOS](#set-up-sdcc-on-macos)
  - [CH552/CH554 Documents](#ch552ch554-documents)
  - [References](#references)
  - [License](#license)

## CH552G/CH554G Pinout

![CH552G/CH554G Pinout](CH552G_CH554G_Pinout.png)

|    # | Pin  | Timer       | SPI  | PWM   | UART  | Timer | Interrupt | Touch | USB   | ADC  | From Datasheet                    |
| ---: | ---- | ----------- | ---- | ----- | ----- | ----- | --------- | ----- | ----- | ---- | --------------------------------- |
|    1 | P3.2 |             |      |       | TXD1_ |       | INT0      |       | VBUS1 | AIN3 | P3.2/TXD1_/INT0/VBUS1/AIN3        |
|    2 | P1.4 | T2_/CAP1_   | SCS  |       |       |       |           | TIN2  | UCC1  | AIN1 | P1.4/T2_/CAP1_/SCS/TIN2/UCC1/AIN1 |
|    3 | P1.5 |             | MOSI | PWM1  |       |       |           | TIN3  | UCC2  | AIN2 | P1.5/MOSI/PWM1/TIN3/UCC2/AIN2     |
|    4 | P1.6 |             | MISO |       | RXD1  |       |           | TIN4  |       |      | P1.6/MISO/RXD1/TIN4               |
|    5 | P1.7 |             | SCK  |       | TXD1  |       |           | TIN5  |       |      | P1.7/SCK/TXD1/TIN5                |
|    6 | RST  | T2EX_/CAP2_ |      |       |       |       |           |       |       |      | RST/T2EX_/CAP2_                   |
|    7 | P3.1 |             |      | PWM2_ | TXD   |       |           |       |       |      | P3.1/PWM2_/TXD                    |
|    8 | P3.0 |             |      | PWM1_ | RXD   |       |           |       |       |      | P3.0/PWM1_/RXD                    |
|    9 | P1.1 | T2EX/CAP2   |      |       |       |       |           | TIN1  | VBUS2 | AIN0 | P1.1/T2EX/CAP2/TIN1/VBUS2/AIN0    |
|   10 | P3.3 |             |      |       |       |       | INT1      |       |       |      | P3.3/INT1                         |
|   11 | P3.4 |             |      | PWM2  | RXD1_ | T0    |           |       |       |      | P3.4/PWM2/RXD1_/T0                |
|   12 | P3.6 |             |      |       |       |       |           |       | UDP   |      | P3.6/UDP                          |
|   13 | P3.7 |             |      |       |       |       |           |       | UDM   |      | P3.7/UDM                          |
|   14 | GND  |             |      |       |       |       |           |       |       |      | GND                               |
|   15 | VCC  |             |      |       |       |       |           |       |       |      | VCC                               |
|   16 | V33  |             |      |       |       |       |           |       |       |      | V33                               |

## Set Up Development Environment

[SDCC](https://github.com/Blinkinlabs/ch554_sdcc) and [Arduino](https://github.com/DeqingSun/ch55xduino) are available for CH552 development.

### Set Up SDCC on macOS

1. Install `sdcc` and `binutils`.

    ```shell
    brew install sdcc

    # For objcopy
    brew install binutils
    ```

    Add the `binutils` path to your `$PATH` environment variable.

    ```shell
    # macOS arm64
    /opt/homebrew/opt/binutils/bin
    # macOS x86_64
    /usr/local/opt/binutils/bin

    # Z shell - Add the following lines to .zshrc
    if [[ $(uname -m) == 'arm64' ]]; then                  # macOS arm64
        path+=('/opt/homebrew/opt/binutils/bin')           # binutils
    else                                                   # macOS x86_64
        path+=('/usr/local/opt/binutils/bin')              # binutils
    fi
    ```

2. Clone [ch554_sdcc](https://github.com/Blinkinlabs/ch554_sdcc).

    ```shell
    git clone https://github.com/Blinkinlabs/ch554_sdcc.git
    ```

3. Install [CH55x flash tool](https://github.com/MarsTechHAN/ch552tool).

    ```shell
    # Install libusb
    brew install libusb

    # [OPTIONAL] Use Python Virtual Environment
    python3 -m venv .venv
    source .venv/bin/activate

    # Install ch55xtool
    python3 -m pip install ch55xtool
    ```

    Replace `WCHISP` in the `Makefile`:

    ```Makefile
    WCHISP ?= python3 -m ch55xtool -f
    # Or explicitly specify the Python version
    WCHISP ?= python3.11 -m ch55xtool -f
    ```

4. Build and flash the examples.

    ```shell
    cd ch554_sdcc/examples
    make
    cd blink
    make flash
    ```

## CH552/CH554 Documents

- CH552 Datasheet - [English](./Documents/CH552%20Datasheet%20V1.8%20-%20English.PDF) / [Chinese](./Documents/CH552%20Datasheet%20V1.8%20-%20English.PDF) (Official Website: [English](https://wch-ic.com/downloads/CH552DS1_PDF.html) / [Chinese](https://www.wch.cn/downloads/CH552DS1_PDF.html))
- CH554 Datasheet - [English](./Documents/CH554%20Datasheet%20V1.8%20-%20English.PDF) / [Chinese](./Documents/CH554%20Datasheet%20V2.1%20-%20Chinese.PDF) (Official Website: [English](https://wch-ic.com/downloads/CH554DS1_PDF.html) / [Chinese](https://www.wch.cn/downloads/CH554DS1_PDF.html))
- [CH554 Evaluation Board](./Documents/CH554EVT.ZIP) ([Official Website](https://www.wch.cn/downloads/CH554EVT_ZIP.html))

## References

- [Blink Labs - CH554 SDCC](https://github.com/Blinkinlabs/ch554_sdcc)
- [Stefan Wagner - CH552 USB OLED](https://github.com/wagiminator/CH552-USB-OLED)

## License

![CC by-nc-sa](../../Images/by-nc-sa.svg)

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

- Attribution - You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- NonCommercial - You may not use the material for commercial purposes.
- ShareAlike - If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
