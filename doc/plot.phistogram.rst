phistogram — Plot or print the histogram of an image or list
============================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>phistogram (Nov89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>phistogram (Nov89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>phistogram</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  phistogram -- print or plot the histogram of an image or stream of values
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  phistogram input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The name of the image, image subsection, or the text file containing the
  stream of values whose histogram is to be computed. <I>Input</I> may be
  the standard input "<TT>STDIN</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z1">z1 = INDEF, z2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF'>
  <DD>The minimum and maximum values included in the histogram. The image or data
  minimum and maximum values are used by default.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binwidth">binwidth = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = INDEF'>
  <DD>The resolution of the histogram in data units. If <I>binwidth</I> is not defined,
  the parameters <I>nbins</I>, <I>z1</I>, and <I>z2</I> determine the resolution of
  the histogram.
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
  <DD>In the case of integer image data, automatically adjust <I>nbins</I> and
  <I>z2</I> to avoid aliasing effects. Data in text files is not autoscaled.
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
  "<TT>difference</TT>" options are calculated as forward differences, i.e.
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
  <DT><B><A NAME="l_title">title = "<TT>imtitle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>The plot title. If title = "<TT>imtitle</TT>", the image name and title or the
  text file name, and the 
  characteristics of the histogram are included in the title.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xlabel">xlabel = "<TT>Data values</TT>", ylabel = "<TT>Counts</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "Data values", ylabel = "Counts"'>
  <DD>The labels for the X and Y axes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wx1">wx1 = INDEF, wx2 = INDEF, wy1 = 0.0, wy2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = INDEF, wx2 = INDEF, wy1 = 0.0, wy2 = INDEF'>
  <DD>The range of user coordinates spanned by the plot. If either of the x axis
  limits is INDEF the histogram minimum or maximum data values
  are used.  If either of the y axis limits is INDEF,  the 
  minimum or maximum counts in the histogram is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logx">logx = no, logy = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = yes'>
  <DD>Use log scaling on the x or y axes of the plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_round">round = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Round the axes minimum and maximum values up to "<TT>nice</TT>" values?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plot_type">plot_type = "<TT>line</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plot_type' Line='plot_type = "line"'>
  <DD>The style of histogram to plot. The options are "<TT>line</TT>", "<TT>box</TT>" and "<TT>fullbox</TT>".
  If <I>plot_type</I> is "<TT>line</TT>" the histogram data points are connected by
  straight lines; if it is "<TT>box</TT>" a stepped histogram is drawn; if it is "<TT>fullbox</TT>" 
  the histogram lines are drawn to the base of the plot.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_box">box = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='box' Line='box = yes'>
  <DD>Draw axes at the perimeter of the plotting window?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ticklabels">ticklabels = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes'>
  <DD>Label the tick marks?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_majrx">majrx = 5, minrx = 5, majry = 5, minry = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx = 5, minrx = 5, majry = 5, minry = 5'>
  <DD>Number of major tick marks on each axis and number of minor tick marks between
  major tick marks. These quantities are ignored if log scaling is in effect
  for an axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill the output viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vx1">vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0.0, vx2 = 1.0, vy1 = 0.0, vy2 = 1.0'>
  <DD>The NDC coordinates (0.0:1.0) of the device plotting viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pattern">pattern = "<TT>solid</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "solid"'>
  <DD>The type of line used to draw the histogram. The options are "<TT>solid</TT>",
  "<TT>dashed</TT>" "<TT>dotted</TT>", and "<TT>dotdash</TT>". <I>Pattern</I> can be changed when
  appending to an existing plot.
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
  <I>Phistogram</I> computes the histogram of the IRAF image or stream
  of values in the text file specified by
  <I>input</I>, using the parameters <I>binwidth</I>, <I>nbins</I>,
  <I>z1</I> and <I>z2</I>.
  If either <I>z1</I> or <I>z2</I> is undefined the data minimum or
  maximum values define the histogram limits.
  If <I>binwidth</I> is undefined, <I>nbins</I>
  determines the resolution of the histogram. If <I>listout</I> = no,
  the histogram is plotted on
  the graphics device <I>device</I> in the style specified by
  <I>plot_type</I>.  The plot may be log scaled if <I>logy</I> = yes (the
  default) and the input is an IRAF image.  If <I>listout</I> = yes,
  the histogram is printed on the standard output.
  <P>
  In addition to computing the "<TT>normal</TT>" histogram, PHISTOGRAM can also
  calculate the cumulative and the first and second difference histograms
  depending on the value of the <I>hist_type</I> parameter. The options are:
  "<TT>normal</TT>", "<TT>cumulative</TT>", "<TT>difference</TT>", and "<TT>second_difference</TT>".
  <P>
  Each bin of the histogram is defined to be half open at the top.  This
  results in an ambiguity in deciding whether those pixels with z=z2 are
  included in the topmost bin.  This decision is left to the user via the
  <I>top_closed</I> parameter.  This is usually only of concern with integer
  image data and histograms with few bins.
  <P>
  If <B>append</B> is enabled, previous values for <B>box</B>,
  <B>fill</B>, <B>round</B>, the plotting viewport (<B>vx1</B>, <B>vx2</B>, 
  <B>vy1</B>, <B>vy2</B>), and the plotting window (<B>wx1</B>, <B>wx2</B>, 
  <B>wy1</B>, <B>wy2</B>) are used.
  <P>
  By default, the plot drawn will fill the device viewport.  Setting
  the value of <B>fill</B>  to "<TT>no</TT>" means the viewport will be adjusted so 
  that equal numbers of data values in x and y will occupy equal lengths 
  when plotted.  That is, when <B>fill = no</B>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by
  PHISTOGRAM appears extended in the x direction unless <B>fill</B> = no.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Output the histogram of an image to a file.
  <P>
      cl&gt; phist M51.imh li+ nbins=100 &gt; fits1.hst
  <P>
  2. Plot the histogram of an image using only values from 0 to 2000.
  <P>
      cl&gt; phist M31.imh nbins=100 z1=0. z2=2000.
  <P>
  3. Ditto, but set the histogram resolution explicitly to avoid
  smoothing the histogram.
  <P>
      cl&gt; phist M31.imh z1=0 z2=2000 nbins=2001
  <P>
  4. Plot the cumulative histogram.  This is most useful for images with
  fairly flat "<TT>normal</TT>" histograms.
  <P>
      cl&gt; phist R50.imh hist=cum
  <P>
  5. Plot the histogram of a stream of values in the textfile "<TT>list</TT>".
  <P>
      cl&gt; phist list
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