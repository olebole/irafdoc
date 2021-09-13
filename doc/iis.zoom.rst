zoom — Zoom in on the image (change magnification)
==================================================

**Package: iis**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>zoom (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv.iis</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>zoom (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>zoom</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  zoom - zoom in on the image (change magnification)
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  zoom
  <DL>
  <DT><B><A NAME="l_zoom_factor">zoom_factor</A></B></DT>
  <! Sec='USAGE' Level=0 Label='zoom_factor' Line='zoom_factor'>
  <DD>Zoom factor by the display is to be expanded.  The factors are powers
  of 2; 1 = no zoom, 2 = factor of 2, 3 = factor of 4, and 4 = factor of 8.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_window">window = no</A></B></DT>
  <! Sec='USAGE' Level=0 Label='window' Line='window = no'>
  <DD>Window the enlarged image?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The display is zoomed by the specified factor.  A zoom factor of 1 is no
  magnification and higher factors correspond to factors of 2.  The zoom
  replicates pixels on the monitor and only a part of the display frame
  centered on the display cursor is visible.  The window option allows
  the user to adjust interactively with the cursor the part of the zoomed
  frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To magnify the displayed frame by a factor of 2:
  <P>
  	cl&gt; zoom 2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>