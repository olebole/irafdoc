.. _pradprof:

pradprof: Plot or list the radial profile of a stellar object
=============================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pradprof -- plot or list the radial profile of a stellar object
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pradprof input xinit yinit
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of images containing the object of interest.
  </dd>
  </dl>
  <dl>
  <dt><b>xinit, yinit</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xinit' Line='xinit, yinit' -->
  <dd>The initial guess for the  x and y coordinates of the object whose
  profile is to be computed.  If <i>center</i>
  is yes, <i>xinit</i> and <i>yinit</i> are the initial input to the centering 
  algorithm, otherwise <i>xinit</i> and <i>yinit</i> are passed directly to the
  radial profiling algorithm.
  </dd>
  </dl>
  <dl>
  <dt><b>radius = 11</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 11' -->
  <dd>The plotting radius in pixels.
  </dd>
  </dl>
  <dl>
  <dt><b>az1 = 0., az2 = 360.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='az1' Line='az1 = 0., az2 = 360.' -->
  <dd>Azimuth limits for the profile points in degrees.  The azimuth is
  measured from the x or first image axis towards the y or second image
  axis.  Negative azimuths are allowed as are any multiples of 360.
  </dd>
  </dl>
  <dl>
  <dt><b>center = yes </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='center' Line='center = yes ' -->
  <dd>Center the initial coordinates before computing the profile?
  </dd>
  </dl>
  <dl>
  <dt><b>cboxsize = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cboxsize' Line='cboxsize = 5' -->
  <dd>The size of the extraction box of pixels to be used by the centering
  algorithm.
  </dd>
  </dl>
  <dl>
  <dt><b>list = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='list' Line='list = no' -->
  <dd>Make a list of the radial profile, instead of a plot?
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>The graphics device for plotting.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot?
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>The plot title. If title = <tt>"imtitle"</tt>, the image name, <i>xinit</i>, and
  <i>yinit</i> are
  used to construct a default title, otherwise the user specified title is
  used.
  </dd>
  </dl>
  <dl>
  <dt><b>xlabel = <tt>"Radius"</tt>, ylabel = <tt>"Intensity"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "Radius", ylabel = "Intensity"' -->
  <dd>The default labels for the X and Y axes.
  </dd>
  </dl>
  <dl>
  <dt><b>wx1 = INDEF, wx2 = INDEF, wy1 = INDEF, wy2 = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = INDEF, wx2 = INDEF, wy1 = INDEF, wy2 = INDEF' -->
  <dd>The range of user coordinates spanned by the plot. By default the data is
  used to determine the range.
  </dd>
  </dl>
  <dl>
  <dt><b>logx = no, logy = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = yes' -->
  <dd>Use log scaling on the x or y axes of the plot?
  </dd>
  </dl>
  <dl>
  <dt><b>round = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='round' Line='round = no' -->
  <dd>Round the axes minimum and maximum values up to <tt>"nice"</tt> values?
  </dd>
  </dl>
  <dl>
  <dt><b>box = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='box' Line='box = yes' -->
  <dd>Draw axes at the perimeter of the plotting window?
  </dd>
  </dl>
  <dl>
  <dt><b>majrx = 5, minrx = 5, majry = 5, minry = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx = 5, minrx = 5, majry = 5, minry = 5' -->
  <dd>Number of major tick marks on each axis and number of minor tick marks between
  major tick marks. These quantities are ignored if log scaling is in effect
  for an axis.
  </dd>
  </dl>
  <dl>
  <dt><b>ticklabels = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes' -->
  <dd>Label the tick marks?
  </dd>
  </dl>
  <dl>
  <dt><b>fill = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes' -->
  <dd>Fill the output viewport regardless of the device aspect ratio ?
  </dd>
  </dl>
  <dl>
  <dt><b>vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0' -->
  <dd>The NDC coordinates (0.0:1.0) of the device plotting viewport.
  </dd>
  </dl>
  <dl>
  <dt><b>pointmode = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = yes' -->
  <dd>Plot points instead of lines?
  </dd>
  </dl>
  <dl>
  <dt><b>marker = <tt>"plus"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='marker' Line='marker = "plus"' -->
  <dd>Type of marker used in pointmode.
  </dd>
  </dl>
  <dl>
  <dt><b>szmarker = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 1.' -->
  <dd>Size of markers used in pointmode.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  PRADPROF computes a radial profile of length <i>radius</i> pixels
  with a range of azimuths (<i>az1</i> to <i>az2</i>),
  for the object near (<i>xinit</i>, <i>yinit</i>) in the input image(s) 
  <i>input</i>, and plots it on the graphics device <i>graphics</i>.
  If the parameter <i>center</i> is
  <tt>"yes"</tt>, then pixels in a box <i>cboxwidth</i> wide around the initial
  coordinates and a simple centroiding algorithm  are used to
  compute a more accurate center, before the radial profile is computed.
  </p>
  <p>
  The azimuths are measured from the first image axis towards the second
  image axis.  The limits may be given in any multiple of 360 degrees
  including negative azimuths.
  </p>
  <p>
  If the parameter
  <i>append</i> is yes then the new plot will be appended to an existing plot,
  otherwise the device is cleared and a new plot is made. The
  remainder of the parameters control the details of how
  the plot is displayed. If the parameter <b>list</b> is <tt>"yes"</tt> 
  the radial profile is listed on the standard output instead of plotted.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Plot the radial profile of a star near (123, 234).
  </p>
  <p>
      cl&gt; pradprof m92red 123 234 
  </p>
  <p>
  2. Plot the profile around (123, 234) with centering turned off.
  </p>
  <p>
      cl&gt; pradprof m92red 123 234 center=no
  </p>
  <p>
  3. List the radial profile and redirect it to a file.
  </p>
  <p>
      cl&gt; pradprof m92red 123 234 list=yes &gt; profile 
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  proto.imcntr, imexamine
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
