.. _imhistogram:

imhistogram: Compute and plot or print an image histogram
=========================================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imhistogram -- print or plot the histogram of an image
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imhistogram image
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>The name of the image or image subsection whose histogram is to be calculated.
  </dd>
  </dl>
  <dl>
  <dt><b>z1 = INDEF, z2 = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF' -->
  <dd>The minimum and maximum histogram intensity.  The image minimum and maximum
  pixel values are used by default.
  </dd>
  </dl>
  <dl>
  <dt><b>binwidth = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = INDEF' -->
  <dd>The resolution of the histogram in counts. If <i>binwidth</i> is not defined,
  the parameter <i>nbins</i> determines the histogram resolution.
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
  <dd>In the case of integer data, automatically adjust <i>nbins</i> and
  <i>z2</i> to avoid aliasing effects.
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
  <dt><b>hist_type = <span style="font-family: monospace;">"normal"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hist_type' Line='hist_type = "normal"' -->
  <dd>The type of histogram to plot or list.  The choices are <span style="font-family: monospace;">"normal"</span>,
  <span style="font-family: monospace;">"cumulative"</span>, <span style="font-family: monospace;">"difference"</span>, or <span style="font-family: monospace;">"second_difference"</span>.  The two
  <span style="font-family: monospace;">"difference"</span> options are calculated as forward differences, i.e.,
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
  <dt><b>plot_type = <span style="font-family: monospace;">"line"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='plot_type' Line='plot_type = "line"' -->
  <dd>The plot vector type. The options are <span style="font-family: monospace;">"line"</span> and <span style="font-family: monospace;">"box"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>logy = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logy' Line='logy = yes' -->
  <dd>Use log scaling on the y-axis of the plot?
  </dd>
  </dl>
  <dl>
  <dt><b>device = <span style="font-family: monospace;">"stdgraph"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>The output graphics device.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>imhistogram</i> calculates the histogram of the IRAF image
  <i>image</i> using the parameters <i>nbins</i>, <i>z1</i> and <i>z2</i>.
  If either <i>z1</i> or <i>z2</i> is undefined the image minimum or
  maximum is used.  If <i>listout</i> = no, the histogram is plotted on
  the graphics device <i>device</i> in the vector mode specified by
  <i>plot_type</i>.  The plot may be log scaled if <i>logy</i> = yes (the
  default).  If <i>listout</i> = yes, the histogram is listed on the
  standard output.
  </p>
  <p>
  In addition to producing the <span style="font-family: monospace;">"normal"</span> histogram, the task will also
  calculate cumulative and marginal (forward difference) histograms
  depending on the choice of the <i>hist_type</i> parameter (choices
  are:  <span style="font-family: monospace;">"normal"</span>, <span style="font-family: monospace;">"cumulative"</span>, <span style="font-family: monospace;">"difference"</span>, and <span style="font-family: monospace;">"second_difference"</span>).
  The plot will be labeled by the type of histogram as well as the image
  name and title and the binning parameters.
  </p>
  <p>
  Each bin of the histogram is defined to be half open at the top.  This
  results in an ambiguity deciding whether those pixels with z=z2 are
  included in the topmost bin.  This decision is left to the user via the
  <i>top_closed</i> parameter.  This is usually only important with integer
  images and histograms with few bins.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Output the histogram of an image to a file.
  </p>
  <p>
      cl&gt; imhist M51.imh li+ nbins=100 &gt; fits1.hst
  </p>
  <p>
  2. Plot the histogram of another image between the values 0 and 2000.
  </p>
  <p>
      cl&gt; imhist M31.imh nbins=100 z1=0. z2=2000.
  </p>
  <p>
  3. Ditto, but set the histogram resolution explicitly to avoid
  smoothing the histogram.
  </p>
  <p>
      cl&gt; imhist M31.imh nbins=100 z1=0 z2=2000 nbins=2001
  </p>
  <p>
  4. Plot the cumulative histogram.  This is most useful for images with
  fairly flat <span style="font-family: monospace;">"normal"</span> histograms.
  </p>
  <p>
      cl&gt; imhist R50.imh hist=cum
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
  
