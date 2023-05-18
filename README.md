# Arduino Nano 33 IoT

This project is a starting platform to build applications on the
Arduino Nano 33 IoT. It comes preconfigured with WiFi, Gyroscope, and
serial via USB.

## Building

### Install dependencies:

```sh
arduino-cli core install arduino:samd
cargo install cargo-binutils
rustup component add llvm-tools-preview
```

### Build & flash:

```sh
cargo build --release
rust-objcopy -O binary target/thumbv6m-none-eabi/release/arduino-nano-33-iot target/arduino.bin
arduino-cli upload -i target/arduino.bin -b arduino:samd:nano_33_iot -p /dev/ttyACM0
```
### Automated build and flash

To save time, use the makefile for cargo-make so you can just run following command while your arduino in bootloader mode.

```sh
cargo make flash
```

### NOTE
**After flashing, serial communication between your arduino and pc will be gone. So if you want to put your arduino into bootloader mode you just need to press `rst` button on the board twice.**
Then you will be able to flash your application to arduino again.
