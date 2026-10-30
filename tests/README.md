# Sample tests

There is one complete input session per mode, with a matching simulator output
file under `expected/`:

| File | What it demonstrates |
|---|---|
| `life.txt` | The handout's blinker for two generations, with a 500 ms interval. |
| `images.txt` | All eight transformations applied successively to one asymmetric 8×8 image; every shift moves a lit pixel past an edge. |
| `tetris.txt` | One Adaptive game using the static sequence `OOOOTIJLSZ`: all seven shapes, movement, normal and faster falling, landing, two-row clearing, rotation, and game over. |

The Life session uses the handout's two-generation blinker. The image session
uses all eight operations; one extra clockwise rotation between the final
nonwrapping shifts ensures both directions actually discard lit pixels.
The wrapping shifts also move lit pixels across an edge.

The Tetris session provides one representative pass through the documented
mechanisms, using Adaptive difficulty and the ten-letter static sequence
`OOOOTIJLSZ`:

- All seven initial shapes, left/right movement, and display of the active
  piece together with fixed cells.
- Seven-update gravity, faster falling, and fresh falling phases after
  downward moves.
- Three-update landing allowance, movement and rotation while grounded,
  moving off support, preserved falling progress, and a fresh allowance
  after landing again.
- Clockwise rotation using up and up-right, counterclockwise rotation using
  up-left, and no horizontal movement during rotation requests.
- One rotation per activation of up, including when held across pieces;
  an O rotation keeps its shape, and a rotation that does not fit is rejected.
- Clearing two full rows together, scoring two points, and changing the
  Adaptive delay from 250 ms to 173 ms for subsequent pieces.
- Repeating the short static sequence, blocked-spawn game over, the final
  board, the continue prompt, and return to the main menu before exiting.

It is one game with 109 updates, ending with `Rows cleared: 2`. It does not
repeat the same mechanisms at every difficulty or enumerate every edge case.

Each input session returns to the main menu and exits. Tetris uses only Static
piece order, so no random-number sequence is involved.

From the repository folder, for example:

```sh
./executables/linux/ex3 < tests/inputs/life.txt > actual.txt
diff -u tests/expected/life.txt actual.txt
```

Use the reference executable for your computer, or replace its path with your
compiled program. Compare the full output, including blank lines and spaces
inside matrix rows. Windows output may use CRLF line endings; normalize line
endings before comparing. The simulator prints delays without waiting in real
time.

These examples illustrate the main behavior. They do not cover every edge case
or replace your own testing on the simulator and Arduino.
