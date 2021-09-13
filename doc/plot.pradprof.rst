.. _pradprof:

pradprof — Plot or list the radial profile of a stellar object
==============================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pradprof -- plot or list the radial profile of a stellar object
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pradprof input xinit yinit
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of images containing the object of interest.
  </DD>
  </DL>
  <DL>
  <DT><B>xinit, yinit</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xinit' Line='xinit, yinit'>
  <DD>The initial guess for the  x and y coordinates of the object whose
  profile is to be computed.  If <I>center</I>
  is yes, <I>xinit</I> and <I>yinit</I> are the initial input to the centering 
  algorithm, otherwise <I>xinit</I> and <I>yinit</I> are passed directly to the
  radial profiling algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 11</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 11'>
  <DD>The plotting radius in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>az1 = 0., az2 = 360.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='az1' Line='az1 = 0., az2 = 360.'>
  <DD>Azimuth limits for the profile points in degrees.  The azimuth is
  measured from the x or first image axis towards the y or second image
  axis.  Negative azimuths are allowed as are any multiples of 360.
  </DD>
  </DL>
  <DL>
  <DT><B>center = yes </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = yes '>
  <DD>Center the initial coordinates before computing the profile?
  </DD>
  </DL>
  <DL>
  <DT><B>cboxsize = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cboxsize' Line='cboxsize = 5'>
  <DD>The size of the extraction box of pixels to be used by the centering
  algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>list = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list' Line='list = no'>
  <DD>Make a list of the radial profile, instead of a plot?
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The graphics device for plotting.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>The plot title. If title = "<TT>imtitle</TT>", the image name, <I>xinit</I>, and
  <I>yinit</I> are
  used to construct a default title, otherwise the user specified title is
  used.
  </DD>
  </DL>
  <DL>
  <DT><B>xlabel = "<TT>Radius</TT>", ylabel = "<TT>Intensity</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "Radius", ylabel = "Intensity"'>
  <DD>The default labels for the X and Y axes.
  </DD>
  </DL>
  <DL>
  <DT><B>wx1 = INDEF, wx2 = INDEF, wy1 = INDEF, wy2 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = INDEF, wx2 = INDEF, wy1 = INDEF, wy2 = INDEF'>
  <DD>The range of user coordinates spanned by the plot. By default the data is
  used to determine the range.
  </DD>
  </DL>
  <DL>
  <DT><B>logx = no, logy = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = yes'>
  <DD>Use log scaling on the x or y axes of the plot?
  </DD>
  </DL>
  <DL>
  <DT><B>round = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Round the axes minimum and maximum values up to "<TT>nice</TT>" values?
  </DD>
  </DL>
  <DL>
  <DT><B>box = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='box' Line='box = yes'>
  <DD>Draw axes at the perimeter of the plotting window?
  </DD>
  </DL>
  <DL>
  <DT><B>majrx = 5, minrx = 5, majry = 5, minry = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx = 5, minrx = 5, majry = 5, minry = 5'>
  <DD>Number of major tick marks on each axis and number of minor tick marks between
  major tick marks. These quantities are ignored if log scaling is in effect
  for an axis.
  </DD>
  </DL>
  <DL>
  <DT><B>ticklabels = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes'>
  <DD>Label the tick marks?
  </DD>
  </DL>
  <DL>
  <DT><B>fill = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill the output viewport regardless of the device aspect ratio ?
  </DD>
  </DL>
  <DL>
  <DT><B>vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0'>
  <DD>The NDC coordinates (0.0:1.0) of the device plotting viewport.
  </DD>
  </DL>
  <DL>
  <DT><B>pointmode = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = yes'>
  <DD>Plot points instead of lines?
  </DD>
  </DL>
  <DL>
  <DT><B>marker = "<TT>plus</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='marker' Line='marker = "plus"'>
  <DD>Type of marker used in pointmode.
  </DD>
  </DL>
  <DL>
  <DT><B>szmarker = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 1.'>
  <DD>Size of markers used in pointmode.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PRADPROF computes a radial profile of length <I>radius</I> pixels
  with a range of azimuths (<I>az1</I> to <I>az2</I>),
  for the object near (<I>xinit</I>, <I>yinit</I>) in the input image(s) 
  <I>input</I>, and plots it on the graphics device <I>graphics</I>.
  If the parameter <I>center</I> is
  "<TT>yes</TT>", then pixels in a box <I>cboxwidth</I> wide around the initial
  coordinates and a simple centroiding algorithm  are used to
  compute a more accurate center, before the radial profile is computed.
  <P>
  The azimuths are measured from the first image axis towards the second
  image axis.  The limits may be given in any multiple of 360 degrees
  including negative azimuths.
  <P>
  If the parameter
  <I>append</I> is yes then the new plot will be appended to an existing plot,
  otherwise the device is cleared and a new plot is made. The
  remainder of the parameters control the details of how
  the plot is displayed. If the parameter <B>list</B> is "<TT>yes</TT>" 
  the radial profile is listed on the standard output instead of plotted.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot the radial profile of a star near (123, 234).
  <P>
      cl&gt; pradprof m92red 123 234 
  <P>
  2. Plot the profile around (123, 234) with centering turned off.
  <P>
      cl&gt; pradprof m92red 123 234 center=no
  <P>
  3. List the radial profile and redirect it to a file.
  <P>
      cl&gt; pradprof m92red 123 234 list=yes &gt; profile 
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  proto.imcntr, imexamine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
