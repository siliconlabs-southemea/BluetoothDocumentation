---
sort: 4
---
# run DTM commands

1. Launch YAT and open a new terminal from the File menu for your kit with the correct UART settings like described in [this page](/Bluetooth/Applications/RCP_HCI/Basic_rcp_test/check_with_YAT.md)
2. alternatively other methods to send hexadecimal data can be used (Python for example)
3. Then you can send commands as per [bluetooth specification](https://www.bluetooth.com/specifications/core54-html/) chapiter 7.8.28/7.8.29/7.8.30

For the below table remember commands start with 0x01 and following bytes are coded using the following scheme (OGF is upper 6 bits for the opcode coded in little endian)

<img src="./images/Screenshot 2024-03-05 at 14.44.21.png" alt="" width="500" class="center">

Here are some useful ones as example:

| test command             | OCF  | OGF  | hex string                          | comments                                                                                                                                                        |
| ------------------------ | ---- | ---- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| reset                    | 0x03 | 0x03 | 01 03 0C 00                         |                                                                                                                                                                 |
| LE Transmit Test v2      | 0x34 | 0x08 | 01 34 20 04 00 25 00 01             | 4 parameters: channel is 0, data length is 25, type is PRBS9 and PHY is LE 1M                                                                                   |
| LE Test End              | 0x1F | 0x08 | 01 1F 20 00                         |                                                                                                                                                                 |
| LE Transmit test v4 0dBm | 0x7B | 0x08 | 01 7B 20 08 00 25 00 01 00 00 00 00 | 8 parameters: channel is 0, data lenght is 25, payload is PRBS9, PHY is LE 1M, no CTE, CTE type AoA, swictng pattern is 0, antenna id is 0 and TX power is 0dBm |

Tests should always be ended by a LE test End to be able to send a new command.
