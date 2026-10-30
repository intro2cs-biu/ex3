# Exercise 3 — Arrays, Images, and Tetris

Read **[ex3.pdf](ex3.pdf)** for the assignment requirements. Implement your
solution in the empty **ex3.c** file. Submit only your completed `ex3.c`,
as explained in the handout.

## Reference executables

These programs demonstrate the required behavior; they are not starter code.

| Folder | Target | File |
|---|---|---|
| `executables/macos/` | macOS, Apple Silicon (arm64) | `ex3` |
| `executables/macos-intel/` | macOS, Intel (x86-64) | `ex3` |
| `executables/linux/` | Linux, x86-64 | `ex3` |
| `executables/windows/` | Windows, x86-64 | `ex3.exe` |
| `executables/arduino/` | Arduino Uno (ATmega328P) | `ex3.hex` |

Run the executable for your computer from a terminal, or upload the HEX file
to the Arduino using the handout's instructions. Serial communication uses
9600 baud. Use the course library package that matches your computer when
compiling your own program; the library is distributed separately.

For example, from this folder on Linux:

```sh
./executables/linux/ex3
```

## Sample tests

`tests/inputs/` contains three sample sessions, one per mode. The same filename under
`tests/expected/` contains the matching simulator output. See
**[tests/README.md](tests/README.md)** for the coverage of each case and how to
compare output. All Tetris test sessions select Static piece order, so they
do not depend on platform-specific random-number sequences.

For example:

```sh
./executables/linux/ex3 < tests/inputs/life.txt > actual.txt
diff -u tests/expected/life.txt actual.txt
```

The reference program also supports Random mode, as required by the handout.
The simulator prints delays without waiting in real time. The physical board
waits for the specified duration. Passing the sample tests does not guarantee
that every required behavior is correct; also test your implementation on
the Arduino with the matrix and joystick.
