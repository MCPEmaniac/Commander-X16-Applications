# Commander X16 Color Palette Editor

This directory contains a snapshot and executable file of a Commander X16 Color Palette Editor which was built from C source files and is compatible with Release 34.

The up/down and left/right cursor keys are used to move between palette entries which are displayed on a color grid. The currently selected palette entry is surrounded by a box in the color grid and is also displayed at the top of the color grid with the associated index and RGB values displayed to the left and the associated palette data displayed to the right. All values are displayed in decimal.

The Commander X16 Color Palette Editor can be used to view the default color palette and to change the RGB values of the entries if desired. The RGB values of the currently selected palette entry can be changed with the r/R, g/G, and b/B keys which increment/decrement the red, green, and blue components respectively.

The palette data can be exported to a BASIC program which can be used to load the modified color palette for a user application or before running the Commander X16 Color Palette Editor again. The palette data is also exported in a format more amenable for inclusion into a C program.

The palette data exported in the BASIC program format can be reloaded into the Palette Editor via the following steps: 1) start the emulator using the -echo option; 2) paste the BASIC program into the emulator; 3) execute the RUN command; 4) execute the NEW command; 5) load the Palette Editor; and 6) execute the RUN command. The Palette Editor will then pick up the palette data that was loaded into the color palette by the BASIC program.
