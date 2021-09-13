skysep — Compute arc separation of two RA/Dec values
====================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>skysep (Feb06)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>skysep (Feb06)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>skysep</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  skysep -- Compute arc separation of two RA/Dec values
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_synopsis">SYNOPSIS</A></H2>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  Given two RA/Dec value pairs the spherical separation is computed.  This
  task can be used in scripts and has both text and parameter output.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  skysep ra1 dec1 ra2 dec2
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ra1">ra1, dec1, ra2, dec2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra1' Line='ra1, dec1, ra2, dec2'>
  <DD>The RA and Dec of two points on the sky for which a separation is to be
  computed.  The RA may be in hours or degrees and the Dec is in degrees.
  The values may be in decimal or sexagesimal format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_raunit">raunit = "<TT>hr</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raunit' Line='raunit = "hr"'>
  <DD>Units for right ascension.  The value "<TT>hr</TT>" selects hours and "<TT>deg</TT>"
  selects degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a verbose output to the standard output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sep">sep</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sep' Line='sep'>
  <DD>This output parameter will contain the separation in arc seconds after
  the task is run.  It may then be referenced as the variable skysep.sep.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This simple script task computes the separation between two celestial
  coordinates given as RA and Dec.  The RA units may be hours or degrees,
  as selected by a parameter, and the Dec units must be degrees.  The result
  may be printed to the standard output (in restricted precision) and is
  also record in a task parameter for later use.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The verbose output appears as follows:
  <P>
  <PRE>
      cl&gt; skysep 12:12:12 32:32:32 12:12:24 32:32:52 verb+
      153.05 arcsec = (12:12:12.00, 32:32:32.0) - (12:12:24.00, 32:32:52.0)
      cl&gt; = skysep.sep
      153.04686934468
  </PRE>
  <P>
  2. To use in a script:
  <P>
  <PRE>
      cache skysep   # Cache to avoid problems with updating par files
      
      # To use scan to get the value.
      skysep (r1, d1, r2, d2, raunit="deg", verbose+) | scan (sep)
      printf ("The separation is %f\n", sep)
  <P>
      # To use the saved value.
      skysep (r1, d1, r2, d2, raunit="deg", verbose-)
      printf ("The separation is %.5f\n", skysep.sep)
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  astcalc, asthedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>