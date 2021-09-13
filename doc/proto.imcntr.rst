imcntr — Locate the center of a stellar image
=============================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imcntr (Dec85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imcntr (Dec85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imcntr</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imcntr -- locate the center of a stellar image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imcntr input x_init y_init
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of images which contain the star to be centered.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x_init">x_init</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x_init' Line='x_init'>
  <DD>The approximate column coordinate as a starting point for the centering.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_y_init">y_init</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='y_init' Line='y_init'>
  <DD>The approximate line (row) coordinate as a starting point for the centering.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cboxsize">cboxsize = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cboxsize' Line='cboxsize = 5'>
  <DD>The size of the extraction box to be used during the centering process.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Given the approximate coordinates of the center of an object, (x_init, y_init),
  IMCNTR will compute a more accurate center using the algorithms described in
  the Kitt Peak publication "<TT>Stellar Magnitudes from Digital Images</TT>" under
  the Mountain Photometry Code section. Briefly, this algorithm computes
  the sum of all the rows and the sum of all the columns in the extraction
  box. These are called "<TT>marginal distributions</TT>". The center in x (column
  value) is then the center of gravity of the row marginal, and the center
  in y is the center of gravity of the column marginal.
  If the resultant x or y center value deviates from the original input
  approximate starting points by more than 1 pixel, the process is repeated
  once more around the new center. Only one iteration is attempted to
  avoid runaway if a bright star is nearby.
  <P>
  Because the centers are computed independently for x and y, the result
  may be considered inferior to a true two-dimensional centering algorithm.
  Nevertheless, in practice the results appear to be very usable.
  <P>
  The value for the box size should be an odd value. If chosen too large,
  nearby objects will affect the result. If too small, the center will be
  poorly defined.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The following example locates the center of a star near (123, 234)
  in 3 images.
  <BR>
  <PRE>
  cl&gt; imcntr m92red,m92blu,m92grn 123 234
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The routine will probably fail if the desired object is within 2 or 3 pixels
  of the image boundary.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pradprof
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>