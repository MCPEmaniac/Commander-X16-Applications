# Commander X16 RGB Color Grid

This directory contains a snapshot and executable file of a Commander X16 RGB Color Grid application which was built from C source files and is currently compatible with Release 34. The green and blue values are the vertical and horizontal components of the color grid respectively, and the entire color grid is updated when the red value is changed.

The green value is selected via the g/G keys or the up/down cursor keys and the blue value is selected via the b/B keys or the right/left cursor keys. The red value is selected via the r/R keys or the +/- keys.

The F1 key affects the display mode associated with the red value. In the default display mode the red value of the first entry in the palette is always set to 0 and the screen background and upper-left cell of the color grid are always black. In the alternate display mode the red value is populated in the first entry in the palette which affects the entire screen background as well as the upper-left cell of the color grid. The selected red value affects the color of the screen text in the default display mode as well as the alternate display mode. The alternate mode allows the shades of red to be viewed when the green and blue components are both zero, but the default mode is preferred when viewing all other color combinations.

The color currently selected is surrounded by a box in the color grid and is also displayed at the top of the color grid with the associated RGB values displayed to the left and the associated palette entry displayed to the right. All values are displayed in decimal.

I developed the Commander X16 RGB Color Grid application as an exercise to learn more about the operation of the VERA video-module and also to help me in choosing color shades for my screen and sprite graphics and easily determining the associated values for the palette.
