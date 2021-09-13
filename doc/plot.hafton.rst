.. _hafton:

hafton — Generate half-tone plots of an image
=============================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hafton -- draw a half tone picture of an image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hafton image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Two dimensional image or image section to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>z1 = 0.0, z2 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = 0.0, z2 = 0.0'>
  <DD>The minimum (z1) and maximum (z2) intensities to be mapped.  If left at the
  default values of 0.0, the full intensity range will be mapped.
  </DD>
  </DL>
  <DL>
  <DT><B>nlevels = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlevels' Line='nlevels = 0'>
  <DD>The number of intensities levels to be shown.  If <B>nlevels = 0</B> or <B>1</B>,
  the maximum of 16 levels is used.
  </DD>
  </DL>
  <DL>
  <DT><B>mapping_function = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mapping_function' Line='mapping_function = "linear"'>
  <DD>A string specifying the image intensity to half tone mapping function.
  The default is linear mapping between <B>z1</B> and <B>z2</B>.  For other
  choices, see the description section below.
  </DD>
  </DL>
  <DL>
  <DT><B>contrast = 0.25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='contrast' Line='contrast = 0.25'>
  <DD>Positive or negative contrast.  Negative contrast is indicated by setting
  <B>contrast</B> to a negative number.  The magnitude of <B>contrast</B> is
  not important unless <B>mapping_function = crtpict</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>perimeter = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='perimeter' Line='perimeter = yes'>
  <DD>Should a <B>crtpict</B> perimeter with labeled tickmarks be drawn around 
  the plot?
  </DD>
  </DL>
  <DL>
  <DT><B>device="<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device="stdgraph"'>
  <DD>Output device for plot.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>The title to be centered above the plot.  By default, the title string from
  the image header is used.
  </DD>
  </DL>
  <DL>
  <DT><B>xres = 64, yres = 64</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xres' Line='xres = 64, yres = 64'>
  <DD>The input image is block averaged or subsampled to this resolution.
  </DD>
  </DL>
  <DL>
  <DT><B>preserve = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='preserve' Line='preserve = yes'>
  <DD>If <B>preserve</B> = yes, the aspect ratio of the image is preserved when
  achieving the resolution specified by <B>xres</B> and <B>yres</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>subsample = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subsample' Line='subsample = no'>
  <DD>Should the image be subsampled (as opposed to block averaged) to achieve the
  specified resolution?
  </DD>
  </DL>
  <DL>
  <DT><B>vx1 = 0.0, vx2 = 0.0, vy1 = 0.0, vy2 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 0.0, vy1 = 0.0, vy2 = 0.0'>
  <DD>The device viewport, in normalized device coordinates (from 0.0 to 1.0
  inclusive).  If not specified by the user, the plot is centered on the viewport.
  </DD>
  </DL>
  <DL>
  <DT><B>fill = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = no'>
  <DD>Should the plot fill the viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>hafton</I> draws a half tone picture of an IRAF image, where varying
  intensities in the image are represented by areas of varying darkness on
  the plot.  Six different mapping functions are available; the desired 
  mapping function is selected with the <B>mapping_function</B> string.
  The types of mapping are:
  <PRE>
  <P>
     linear
     exponential - emphasizes high intensity values.
     logarithmic - emphasizes low intensity values.
     sinusoidal  - emphasizes mid-range values.
     arcsine     - extreme values emphasized at the expense of mid-range.
     crtpict     - linear mapping centered on median intensity.  The slope of
  		 the function is modified by <B>contrast</B>.
  </PRE>
  To speed up the plotting, the resolution of the input image can be 
  decreased to <B>xres</B> by <B>yres</B>.  
  When <B>preserve</B> = yes, <B>hafton</B> automatically reduces the 
  image in both directions by the same factor, which
  is the larger of [ncolumns / xres or nlines / yres].  If the
  aspect ratio is not being preserved, the x and y dimensions are independently
  reduced to the specified resolution.
  No reduction is done if
  <B>xres</B> and <B>yres</B> = 0, if the input image is an image section, or
  if the image is smaller than <B>xres</B> by <B>yres</B>.
  <P>
  If the device viewport is not set by the user, <I>hafton</I> automatically
  sets a viewport centered on the output device.  The default value of
  <B>fill=no</B> means the viewport will be adjusted so that equal
  numbers of image pixels in x and y will occupy equal lengths when plotted.
  That is, when <B>fill=no</B>, a unity aspect
  ratio is enforced, and square images are represented as square plots
  regardless of the device aspect ratio.
  On devices with non square full device
  viewports (e.g., the vt640), a square image will appear extended when
  <B>fill=yes</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Image "<TT>crab.6563</TT>" is plotted in negative contrast, with linear mapping
  between the minimum and maximum image pixel.
  <P>
      cl&gt; hafton crab.6563 contrast=-1
  <P>
  2. The image is plotted in negative contrast using the same mapping
  function as used by the <I>crtpict</I> task.  The resulting plot is
  in negative contrast.
  <P>
      cl&gt; hafton crab.6563 mapping_fun=crt contrast =-0.25
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  To produce a <I>hafton</I> plot on the terminal takes just under 9 cpu
  minutes.  If the output device is the imagen or versatec (or another
  nspp device) the total cpu time is about an hour.  
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  A large number of plotter instructions ( &gt; 100,000 polylines) is generated 
  per frame for square images.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS'  >
  
