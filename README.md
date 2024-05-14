displays 3D points defined by a right ascension and declesion from a body, with the idea being that it maps stars as seen from Earth.

you can move the "view point" of a pretend person with the latitude/longitude sliders in the control panel;
  for now, the latitude slider has limited movement due to issues I encountered with the revolution and the way I fixed it
  (by which I mean I made most of it fake 3D and lost the ability to revolve the NCP in a 3D space).

additionally, you can highlight the paths to any star (or whatever else is loaded into the program) by hovering the mouse over its name in the key;
  this works for both the 'Map Orientation Lines' and 'Tracked Objects' sections of the control panel, but not 'Equator Rotation';
    to highlight the equator, hover over its entry in 'Map Orientation Lines' (individual parts of the equator cannot be individually highlighted).

the 'Equator Rotation' compass shows a top-down view of the equator lines (relative to the equator, not latitude/longitude), 
  with the up direction in the display roughly corresponding to the direction going into the screen.

there are no controls in the page yet for adding custom stars, but such functionality exists in the script -
to add a custom star, go to the JavaScript console, and call the function
    **addRenderObject(\<*name*\>, \<*right ascension*\>, \<*declination*\>);**
where
     \<*name*\>             is the name of the object (which appears in the legends in the control panel),
     \<*right ascension*\>  is an array of 3 numbers representing the hours (index 0), minutes (index 1), and seconds (index 2) of the star's RA,
and  \<*declination*\>      is an array of 3 numbers representing the degrees (index 0), arcminutes (index 1), and arcseconds (index 2) of the star's declination.
e.g.,
  addRenderObject("Star", \[-50,0,0\], \[50,0,0\]);

the color of the star is *somewhat* customizable -
  the script automatically spreads all stars evenly across a part of the RGB spectrum according to the min and max values in the rgbTrigData object,
    min being the lowest value any color channel can be and max being the highest;
  these values can be set to anything through the console, but the sine waves used to determine the intensity of each color channel are not modifiable.

there is currently no way to remove stars other than the 'cull renderList' option in the devbar, which removes all items from the rendering queue.

the stars present by default make up the Big Dipper.

I have no idea whether the thing renders flipped or spins backwards or not. I've been unable to tune the sensitivity on the projection algorithm well,
  but I've attempted to use shading (darker = farther; ligher = closer) to show which side of the sphere thing the stars are supposed to be on.

why do newlines not work
