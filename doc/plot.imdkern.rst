.. _imdkern:

imdkern: Image display device (IMD) graphics kernel
===================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imdkern -- image display device graphics kernel
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imdkern input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input metacode files.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <span style="font-family: monospace;">"stdimage"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdimage"' -->
  <dd>The output device.
  </dd>
  </dl>
  <dl>
  <dt><b>generic = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no' -->
  <dd>The remaining parameters are ignored when <b>generic</b> = yes (as when
  the kernel is called automatically by the system during plotting).
  </dd>
  </dl>
  <dl>
  <dt><b>frame = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame' Line='frame = 0' -->
  <dd>The display frame to be drawn into.  If the value given is less than or
  equal to zero, the plot is drawn into the frame currently being displayed.
  </dd>
  </dl>
  <dl>
  <dt><b>color = 205</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='color' Line='color = 205' -->
  <dd>The pixel value to be used for graphics.  The value required to generate
  a given color is device dependent.  For IMTOOL and compatible display servers
  (such as SAOIMAGE) black=202, white=203, red=204, green=205, blue=206,
  yellow=207, and so on through 217.  (The <i>tvmark</i> help page contains
  a full listing of the available colors).
  </dd>
  </dl>
  <dl>
  <dt><b>debug = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no' -->
  <dd>If <b>debug</b> = yes, the graphics instructions are decoded and printed
  during processing.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If <b>verbose</b> = yes, the elements of polylines, cell arrays, etc. will
  be printed in debug mode.
  </dd>
  </dl>
  <dl>
  <dt><b>gkiunits = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no' -->
  <dd>By default, coordinates are printed in NDC rather than GKI units.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>imdkern</i> graphics kernel is used to draw graphics into the image
  display.  To overlay a plot on a displayed image, one first displays the
  image, then runs <i>imdkern</i> to overlay the graphics on the displayed image.
  <i>imdkern</i> always overlays a plot on whatever is currently in the display
  frame buffer.  To erase the graphics drawn by <i>imdkern</i>, one must
  redisplay the frame using <i>display</i> or a similar program, or erase the
  frame entirely using <i>tv.erase</i>.
  </p>
  <p>
  Like all IRAF graphics kernels, <i>imdkern</i> may be called either explicitly
  as a task, to plot a graphics metacode file, or implicitly when the output
  of a graphics task is directed to a device which uses the IMD kernel.
  The standard IRAF <i>graphcap</i> file defines the following logical IMD
  graphics devices:
  </p>
  <pre>
  	imd|imdkern	same as imdg
  	imdw		output to stdimage, frame=0, color=white
  	imdr		output to stdimage, frame=0, color=red
  	imdg		output to stdimage, frame=0, color=green
  	imdb		output to stdimage, frame=0, color=blue
  	imdy		output to stdimage, frame=0, color=yellow
  </pre>
  <p>
  As noted earlier, <i>frame=0</i> causes the graph to be plotted in the
  currently displayed image display frame.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Capture the output of the <i>prow</i> task in a metacode file and
  plot in image display frame 2.
  </p>
  <pre>
      cl&gt; prow dev$pix 101 &gt;G mc
      cl&gt; imdkern mc frame=2
  </pre>
  <p>
  2. Display dev$pix in image display frame 1 and overlay a contour plot,
  drawing the contour plot overlaid on the image in green.
  </p>
  <pre>
      cl&gt; display dev$pix 1
      cl&gt; contour dev$pix \<br>
      &gt;&gt;&gt; xres=256 yres=256 perim- fill+ label- ceil=500 dev=imdg
  </pre>
  <p>
  Note that a higher than normal resolution contour plot is generated to
  avoid the contour placement errors that occur when a large block averaging
  factor is used to generate the contour map (this can make contours drawn
  around objects such as stars appear to not be centered on the object).
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The IMD interface, used by this task to draw the graphics, requires that the
  display frame buffer be read and edited in the client address space, hence
  drawing is slow compared to having the display server draw the graphics.
  This effect is especially noticeable when the display is accessed remotely
  over the network.  Also, because the graph is drawn in the client
  (i.e., in <i>imdkern</i>) the GIO fonts must be used for character drawing,
  so characters will not be as well formed as when display server character
  generation is used.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  tvmark, display
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
