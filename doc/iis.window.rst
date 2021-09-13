.. _window:

window — Adjust the contrast and dc offset of the current frame
===============================================================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  window -- adjust the contrast and dc offset of the current frame
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  window
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The lookup table between the display frame values and the values sent
  to the display monitor is adjusted interactively to enhance the display.
  The mapping is linear with two adjustable parameters; the intercept
  and the slope.  The two values are set with the image display cursor
  in the two dimensional plane of the display.  The horizontal position
  of the cursor sets the intercept or zero point of the transformation.
  Moving the cursor to the left lowers the zero point while moving the cursor to
  the right increases the zero point.  The vertical position of the cursor
  sets the slope of the transformation.  The middle of the display is zero
  slope (all frame values map into the same output value) while points above
  the middle have negative slope and points below the middle have positive
  slope.  Positions near the middle have low contrast while positions near
  the top and bottom have very high contrast.  By changing the slope from
  positive to negative the image may be displayed as positive or negative.
  <P>
  The interactive loop is exited by pressing any button on the cursor control.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  	cl&gt; window
  	Window the display and push any button to exit:
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  It may be necessary to execute FRAME before windowing.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
