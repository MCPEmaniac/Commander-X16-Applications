# Commander X16 Sprite Editor

This directory contains a screen snapshot and the executable of a Commander X16 Sprite Editor which is built from "C" source files I’ve been developing that currently runs on Release 33 of the emulator.

## Features

The sprite editor supports all combinations of sprite height and width dimensions up to 64x64. The sprite editor is currently limited to 4 color bits per pixel, but provides the ability to edit the RGB values of the first 16 entries of the color palette. The sprite editor supports a pen mode which reduces the keystrokes required to assign colors to sprite pixels, and the ability to shift the design of the sprite to make more room near the edge of the sprite.

The sprite editor provides the ability to export color palette data as well as sprite data to the terminal in a BASIC program format and also in a format more amenable to importing into a C program. The BASIC program allows the sprite to be rendered and moved around a bit using the W/A/S/D keys. This export capability requires the -echo option when starting the emulator.

## Operation

### Cursor Movement

The arrow keys are used to move the cursor around the sprite pixel edit grid. When height=64 the edit grid can be paged up and down using the comma and period keys ("," and "."), and when width=64 the edit grid can be paged left and rignt using the less-than and greater-than keys ("<" and ">").

### Assigning Colors to Sprite Pixels

The 0-9/A-F keys are used to assign a color to the sprite bit corresponding to the current edit grid cursor position.

When pen mode is turned on using the P key, the color at the current edit grid cursor position is assigned to the pen, and this color is automatically assigned to pixels as the edit cursor is moved. The pen color can be changed by selecting a new color via the 0-9/A-F keys. Pen mode is manually turned off by pressing the P key a second time, and is automatically turned off when the cursor is moved past the edge of the edit grid and when the edit grid is paged when height=64 or width=64.

The fill command (F5 key) fills the entire sprite with the color at the current edit grid cursor position.

### RGB Edit Mode

RGB edit mode provides the ability to edit the RGB values of the first 16 entries of the color palette. RGB edit mode is entered and exited by pressing the F6 key. In RGB edit mode, a right arrow appears to the left of the selected color, and selected color is changed by using the up/down cursor keys. The red, green, and blue components of the selected color are changed by using the R/shift-R, G/shift-G, and B/shift-B keys.

### Sprite Design Shifting

The sprite design can be shifted up or down one pixel row using the U and shift-U keys, and can be shifted right or left one pixel column using the R and shift-R keys. This feature is useful when a sprite design is not centered correctly when started and one runs out of space near an edge. The sprite design can be shifted to make more room near the edge which avoids having to start the sprite design over again at a new location.

### Sprite Options

V-flip and H-flip (V and H keys) affect the display of the actual sprite but not the sprite edit grid. The palette offset (+/- keys) also only affects the display of the actual sprite (the edit grid colors and remainder of the screen colors are not affected).

### Screen Options

The BG and FG options (F3 and F4 keys) provide the ability to change the screen background color and the color of the text on the screen.

There's an anomaly associated with color 0 which is black in the standard color palette. Color 0 is shown as black on the screen and edit grid but is transparent when used in sprites, so the edit grid doesn't match the sprite with respect to color 0.

### Exported BASIC Program

The exported BASIC program between line 10 and the DATA statements is constant. Line 10 varies with the height and width of the sprite and the DATA statements vary with the color palette data and design of the sprite.

The SA7 value is based on the enumerated values of the height and width dimensions (0 for 8, 1 for 16, 2 for 32, and 3 for 64) and places these values into the proper position to be populated in the most significant nibble of the last sprite attribute register which has an offset of 7. The least significant nibble of this register is the palette offset which I assumed to be 0. The SA7 value is computed in the C program, but it could have been computed in the BASIC program since the enumerated values can be determined from the height and width which are exported on line 10 and palette offset is assumed to be 0.

I deferred support for saving/loading color palette and sprite data because I'm under the impression the emulator currently doesn't support file I/O, but the BASIC program provides a near-term workaround. The color palette and sprite data exported in the BASIC program format can be reloaded into the sprite editor via the following steps: 1) start the emulator; 2) paste the BASIC program into the emulator; 3) execute the RUN command; 4) push the Esc key to quit the running program; 5) execute the NEW command; 6) load the sprite editor; and 7) execute the RUN command. The sprite editor will then pick up the color palette data that was loaded into the palette and sprite data that was loaded into the VERA sprite attribute registers and VRAM by the BASIC program.

## Potential Future Enhancements

I'm considering enhancements including support for 8 color bits per pixel, saving/loading of palette and sprite data, rotation of sprites, undo/redo of changes to the sprite graphics data in VRAM.
