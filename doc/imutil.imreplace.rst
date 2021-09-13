imreplace — Replace a range of pixel values with a constant
===========================================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imreplace (Dec97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imreplace (Dec97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imreplace</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imreplace -- replace pixels in a window by a constant
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  imreplace images value lower upper
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images in which the pixels are to be replaced.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_value">value</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>Replacement value for pixels in the window.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imaginary">imaginary = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imaginary' Line='imaginary = 0.'>
  <DD>Replacement value for pixels in the windoe for the imaginary part of
  complex data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lower">lower = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Lower limit of window for replacing pixels.  If INDEF then all pixels
  are above <I>lower</I>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded up
  to the next higher integer.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Upper limit of window for replacing pixels.  If INDEF then all pixels
  are below <I>upper</I>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded down
  to the next lower integer.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 0.'>
  <DD>Additional replacement radius around pixels which are in the replacement
  window.  If a pixel is within this distance of a pixel within the replacement
  window it is also replaced with the replacement value.  Distances are
  measured between pixel centers which are have integer coordinates.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The pixels in the <I>images</I> between <I>lower</I> and <I>upper</I>,
  and all other pixels with a distance given by <I>radius</I>,
  are replaced by the constant <I>value</I>.  The special value INDEF in
  <I>lower</I> and <I>upper</I> corresponds to the minimum and maximum
  possible pixel values, respectively.
  <P>
  For complex images the replacement value is specified as separate
  real and imaginary and the thresholds are the magnitude.  For
  integer images the thresholds are used as inclusive limits
  so that, for example, the range 5.1-9.9 affets pixels 6-9.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. In a flat field calibration which has been scaled to unit mean replace
  all response values less than or equal to 0.8 by 1.
  <P>
      cl&gt; imreplace calib 1 upper=.8
  <P>
  2. Set all pixels to zero within a section of an image.
  <P>
      cl&gt; imreplace image[1:10,5:100] 0
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_IMREPLACE">IMREPLACE V2.11.1</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11.1'>
  <DD>A replacement radius to replace additional pixels was added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_IMREPLACE">IMREPLACE V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11'>
  <DD>The lower value is now rounded up for integer images so that a range
  like 5.1-9.9 affects pixels 6-9 instead of 5-9.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>