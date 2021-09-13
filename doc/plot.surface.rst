surface — Make a surface plot of an image
=========================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>surface (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>surface (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>surface</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  surface -- draw a three dimensional perspective plot of a surface
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  surface image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Image or image section to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_floor">floor = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='floor' Line='floor = INDEF'>
  <DD>Data values below <B>floor</B> are clipped.  If <B>floor = INDEF</B>, the data
  minimum is used for the floor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ceiling">ceiling = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ceiling' Line='ceiling = INDEF'>
  <DD>Data values above <B>ceiling</B> are clipped.  If <B>ceiling = INDEF</B>, the
  data maximum is used for the ceiling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_angh">angh = -33.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='angh' Line='angh = -33.0'>
  <DD>Horizontal viewing angle, degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_angv">angv = 25.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='angv' Line='angv = 25.0'>
  <DD>Vertical viewing angle, degrees.
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
  <DT><B><A NAME="l_title">title = "<TT>imtitle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>A title string is centered above the plot.  The user can specify a title
  string; the default is the image title.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_label">label = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='label' Line='label = no'>
  <DD>The axes are drawn and the corner points of the plotting area are labeled 
  if <B>label</B> = yes.
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
  averaging unless <B>subsample</B> = yes.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Surface</B> draws a pseudo-three dimensional perspective of an image
  section.  Hidden lines are removed.  The surface may be viewed from any
  angle.  Subsampling or block averaging is used to achieve the resolution
  specified.  A labeled perimeter is optionally drawn around the plot.
  <P>
  To speed up the plot, the resolution of the image can be decreased to
  <B>xres</B> by <B>yres</B>.  When <B>preserve</B> = yes, <B>surface</B> 
  automatically reduces the image in both directions by the same factor, which
  is the larger of [ncolumns / xres or nlines / yres].  If the
  aspect ratio is not being preserved, the x and y dimensions are independently
  reduced to the specified resolution.
  No reduction is done if
  <B>xres</B> and <B>yres</B> = 0, if the input image is an image section, or if
  the image is smaller than <B>xres</B> by <B>yres</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Surface plot of a 512 square image.  With the default values of <B>xres</B>
  and <B>yres</B>, the image would be block averaged by a factor of 8 in x and y.
  <P>
      cl&gt; surface crab.5009
  <P>
  2. Look at the bottom of the surface, but subsample rather that block average
  to decrease resolution and speed things up.  Also, the output device will
  be the plotter, and the job will run in the background:
  <P>
      cl&gt; surface crab.5009 angv=-30 subsample+ device=stdplot &amp;
  <P>
  3. Surface plot of band 4 of an image cube.  Since the image is specified using
  image section notation, no block averaging or subsampling will be done.
  <P>
      cl&gt; surface cube[*,*,4]
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  The time required by <I>surface</I> depends on image size and resolution.
  A surface plot of a
  512 square image block averaged to 64 square requires 30 cpu seconds.  The
  same image subsampled would take 23 seconds to plot.  
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  It should be possible to input the surface in list form. 
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  contour, graph
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>