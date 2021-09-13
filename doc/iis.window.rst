window — Adjust the contrast and dc offset of the current frame
===============================================================

**Package: iis**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>window (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv.iis</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>window (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>window</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  window -- adjust the contrast and dc offset of the current frame
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  window
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  	cl&gt; window
  	Window the display and push any button to exit:
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  It may be necessary to execute FRAME before windowing.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>