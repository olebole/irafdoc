contour — Make a contour plot of an image
=========================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>contour (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>contour (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>contour</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  contour -- draw a contour plot of an image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  contour image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Two dimensional image or image section to be contoured.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_floor">floor = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='floor' Line='floor = INDEF'>
  <DD>Minimum value to be contoured.  If <B>floor = INDEF</B>, the data minimum is
  used for the floor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ceiling">ceiling = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ceiling' Line='ceiling = INDEF'>
  <DD>Maximum value to be contoured.  If <B>ceiling = INDEF</B>, the data maximum
  is used for the ceiling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zero">zero = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zero' Line='zero = 0'>
  <DD>Greyscale value of the zero contour, i.e., the value of a zero point shift
  to be applied to the image data before plotting.  Does not affect the values
  of the floor and ceiling parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncontours">ncontours = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncontours' Line='ncontours = 0'>
  <DD>Number of contours to be drawn.  If 0, the contour interval may be specified,
  otherwise 20-30 nicely spaced contours are drawn.  A maximum of 40 contours
  can be drawn.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interval">interval = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interval' Line='interval = 0'>
  <DD>Contour interval.  If 0, a contour interval is chosen which places 20 to 30
  contours spanning the intensity range of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nhi">nhi = -1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nhi' Line='nhi = -1'>
  <DD>If -1, highs and lows are not marked.  If 0, highs and lows are marked
  on the plot.  If 1, the intensity of each pixel is marked on the plot.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dashpat">dashpat = 528</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dashpat' Line='dashpat = 528'>
  <DD>Dash pattern for negative contours.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Output device (<B>stdgraph</B>, <B>stdplot</B>, or the name of a physical
  device).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xres">xres = 64, yres = 64</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xres' Line='xres = 64, yres = 64'>
  <DD>The input image is block averaged or subsampled to this resolution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_preserve">preserve = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='preserve' Line='preserve = yes'>
  <DD>If <B>preserve</B> = yes, the aspect ratio of the image is preserved when 
  achieving the resolution specified by <B>xres</B> and <B>yres</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_subsample">subsample = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subsample' Line='subsample = no'>
  <DD>The resolution specified by <B>xres</B>, <B>yres</B> is achieved by block 
  averaging unless <B>subsample = yes</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_perimeter">perimeter = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='perimeter' Line='perimeter = yes'>
  <DD>A <I>crtpict</I> perimeter is drawn around the contour plot with labeled
  tickmarks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_label">label= yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='label' Line='label= yes'>
  <DD>By default, the value of each major contour is embedded in the contour
  line.  This can be disabled by setting <B>label=no</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vx1">vx1 = 0.0, vx2 = 0.0, vy1 = 0.0, vy2 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 0.0, vy1 = 0.0, vy2 = 0.0'>
  <DD>The device viewport, in normalized device coordinates (from 0.0 to 1.0
  inclusive).  If not specified by the user,
  <B>contour</B> automatically centers the plot on the device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = no'>
  <DD>Fill the output viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = "<TT>imtitle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>A title to be centered above the plot.  The user can specify a title string;
  the default string is the image title.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Contours are traced, smoothed with splines under tension, and optionally printed
  with embedded intensity labels.  Positive contours are printed as solid
  lines and negative contours as dashed lines.  The plot is generated
  by the NCAR <B>conrec</B> utility, using <B>dashsmth</B> to smooth the
  contours and draw dashed lines.  
  <P>
  To speed up the contouring, the resolution of the image to be plotted can
  be decreased to <B>xres</B> by <B>yres</B>.
  When <B>preserve</B> = yes, <B>contour</B> 
  automatically reduces the image in both directions by the same factor, which
  is the larger of [ncolumns / xres or nlines / yres]. If the
  aspect ratio is not being preserved, the x and y dimensions are independently
  reduced to the specified resolution.
  No reduction is done if <B>xres</B> and <B>yres</B> = 0, if the input image is 
  an image section, or if the image is smaller than <B>xres</B> by <B>yres</B>.
  <P>
  If the device viewport (plotting area) is not set by the user,
  <I>contour</I> automatically
  sets a viewport centered on the output device.  The default value of
  <B>fill=no</B> means the viewport will be adjusted so that equal
  numbers of image pixels in x and y will occupy equal lengths when plotted.
  That is, when <B>fill = no</B>, a unity aspect ratio is enforced, and square 
  images are represented as square plots regardless of the device aspect ratio.
  On devices with non square full device viewports (e.g., the vt640), a 
  square image will appear extended when <B>fill</B> = yes.  To completely
  fill the device viewport with contour lines, disable perimeter drawing
  and enable fill, and nothing but the contour map will be drawn.
  <P>
  Contour plots may be overlaid on a displayed image by setting the output
  <B>device</B> to "<TT>imd</TT>" for image display and the contouring parameters
  <B>fill</B> and <B>perimeter</B> to "<TT>yes</TT>" and "<TT>no</TT>" respectively. By default
  green contours will be drawn on the image display. Other choices for
  <B>device</B> are "<TT>imdr</TT>", "<TT>imb</TT>", "<TT>imdy</TT>", "<TT>imdw</TT>" and "<TT>imdg</TT>" for red, blue,
  yellow, white and green output contours respectively.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Draw a contour plot of a 512 square image on the graphics terminal.
  With the default values for <B>xres</B> and <B>yres</B>, the image
  would automatically be block averaged by a factor of 8 in x and y.
  <P>
      cl&gt; contour crab.5009
  <P>
  2. The plot could be output to the plotter as a background job:
  <P>
      cl&gt; contour crab.5009 device=stdplot &amp;
  <P>
  3. Place a ceiling at an intensity value of 500 to cut out a noise spike.
  The plot has been moved to the lower left corner of the display.
  <P>
      cl&gt; cont crab.5009 ceil=500 vx1=.1 vx2=.6 vy1=.1 vy2=.6
  <P>
  4. Overlay a contour plot of an image on the same image displayed on the
  display device. Note that the CONTOUR parameters <B>fill</B> and <B>perimeter</B>
  must be on and off respectively, the <B>fill</B> parameter should be specified
  for the DISPLAY task to ensure the image fills the frame buffer in the 
  same way.
  <P>
  <PRE>
      cl&gt; display m51 1 fill+
      cl&gt; cont m51 fill+ per- device=imd
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  The time required for <I>contour</I> depends on the number of contours
  being drawn - that is, the size and smoothness of the intensity array.
  A 512 square image of "<TT>average</TT>" smoothness, with x and y resolution equal to
  64, requires about 22 cpu seconds with block averaging.  Using subsampling
  rather than block averaging, <I>contour</I> takes 16 seconds.  A noisy
  picture will be plotted more quickly if block averaged rather than
  subsampled.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If block averaging is used the precision with which a contour is drawn
  will be no better than the blocking factor.  For example, if a contour
  map drawn with a block averaging factor of 8 is overlaid on an image of
  a starfield, contours drawn around stars in the field may not appear to
  be centered.  If this is a problem the solution is to increase the plotting
  resolution using the <I>xres</I> and <I>yres</I> parameters.
  <P>
  It should be possible to have list input as well as image section input.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  surface, display, imdkern, imexamine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>