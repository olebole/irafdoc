imscale — Scale an image to a specified (windowed) mean
=======================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imscale (Aug84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imscale (Aug84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imscale</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imscale -- Scale an image to a specified windowed mean
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  imscale input output mean
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image to be scaled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output scaled image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mean">mean</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mean' Line='mean'>
  <DD>Scale the output image to this mean value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lower">lower = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Lower limit of window for calculating the input image mean.  INDEF corresponds
  to the minimum possible pixel value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Upper limit of window for calculating the input image mean.  INDEF corresponds
  to the maximum possible pixel value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print the calculated input and output image means.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The mean of the <I>input</I> image between the limits <I>lower</I>
  and <I>upper</I> is computed.  The image is then scaled to the
  specified output <I>mean</I>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To scale an image to a unit mean excluding deviant points below
  1000 and above 5000.
  <P>
  <PRE>
      cl&gt; imscale calib flat 1 lower=1000 upper=5000
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>