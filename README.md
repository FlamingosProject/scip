# scipio: a roamin' general terminal program

This is a fork by Bart Massey and Philipp Oppermann of the
quite nice [Scip](https://gitlab.com/w0lff/scip) Rust serial
terminal program, with an enhancement to upload bin files to
a remote.

This version of Scip supports the upload protocol used by
<https://github.com/FlamingosProject/flamingos/>
for uploading kernel images to a Raspberry Pi: this is
intended as a replacement for the Ruby `minipush` in the
original tutorials. See the OS source code for details.

The remainder of this README is from the original Scip.

## Scip - Serial Console Interfacing Program

A command line tool to communicate with a serial console written in [Rust](https://rust-lang.org)

### Usage
```
USAGE:
    scip [--binfile <FILE>] <DEVICE> [ARGS]

ARGS:
    --binfile <FILE>  Provide a file that can be uploaded by a remote escape sequence
    --verbose         Print messages during file upload
    <DEVICE>          Set the device path to a serial port
    <baud rate>       Set the baud rate to connect at [default: 9600]
    <data bits>       Set the number of bits used per character [default: 8] [possible values:
                      5, 6, 7, 8]
    <parity>          Set the parity checking mode [default: N] [possible values: N, O, E]
    <stop bits>       Set the number of stop bits transmitted after every character [default: 1]
                      [possible values: 1, 2]
    <flow control>    Set the flow control mode [default: N] [possible values: N, H, S]

Escape commands begin with <Enter> and end with one of the following sequences:
    ~~ - send the '~' character
    ~. - terminate the connection
```

For more verbose help information and parameter suggestions add the `--help` option:
```bash
scip --help
```

### Examples
```bash
scip /dev/ttyUSB0 115200
scip /dev/ttyUSB1 19200 6 E 2 H
scip --binfile kernel8.img /dev/ttyUSB0 921600 8 N 1 N
```

### License
MIT
