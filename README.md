# PINOUTS

- [PINOUTS](#pinouts)
  - [CH552G/CH554G Pinout](#ch552gch554g-pinout)

## CH552G/CH554G Pinout

![CH552G/CH554G Pinout](MCU/CH55x/CH552G_CH554G_Pinout.png)

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
