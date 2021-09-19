.. _phistogram:

phistogram: Plot or print the histogram of an image or list
===========================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  phistogram -- print or plot the histogram of an image or stream of values
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  phistogram input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The name of the image, image subsection, or the text file containing the
  stream of values whose histogram is to be computed. <i>Input</i> may be
  the standard input <tt>"STDIN"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>z1 = INDEF, z2 = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF' -->
  <dd>The minimum and maximum values included in the histogram. The image or data
  minimum and maximum values are used by default.
  </dd>
  </dl>
  <dl>
  <dt><b>binwidth = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = INDEF' -->
  <dd>The resolution of the histogram in data units. If <i>binwidth</i> is not defined,
  the parameters <i>nbins</i>, <i>z1</i>, and <i>z2</i> determine the resolution of
  the histogram.
  </dd>
  </dl>
  <dl>
  <dt><b>nbins = 512</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins = 512' -->
  <dd>The number of bins in, or resolution of, the histogram. 
  The <i>nbins</i> parameter is overridden if <i>binwidth</i> is defined.
  </dd>
  </dl>
  <dl>
  <dt><b>autoscale = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='autoscale' Line='autoscale = yes' -->
  <dd>In the case of integer image data, automatically adjust <i>nbins</i> and
  <i>z2</i> to avoid aliasing effects. Data in text files is not autoscaled.
  </dd>
  </dl>
  <dl>
  <dt><b>top_closed = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='top_closed' Line='top_closed = no' -->
  <dd>Include z2 in the top bin?  Each bin of the histogram is a subinterval
  that is half open at the top.  <i>Top_closed</i> decides whether those
  pixels with values equal to z2 are to be counted in the histogram.  If
  <b>top_closed</b> is yes, the top bin will be larger than the other bins.
  </dd>
  </dl>
  <dl>
  <dt><b>hist_type = <tt>"normal"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hist_type' Line='hist_type = "normal"' -->
  <dd>The type of histogram to plot or list.  The choices are <tt>"normal"</tt>,
  <tt>"cumulative"</tt>, <tt>"difference"</tt>, or <tt>"second_difference"</tt>.  The two
  <tt>"difference"</tt> options are calculated as forward differences, i.e.
  diff[n] = hist[n+1] - hist[n].
  </dd>
  </dl>
  <dl>
  <dt><b>listout = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='listout' Line='listout = no' -->
  <dd>List instead of plot the histogram?  The list is never log scaled.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>The plot title. If title = <tt>"imtitle"</tt>, the image name and title or the
  text file name, and the 
  characteristics of the histogram are included in the title.
  </dd>
  </dl>
  <dl>
  <dt><b>xlabel = <tt>"Data values"</tt>, ylabel = <tt>"Counts"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "Data values", ylabel = "Counts"' -->
  <dd>The labels for the X and Y axes.
  </dd>
  </dl>
  <dl>
  <dt><b>wx1 = INDEF, wx2 = INDEF, wy1 = 0.0, wy2 = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = INDEF, wx2 = INDEF, wy1 = 0.0, wy2 = INDEF' -->
  <dd>The range of user coordinates spanned by the plot. If either of the x axis
  limits is INDEF the histogram minimum or maximum data values
  are used.  If either of the y axis limits is INDEF,  the 
  minimum or maximum counts in the histogram is used.
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
  <dt><b>plot_type = <tt>"line"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='plot_type' Line='plot_type = "line"' -->
  <dd>The style of histogram to plot. The options are <tt>"line"</tt>, <tt>"box"</tt> and <tt>"fullbox"</tt>.
  If <i>plot_type</i> is <tt>"line"</tt> the histogram data points are connected by
  straight lines; if it is <tt>"box"</tt> a stepped histogram is drawn; if it is <tt>"fullbox"</tt> 
  the histogram lines are drawn to the base of the plot.
  </dd>
  </dl>
  <dl>
  <dt><b>box = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='box' Line='box = yes' -->
  <dd>Draw axes at the perimeter of the plotting window?
  </dd>
  </dl>
  <dl>
  <dt><b>ticklabels = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes' -->
  <dd>Label the tick marks?
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
  <dt><b>fill = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes' -->
  <dd>Fill the output viewport regardless of the device aspect ratio?
  </dd>
  </dl>
  <dl>
  <dt><b>vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0' -->
  <dd>The NDC coordinates (0.0:1.0) of the device plotting viewport.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot?
  </dd>
  </dl>
  <dl>
  <dt><b>pattern = <tt>"solid"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "solid"' -->
  <dd>The type of line used to draw the histogram. The options are <tt>"solid"</tt>,
  <tt>"dashed"</tt> <tt>"dotted"</tt>, and <tt>"dotdash"</tt>. <i>Pattern</i> can be changed when
  appending to an existing plot.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>The output graphics device.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Phistogram</i> computes the histogram of the IRAF image or stream
  of values in the text file specified by
  <i>input</i>, using the parameters <i>binwidth</i>, <i>nbins</i>,
  <i>z1</i> and <i>z2</i>.
  If either <i>z1</i> or <i>z2</i> is undefined the data minimum or
  maximum values define the histogram limits.
  If <i>binwidth</i> is undefined, <i>nbins</i>
  determines the resolution of the histogram. If <i>listout</i> = no,
  the histogram is plotted on
  the graphics device <i>device</i> in the style specified by
  <i>plot_type</i>.  The plot may be log scaled if <i>logy</i> = yes (the
  default) and the input is an IRAF image.  If <i>listout</i> = yes,
  the histogram is printed on the standard output.
  </p>
  <p>
  In addition to computing the <tt>"normal"</tt> histogram, PHISTOGRAM can also
  calculate the cumulative and the first and second difference histograms
  depending on the value of the <i>hist_type</i> parameter. The options are:
  <tt>"normal"</tt>, <tt>"cumulative"</tt>, <tt>"difference"</tt>, and <tt>"second_difference"</tt>.
  </p>
  <p>
  Each bin of the histogram is defined to be half open at the top.  This
  results in an ambiguity in deciding whether those pixels with z=z2 are
  included in the topmost bin.  This decision is left to the user via the
  <i>top_closed</i> parameter.  This is usually only of concern with integer
  image data and histograms with few bins.
  </p>
  <p>
  If <b>append</b> is enabled, previous values for <b>box</b>,
  <b>fill</b>, <b>round</b>, the plotting viewport (<b>vx1</b>, <b>vx2</b>, 
  <b>vy1</b>, <b>vy2</b>), and the plotting window (<b>wx1</b>, <b>wx2</b>, 
  <b>wy1</b>, <b>wy2</b>) are used.
  </p>
  <p>
  By default, the plot drawn will fill the device viewport.  Setting
  the value of <b>fill</b>  to <tt>"no"</tt> means the viewport will be adjusted so 
  that equal numbers of data values in x and y will occupy equal lengths 
  when plotted.  That is, when <b>fill = no</b>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by
  PHISTOGRAM appears extended in the x direction unless <b>fill</b> = no.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Output the histogram of an image to a file.
  </p>
  <p>
      cl&gt; phist M51.imh li+ nbins=100 &gt; fits1.hst
  </p>
  <p>
  2. Plot the histogram of an image using only values from 0 to 2000.
  </p>
  <p>
      cl&gt; phist M31.imh nbins=100 z1=0. z2=2000.
  </p>
  <p>
  3. Ditto, but set the histogram resolution explicitly to avoid
  smoothing the histogram.
  </p>
  <p>
      cl&gt; phist M31.imh z1=0 z2=2000 nbins=2001
  </p>
  <p>
  4. Plot the cumulative histogram.  This is most useful for images with
  fairly flat <tt>"normal"</tt> histograms.
  </p>
  <p>
      cl&gt; phist R50.imh hist=cum
  </p>
  <p>
  5. Plot the histogram of a stream of values in the textfile <tt>"list"</tt>.
  </p>
  <p>
      cl&gt; phist list
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  If the resolution of the histogram (number of bins) is a non-integral multiple
  of the intensity resolution of the data (number of possible intensity values),
  then <i>aliasing</i> can occur.  The effect is to cause periodic zero dropouts
  (for an oversampled histogram) or excess-valued bins (for a slightly
  undersampled histogram).  The <i>autoscaling</i> feature, if enabled, will
  adjust the histogram parameters to avoid such aliasing effects for integer
  data.  This is not possible for floating point data, however, in which case
  aliasing is certainly possible and can only be avoided by manually adjusting
  the histogram parameters.  One should also be aware that <i>smoothing</i> of
  the histogram will occur whenever the data range exceeds the histogram
  resolution.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  listpixels, plot.graph, proto.mkhistogram
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
