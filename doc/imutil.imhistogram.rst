imhistogram — Compute and plot or print an image histogram
==========================================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imhistogram (Nov89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imhistogram (Nov89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imhistogram</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imhistogram -- print or plot the histogram of an image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imhistogram image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The name of the image or image subsection whose histogram is to be calculated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z1">z1 = INDEF, z2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF'>
  <DD>The minimum and maximum histogram intensity.  The image minimum and maximum
  pixel values are used by default.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binwidth">binwidth = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = INDEF'>
  <DD>The resolution of the histogram in counts. If <I>binwidth</I> is not defined,
  the parameter <I>nbins</I> determines the histogram resolution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbins">nbins = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins = 512'>
  <DD>The number of bins in, or resolution of, the histogram. 
  The <I>nbins</I> parameter is overridden if <I>binwidth</I> is defined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_autoscale">autoscale = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autoscale' Line='autoscale = yes'>
  <DD>In the case of integer data, automatically adjust <I>nbins</I> and
  <I>z2</I> to avoid aliasing effects.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_top_closed">top_closed = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='top_closed' Line='top_closed = no'>
  <DD>Include z2 in the top bin?  Each bin of the histogram is a subinterval
  that is half open at the top.  <I>Top_closed</I> decides whether those
  pixels with values equal to z2 are to be counted in the histogram.  If
  <B>top_closed</B> is yes, the top bin will be larger than the other bins.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hist_type">hist_type = "<TT>normal</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hist_type' Line='hist_type = "normal"'>
  <DD>The type of histogram to plot or list.  The choices are "<TT>normal</TT>",
  "<TT>cumulative</TT>", "<TT>difference</TT>", or "<TT>second_difference</TT>".  The two
  "<TT>difference</TT>" options are calculated as forward differences, i.e.,
  diff[n] = hist[n+1] - hist[n].
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listout">listout = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listout' Line='listout = no'>
  <DD>List instead of plot the histogram?  The list is never log scaled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plot_type">plot_type = "<TT>line</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plot_type' Line='plot_type = "line"'>
  <DD>The plot vector type. The options are "<TT>line</TT>" and "<TT>box</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logy">logy = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logy' Line='logy = yes'>
  <DD>Use log scaling on the y-axis of the plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output graphics device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>imhistogram</I> calculates the histogram of the IRAF image
  <I>image</I> using the parameters <I>nbins</I>, <I>z1</I> and <I>z2</I>.
  If either <I>z1</I> or <I>z2</I> is undefined the image minimum or
  maximum is used.  If <I>listout</I> = no, the histogram is plotted on
  the graphics device <I>device</I> in the vector mode specified by
  <I>plot_type</I>.  The plot may be log scaled if <I>logy</I> = yes (the
  default).  If <I>listout</I> = yes, the histogram is listed on the
  standard output.
  <P>
  In addition to producing the "<TT>normal</TT>" histogram, the task will also
  calculate cumulative and marginal (forward difference) histograms
  depending on the choice of the <I>hist_type</I> parameter (choices
  are:  "<TT>normal</TT>", "<TT>cumulative</TT>", "<TT>difference</TT>", and "<TT>second_difference</TT>").
  The plot will be labeled by the type of histogram as well as the image
  name and title and the binning parameters.
  <P>
  Each bin of the histogram is defined to be half open at the top.  This
  results in an ambiguity deciding whether those pixels with z=z2 are
  included in the topmost bin.  This decision is left to the user via the
  <I>top_closed</I> parameter.  This is usually only important with integer
  images and histograms with few bins.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Output the histogram of an image to a file.
  <P>
      cl&gt; imhist M51.imh li+ nbins=100 &gt; fits1.hst
  <P>
  2. Plot the histogram of another image between the values 0 and 2000.
  <P>
      cl&gt; imhist M31.imh nbins=100 z1=0. z2=2000.
  <P>
  3. Ditto, but set the histogram resolution explicitly to avoid
  smoothing the histogram.
  <P>
      cl&gt; imhist M31.imh nbins=100 z1=0 z2=2000 nbins=2001
  <P>
  4. Plot the cumulative histogram.  This is most useful for images with
  fairly flat "<TT>normal</TT>" histograms.
  <P>
      cl&gt; imhist R50.imh hist=cum
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If the resolution of the histogram (number of bins) is a non-integral multiple
  of the intensity resolution of the data (number of possible intensity values),
  then <I>aliasing</I> can occur.  The effect is to cause periodic zero dropouts
  (for an oversampled histogram) or excess-valued bins (for a slightly
  undersampled histogram).  The <I>autoscaling</I> feature, if enabled, will
  adjust the histogram parameters to avoid such aliasing effects for integer
  data.  This is not possible for floating point data, however, in which case
  aliasing is certainly possible and can only be avoided by manually adjusting
  the histogram parameters.  One should also be aware that <I>smoothing</I> of
  the histogram will occur whenever the data range exceeds the histogram
  resolution.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  listpixels, plot.graph, proto.mkhistogram
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>