velvect — Plot representation of a velocity field
=================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>velvect (Sep85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>velvect (Sep85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>velvect</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  velvect -- two dimensional velocity field plot
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  velvect uimage vimage
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_uimage">uimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='uimage' Line='uimage'>
  <DD>Name of image containing u components of the velocity field.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vimage">vimage </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vimage' Line='vimage '>
  <DD>Name of image containing v components of the velocity field.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = stdgraph</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = stdgraph'>
  <DD>Output device for plot.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = "<TT>imtitle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>Title to be centered over the plot.  By default, it will be the title
  from the image header of the <B>uimage</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an old plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print warning messages?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>velvect</I> draws a representation of a two-dimensional velocity
  field by drawing arrows from each data location.  The length of the arrow
  is proportional to the strength of the field at that location and the direction
  of the arrow indicates the direction of the flow at that location.  The
  two images <I>uimage</I> and <I>vimage</I> contain the velocity field to be
  plotted.  The vector at the point (i,j) has:
  <P>
  <PRE>
      magnitude = sqrt (uimage(i,j)**2 + vimage(i,j)**2)
      direction = atan2 (vimage(i,j), uimage(i,j))
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Make a vector plot from the two images "<TT>crab.blue</TT>" and "<TT>crab.red</TT>".
  <P>
      cl&gt; velvect crab.blue crab.red
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>