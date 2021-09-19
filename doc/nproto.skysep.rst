.. _skysep:

skysep: Compute arc separation of two RA/Dec values
===================================================

**Package: nproto**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  skysep -- Compute arc separation of two RA/Dec values
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Synopsis</h3>
  <!-- BeginSection: 'SYNOPSIS' -->
  <p>
  Given two RA/Dec value pairs the spherical separation is computed.  This
  task can be used in scripts and has both text and parameter output.
  </p>
  <!-- EndSection:   'SYNOPSIS' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  skysep ra1 dec1 ra2 dec2
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>ra1, dec1, ra2, dec2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ra1' Line='ra1, dec1, ra2, dec2' -->
  <dd>The RA and Dec of two points on the sky for which a separation is to be
  computed.  The RA may be in hours or degrees and the Dec is in degrees.
  The values may be in decimal or sexagesimal format.
  </dd>
  </dl>
  <dl>
  <dt><b>raunit = <tt>"hr"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='raunit' Line='raunit = "hr"' -->
  <dd>Units for right ascension.  The value <tt>"hr"</tt> selects hours and <tt>"deg"</tt>
  selects degrees.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print a verbose output to the standard output?
  </dd>
  </dl>
  <dl>
  <dt><b>sep</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sep' Line='sep' -->
  <dd>This output parameter will contain the separation in arc seconds after
  the task is run.  It may then be referenced as the variable skysep.sep.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This simple script task computes the separation between two celestial
  coordinates given as RA and Dec.  The RA units may be hours or degrees,
  as selected by a parameter, and the Dec units must be degrees.  The result
  may be printed to the standard output (in restricted precision) and is
  also record in a task parameter for later use.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The verbose output appears as follows:
  </p>
  <pre>
      cl&gt; skysep 12:12:12 32:32:32 12:12:24 32:32:52 verb+
      153.05 arcsec = (12:12:12.00, 32:32:32.0) - (12:12:24.00, 32:32:52.0)
      cl&gt; = skysep.sep
      153.04686934468
  </pre>
  <p>
  2. To use in a script:
  </p>
  <pre>
      cache skysep   # Cache to avoid problems with updating par files
      
      # To use scan to get the value.
      skysep (r1, d1, r2, d2, raunit="deg", verbose+) | scan (sep)
      printf ("The separation is %f\n", sep)
  
      # To use the saved value.
      skysep (r1, d1, r2, d2, raunit="deg", verbose-)
      printf ("The separation is %.5f\n", skysep.sep)
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  astcalc, asthedit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'SYNOPSIS' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
