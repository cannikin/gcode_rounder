# Gcode Rounder

Rounds off gcode to a given number of digits after the decimal. Requires an `IN` file and `OUT` file 
and optionally the `PRECISION` to round off (defaults to 6 decimals).

## Requirements

This script requires [Ruby](https://www.ruby-lang.org/en/documentation/installation/).

## Installation

Clone the repo:

    git clone https://github.com/cannikin/gcode_rounder.git
    cd gcode_rounder
  
Done!

## Usage

    IN=/path/to/file OUT=/path/to/file PRECISION=6 ./round
  
`IN` and `OUT` are file paths, something like:

    IN=~/gcode/file.nc OUT=~/gcode/file.gcode ./round

This will round off your gcode to 6 decimals which should be more than enough precision for most
machines. If you need more (or less) you can also set the precision:

    IN=~/gcode/file.nc OUT=~/gcode/file.gcode PRECISION=8 ./round

The output will have comment on the first line that rounding was performed by this library.

You'll get a little bit of output while your gcode is being rounded and once complete:

    Converting 838 lines...done!

    2850 commands rounded to 6 decimal precision.
    1068 commands ignored.

## Example Input/Output

#### Input

    G21 G90 G40

    G0 Z3
    T0 M6
    G17
    M3
    G0 X187.35558375634517 Y107.70558375634518
    G1 Z-1.3401015228426396 F50
    G3 X188.14974619289342 Y109.07868020304569 I-0.7918781725888324 J1.3730964467005078 F1200
    G3 X187.93654822335026 Y109.8730964467005 I-1.5837563451776648 J0
    G1 X187.8730964467005 Y109.97969543147208
    
#### Output

    (Decimal precision updated by Gcode Rounder 1.0)

    G21 G90 G40

    (controllers)
    G0 Z3
    T0 M6
    G17
    M3
    G0 X187.355584 Y107.705584
    G1 Z-1.340102 F50
    G3 X188.149746 Y109.07868 I-0.791878 J1.373096 F1200
    G3 X187.936548 Y109.873096 I-1.583756 J0
    G1 X187.873096 Y109.979695
    
