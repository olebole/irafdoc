.. _surface:

surface: Make a surface plot of an image
========================================

**Package: plot**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  surface image
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>Image or image section to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>floor = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='floor' Line='floor = INDEF' -->
  <dd>Data values below <b>floor</b> are clipped.  If <b>floor = INDEF</b>, the data
  minimum is used for the floor.
  </dd>
  </dl>
  <dl>
  <dt><b>ceiling = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ceiling' Line='ceiling = INDEF' -->
  <dd>Data values above <b>ceiling</b> are clipped.  If <b>ceiling = INDEF</b>, the
  data maximum is used for the ceiling.
  </dd>
  </dl>
  <dl>
  <dt><b>angh = -33.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='angh' Line='angh = -33.0' -->
  <dd>Horizontal viewing angle, degrees.
  </dd>
  </dl>
  <dl>
  <dt><b>angv = 25.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='angv' Line='angv = 25.0' -->
  <dd>Vertical viewing angle, degrees.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <span style="font-family: monospace;">"stdgraph"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>Output device (<b>stdgraph</b>, <b>stdplot</b>, or the name of a physical
  device).
  </dd>
  </dl>
  <dl>
  <dt><b>title = <span style="font-family: monospace;">"imtitle"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>A title string is centered above the plot.  The user can specify a title
  string; the default is the image title.
  </dd>
  </dl>
  <dl>
  <dt><b>label = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='label' Line='label = no' -->
  <dd>The axes are drawn and the corner points of the plotting area are labeled 
  if <b>label</b> = yes.
  </dd>
  </dl>
  <dl>
  <dt><b>xres = 64, yres = 64</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xres' Line='xres = 64, yres = 64' -->
  <dd>The input image is block averaged or subsampled to this resolution.
  </dd>
  </dl>
  <dl>
  <dt><b>preserve = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='preserve' Line='preserve = yes' -->
  <dd>If <b>preserve</b> = yes, the aspect ratio of the image is preserved when
  achieving the resolution specified by <b>xres</b> and <b>yres</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>subsample = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='subsample' Line='subsample = no' -->
  <dd>The resolution specified by <b>xres</b>, <b>yres</b> is achieved by block
  averaging unless <b>subsample</b> = yes.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <b>Surface</b> draws a pseudo-three dimensional perspective of an image
  section.  Hidden lines are removed.  The surface may be viewed from any
  angle.  Subsampling or block averaging is used to achieve the resolution
  specified.  A labeled perimeter is optionally drawn around the plot.
  </p>
  <p>
  To speed up the plot, the resolution of the image can be decreased to
  <b>xres</b> by <b>yres</b>.  When <b>preserve</b> = yes, <b>surface</b> 
  automatically reduces the image in both directions by the same factor, which
  is the larger of [ncolumns / xres or nlines / yres].  If the
  aspect ratio is not being preserved, the x and y dimensions are independently
  reduced to the specified resolution.
  No reduction is done if
  <b>xres</b> and <b>yres</b> = 0, if the input image is an image section, or if
  the image is smaller than <b>xres</b> by <b>yres</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Surface plot of a 512 square image.  With the default values of <b>xres</b>
  and <b>yres</b>, the image would be block averaged by a factor of 8 in x and y.
  </p>
  <p>
      cl&gt; surface crab.5009
  </p>
  <p>
  2. Look at the bottom of the surface, but subsample rather that block average
  to decrease resolution and speed things up.  Also, the output device will
  be the plotter, and the job will run in the background:
  </p>
  <p>
      cl&gt; surface crab.5009 angv=-30 subsample+ device=stdplot &amp;
  </p>
  <p>
  3. Surface plot of band 4 of an image cube.  Since the image is specified using
  image section notation, no block averaging or subsampling will be done.
  </p>
  <p>
      cl&gt; surface cube[*,*,4]
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  The time required by <i>surface</i> depends on image size and resolution.
  A surface plot of a
  512 square image block averaged to 64 square requires 30 cpu seconds.  The
  same image subsampled would take 23 seconds to plot.  
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  It should be possible to input the surface in list form. 
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  contour, graph
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
