ringavg — Compute pixel averages in concentric rings about given center
=======================================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ringavg (Nov02)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ringavg (Nov02)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ringavg</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ringavg -- compute pixel averages in concentric rings about given center
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ringavg image xc yc
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Image to be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xc">xc, yc</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xc' Line='xc, yc'>
  <DD>Pixel coordinate for center of rings.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_r1">r1 = 0, r2 = 10, dr = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='r1' Line='r1 = 0, r2 = 10, dr = 1'>
  <DD>Rings to be measured.  <I>r1</I> is the inner radius of the first ring,
  <I>r2</I> is the outer radius of the last bin, and <I>dr</I> is the widths
  of the rings.  The values are in units of pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_labels">labels = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='labels' Line='labels = yes'>
  <DD>Print column labels for the output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vebar">vebar = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vebar' Line='vebar = no'>
  <DD>If <I>vebar</I> is yes then the standard deviation and standard error will
  be printed as negative values for use with <B>graph</B>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Pixels are binned into a series of concentric rings centered on a given
  position in the input image.  The rings are defined by an inner radius
  for the first ring, an outer radius for the last ring, and the width
  of the rings.  The statistics of the pixel values in each ring are then 
  computed and list to the standard output.  The output lines consist
  of the inner and outer ring radii, the number of pixels, the average value,
  the standard deviation of the value (corrected for population size), and
  the standard error.  The parameter <I>label</I> selects whether to include
  column labels.
  <P>
  If the ring average are to be plotted with the task <B>graph</B> using
  the option to plot error bars based on the standard deviation or standard
  error then the <I>vebar</I> parameter may be set to write the values as
  negative values are required by that task.
  <P>
  This task is a script and so users may copy it and modify it as desired.
  Because it is a script it will be very slow if r2 becomes large.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Compute the ring averages with labels and output to the terminal.
  <P>
  <PRE>
      cl&gt; ringavg pwimage 17 17
      #  R min    R max     Npix    Average    Std Dev    Std Err
  	0.00     1.00        5      7.336       9.16      4.096
  	1.00     2.00        8     0.2416     0.2219    0.07844
  	2.00     3.00       16     0.3994     0.5327     0.1332
  	3.00     4.00       20    0.06211    0.05491    0.01228
  	4.00     5.00       32     0.0987    0.08469    0.01497
  	5.00     6.00       32    0.06983    0.06125    0.01083
  	6.00     7.00       36     0.0641     0.0839    0.01398
  	7.00     8.00       48    0.06731    0.05373   0.007755
  	8.00     9.00       56    0.06146    0.07601    0.01016
  	9.00    10.00       64    0.05626    0.05846   0.007308
  </PRE>
  <P>
  2.  Plot the ring averages with standard errors used for error bars.
  <P>
  <PRE>
      cl&gt; ringavg pwimage 17 17 label- vebar+ | fields STDIN 2,4,6 |
      &gt;&gt;&gt; graph point+ marker=vebar
  </PRE>
  <P>
  3.  Plot ring averages for galaxy in dev$pix.
  <P>
  <PRE>
      cl&gt; ringavg dev$pix 256 256 r2=100 dr=5 label- | fields STDIN 2,4 |
      &gt;&gt;&gt; graph logy+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pradprof, psfmeasure, radprof
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>