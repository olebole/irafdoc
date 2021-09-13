rmode — Ring modal filter a list of 1D or 2D images
===================================================

**Package: imfilter**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rmode (May95)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfilter</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rmode (May95)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rmode</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rmode -- ring modal filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rmode input output rinner router
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of filtered images. The number of input images must be the same as the
  number of output images. If the input image name equals the output image name
  the filtered image replaces the original image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rinner">rinner, router</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rinner' Line='rinner, router'>
  <DD>The inner and outer semi-major axes of the ring filter in pixels. If rinner
  is set to 0.0 then the ring filter becomes a circular filter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ratio">ratio = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 1.0'>
  <DD>The ratio of the semi-minor axis to the semi-major axis of the ring filter.
  If ratio is 1.0 the ring filter is circularly symmetric.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_theta">theta = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 0.0'>
  <DD>The position angle of the major axis of the ring filter. Theta is measured
  counter-clockwise in degrees from the x axis and must be between 0 and
  180 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zloreject">zloreject = INDEF, zhireject = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good pixel values. Zloreject and zhireject default
  to  -MAX_REAL and MAX_REAL respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary">boundary = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The type of boundary extension. The options are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Reflect pixel values around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Wrap pixel values around the boundary.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value for constant valued boundary extension.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  RMODE takes a list of input images <I>input</I> and produces a list of
  filtered
  images <I>output</I>. The filter consists of a sliding circular / elliptical or
  annular circular / elliptical window whose size and orientation is determined
  by the <I>rinner</I>, <I>router</I>, <I>ratio</I>, and <I>theta</I> parameters.
  The center pixel in the window is replaced by the mode of the pixel
  distribution where mode is defined below.
  <P>
  <PRE>
  	mode = 3. * median - 2. * mean
  </PRE>
  <P>
  The median is defined as the value of the (n + 1) / 2 number in an ordered
  sequence of numbers.
  Out of bounds pixel references are handled by setting the parameter
  <I>boundary</I>. The principal function of the circular / elliptical filter
  is to smooth and image using a circularly / elliptically symmetric filter.
  The principal function of the circular / elliptical ring filter is to
  remove objects from the image which have a scale length of rinner and
  replace them with an estimate of the local background value.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to reject
  bad data from the modal filtering box.  If no good
  data is left in a given filtering box, then the mode is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  The properties of the ring median filter and its application to
  astronomical analysis problems is summarized in the
  article "<TT>A Ring Median Filter  for Digital Images</TT>" (Secker, J., 1995,
  PASP, 107, 496-501) and references therein.
  <P>
  A derivation of the expression for the mode used here can be found in
  "<TT>Statistics in Theory and Practice</TT>", Robert Lupton, 1993, Princeton
  University Press, problem 2.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Modal filter an image using a circular ring filter with an inner radius
  of 4 pixels and a width of 1 pixel.
  <P>
  <PRE>
     cl&gt; rmode input output 4.0 5.0
  </PRE>
  <P>
  2. Modal filter an image using a circular filter of outer radius 3.0.
  <P>
  <PRE>
     cl&gt; rmode input output 0.0 3.0
  </PRE>
  <P>
  3. Modal filter the test image dev$pix rejecting any pixels &lt; 5 or
  greater than 19935 from the modal filter using a circular
  filter of outer radius 5.0.
  <P>
  <PRE>
      im&gt; rmode dev$pix output 0.0 5.0 zloreject=5 zhireject=19935
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It requires approximately 59 and 35 CPU seconds to modal filter a
  512 by 512 square integer image with a circular filter of radius 5 pixels
  and a ring filter of inner and outer radii of 4.0 and 5.0 pixels respectively.
  (SPARCStation2).
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mode,fmode,rmode
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>