# Slic3r (and printer) configs

Configuring 3d printers is, politely, a bear.
This repo houses my attempts to dial and document the configuration for my printers, and the filament parameters.

While the precise printer configs may not be of use, I hope that others may find the filament settings more helpful.

**WARNING** these configurations hard-code the "correct" tunings for my printer(s) as part of the print prelude.
Before using these settings, check `Printer Settings > Custom G-Code` and either adapt or remove the `M92` command which alters feed rates.

**WARNING** 3d printers are incredibly finicky.
Each machine is unique, and performing x/y/z/e calibration for your specific unit(s) is essential to getting good results.
DO NOT EXPECT MY CALIBRATION VALUES TO WORK FOR YOU.

### Calibrating X/Y/Z

For X/Y/Z calibration, I like https://www.thingiverse.com/thing:195604.
It's a single object which should be 100mm in X, 100mm in Y and 50mm in Z.
1. Print one off
2. Issue [`M92`](https://marlinfw.org/docs/gcode/M092.html) to get your current x/y/z (and E) steps, or look in your printer's settings.
3. For each axis `steps_new = steps_old / (actual_size / expected_size)`. Note that Marlinfw and friends are precise AT MOST to two decimal places, if not zero for steps.

### Calibrating E

1. Heat the print end for your available filament.
2. Measure 100mm from where the filament enters your print head's drive.
3. Issue `G1 E100 F100`; which will feed what the printer believes to be 100mm of material through the hot end.
4. Measure the distance between your mark and reference point on the print head's drive.
5. Compute the over or under-extrusion as a fraction of the 100mm you were expecting to print.

## License

Copyright Reid D. 'arrdem' McKenzie, 2021.

Published under the terms of the [anticapitalist.software](https://anticapitalist.software) v1.4 license.

See [LICENSE.md](LICENSE.md).
