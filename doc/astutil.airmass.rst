airmass — Compute the airmass at a given elevation above the horizon
====================================================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>airmass (Mar84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>airmass (Mar84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>airmass</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  airmass -- compute the airmass at a given elevation above horizon
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  airmass elevation
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_elevation">elevation</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='elevation' Line='elevation'>
  <DD>Elevation above horizon in either degrees or radians.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = 750.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 750.0'>
  <DD>Scale factor of the Earth's atmosphere.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radians">radians = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radians' Line='radians = no'>
  <DD>Input elevation in radians instead of degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass'>
  <DD>On output, contains the computed airmass.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_example">EXAMPLE</A></H2>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Compute the airmass at an elevation of 30 degrees above the horizon
  <P>
  <PRE>
  	cl&gt; airmass 30
  	airmass 1.996 at an elevation of 30. degrees (0.5236 radians)
  	above horizon
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
  </BODY>
  </HTML>