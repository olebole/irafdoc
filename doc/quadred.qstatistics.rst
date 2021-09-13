qstatistics — Calculate image statistics for multi-amplifier CCD images
=======================================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>qstatistics (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>qstatistics (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>qstatistics</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  qstatistics -- Compute and print statistics for multi-amp data
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  qstatistics images
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
  <DD>Type of section to output.  The choices are "<TT>datasec</TT>" for the amplifier
  section which includes the bias if any is present, "<TT>trimsec</TT>" for the trim
  section, and "<TT>biassec</TT>" for the bias section.
  </DD>
  </DL>
  <P>
  The remaining parameters come from the <B>imstatistics</B> task.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This script tasks uses the <B>quadsections</B> task to break the
  <B>quadformat</B> data into separate sections and runs the <B>imstatistics</B>
  task on the sections.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. To compute the mean and stddev of the data section.
  <P>
  <PRE>
      qu&gt; qstat quad0072 fields=image,mean,stddev
      #               IMAGE      MEAN    STDDEV
       quad0072[1:1034,1:1024]     5537.     2647.
       quad0072[1163:2196,1:1024]     6210.     5439.
       quad0072[1:1034,1025:2048]     5364.     2535.
       quad0072[1163:2196,1025:2048]     5862.     1327.
  </PRE>
  <P>
  2. To compute the mean and stdev of the bias section.
  <P>
  <PRE>
      qu&gt; qstat quad0072 fields=image,mean,stddev window=biassec
      #               IMAGE      MEAN    STDDEV
       quad0072[1045:1098,1:1024]      713.     1.272
       quad0072[1099:1152,1:1024]     516.2     1.425
       quad0072[1045:1098,1025:2048]     554.3     1.347
       quad0072[1099:1152,1025:2048]     530.3     1.377
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, quadsections, imstatistics
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>