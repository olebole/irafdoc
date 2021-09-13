.. _skysep:

skysep — Compute arc separation of two RA/Dec values
====================================================

**Package: nproto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  skysep -- Compute arc separation of two RA/Dec values
  </UL>
  <! EndSection:   'NAME'>
  <H3>Synopsis</H3>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  Given two RA/Dec value pairs the spherical separation is computed.  This
  task can be used in scripts and has both text and parameter output.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  skysep ra1 dec1 ra2 dec2
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>ra1, dec1, ra2, dec2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra1' Line='ra1, dec1, ra2, dec2'>
  <DD>The RA and Dec of two points on the sky for which a separation is to be
  computed.  The RA may be in hours or degrees and the Dec is in degrees.
  The values may be in decimal or sexagesimal format.
  </DD>
  </DL>
  <DL>
  <DT><B>raunit = "<TT>hr</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raunit' Line='raunit = "hr"'>
  <DD>Units for right ascension.  The value "<TT>hr</TT>" selects hours and "<TT>deg</TT>"
  selects degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a verbose output to the standard output?
  </DD>
  </DL>
  <DL>
  <DT><B>sep</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sep' Line='sep'>
  <DD>This output parameter will contain the separation in arc seconds after
  the task is run.  It may then be referenced as the variable skysep.sep.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This simple script task computes the separation between two celestial
  coordinates given as RA and Dec.  The RA units may be hours or degrees,
  as selected by a parameter, and the Dec units must be degrees.  The result
  may be printed to the standard output (in restricted precision) and is
  also record in a task parameter for later use.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  astcalc, asthedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
