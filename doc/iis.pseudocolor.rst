pseudocolor — Select pseudocolor enhancement
============================================

**Package: iis**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pseudocolor (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv.iis</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pseudocolor (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pseudocolor</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pseudocolor -- select pseudocolor enhancement
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pseudocolor
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_enhancement">enhancement</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='enhancement' Line='enhancement'>
  <DD>Type of pseudocolor enhancement.  The types are:
  <DL>
  <DT><B><A NAME="l_">"<TT>random</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"random"'>
  <DD>A randomly chosen color is assigned to each display level.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"linear"'>
  <DD>The display levels are mapped into a spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>8color</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"8color"'>
  <DD>Eight colors are chosen at random over the range of the display levels.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_window">window = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = yes'>
  <DD>Window the lookup table for the frame after enabling the pseudocolor?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The display levels from the lookup table are mapped into various saturated
  colors to enhance an image.  There is a choice of three color mappings.
  After the pseudocolor enhancement is enabled on the display monitor the
  user may, optionally, adjust the frame lookup table.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  	cl&gt; pseudocolor random
  	cl&gt; pseudocolor 8color
  	cl&gt; pseudocolor linear
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>