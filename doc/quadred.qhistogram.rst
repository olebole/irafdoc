qhistogram — Make histogram of multi-amplifier CCD image
========================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>qhistogram (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>qhistogram (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>qhistogram</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  qhistogram -- Compute and print histogram for multi-amp data
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  qhistogram images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of image names in <B>quadformat</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_window">window = "<TT>datasec</TT>" (datasec|trimsec|biassec)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)'>
  <DD>Type of section to use for histogram.  The choices are "<TT>datasec</TT>" for the
  amplifier section which includes the bias if any is present, "<TT>trimsec</TT>" for
  the trim section, and "<TT>biassec</TT>" for the bias section.
  </DD>
  </DL>
  <P>
  The remaining parameters come from the <B>imhistogram</B> task.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This script tasks uses the <B>quadsections</B> task to break the
  <B>quadformat</B> data into separate sections and runs the <B>imhistogram</B>
  task on the sections.  The graphics is collected onto a single page.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. To graph the histograms (default behavior).
  <P>
  <PRE>
      qu&gt; qhist quad0072
      [graph appears]
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, quadsections, imhistogram
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>