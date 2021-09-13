.. _imdkern:

imdkern — Image display device (IMD) graphics kernel
====================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imdkern -- image display device graphics kernel
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imdkern input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdimage</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdimage"'>
  <DD>The output device.
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored when <B>generic</B> = yes (as when
  the kernel is called automatically by the system during plotting).
  </DD>
  </DL>
  <DL>
  <DT><B>frame = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame = 0'>
  <DD>The display frame to be drawn into.  If the value given is less than or
  equal to zero, the plot is drawn into the frame currently being displayed.
  </DD>
  </DL>
  <DL>
  <DT><B>color = 205</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='color' Line='color = 205'>
  <DD>The pixel value to be used for graphics.  The value required to generate
  a given color is device dependent.  For IMTOOL and compatible display servers
  (such as SAOIMAGE) black=202, white=203, red=204, green=205, blue=206,
  yellow=207, and so on through 217.  (The <I>tvmark</I> help page contains
  a full listing of the available colors).
  </DD>
  </DL>
  <DL>
  <DT><B>debug = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no'>
  <DD>If <B>debug</B> = yes, the graphics instructions are decoded and printed
  during processing.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, the elements of polylines, cell arrays, etc. will
  be printed in debug mode.
  </DD>
  </DL>
  <DL>
  <DT><B>gkiunits = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no'>
  <DD>By default, coordinates are printed in NDC rather than GKI units.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>imdkern</I> graphics kernel is used to draw graphics into the image
  display.  To overlay a plot on a displayed image, one first displays the
  image, then runs <I>imdkern</I> to overlay the graphics on the displayed image.
  <I>imdkern</I> always overlays a plot on whatever is currently in the display
  frame buffer.  To erase the graphics drawn by <I>imdkern</I>, one must
  redisplay the frame using <I>display</I> or a similar program, or erase the
  frame entirely using <I>tv.erase</I>.
  <P>
  Like all IRAF graphics kernels, <I>imdkern</I> may be called either explicitly
  as a task, to plot a graphics metacode file, or implicitly when the output
  of a graphics task is directed to a device which uses the IMD kernel.
  The standard IRAF <I>graphcap</I> file defines the following logical IMD
  graphics devices:
  <P>
  <PRE>
  	imd|imdkern	same as imdg
  	imdw		output to stdimage, frame=0, color=white
  	imdr		output to stdimage, frame=0, color=red
  	imdg		output to stdimage, frame=0, color=green
  	imdb		output to stdimage, frame=0, color=blue
  	imdy		output to stdimage, frame=0, color=yellow
  </PRE>
  <P>
  As noted earlier, <I>frame=0</I> causes the graph to be plotted in the
  currently displayed image display frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Capture the output of the <I>prow</I> task in a metacode file and
  plot in image display frame 2.
  <P>
  <PRE>
      cl&gt; prow dev$pix 101 &gt;G mc
      cl&gt; imdkern mc frame=2
  </PRE>
  <P>
  2. Display dev$pix in image display frame 1 and overlay a contour plot,
  drawing the contour plot overlaid on the image in green.
  <P>
  <PRE>
      cl&gt; display dev$pix 1
      cl&gt; contour dev$pix \<BR>
      &gt;&gt;&gt; xres=256 yres=256 perim- fill+ label- ceil=500 dev=imdg
  </PRE>
  <P>
  Note that a higher than normal resolution contour plot is generated to
  avoid the contour placement errors that occur when a large block averaging
  factor is used to generate the contour map (this can make contours drawn
  around objects such as stars appear to not be centered on the object).
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The IMD interface, used by this task to draw the graphics, requires that the
  display frame buffer be read and edited in the client address space, hence
  drawing is slow compared to having the display server draw the graphics.
  This effect is especially noticeable when the display is accessed remotely
  over the network.  Also, because the graph is drawn in the client
  (i.e., in <I>imdkern</I>) the GIO fonts must be used for character drawing,
  so characters will not be as well formed as when display server character
  generation is used.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tvmark, display
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
