.. _hpctran:

hpctran — Convert between HEALPix row and spherical coordinate
==============================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hpctran -- Convert between HEALPix row and spherical coordinate
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hpctran lng=xxx lat=xxx
  <BR>
  hpctran row=xxx
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>row     </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row     '>
  <DD>HEALPix table row (1 indexed).
  This is used as input if the direction
  is "<TT>row2ang</TT>" or is used to store the value if the direction is
  "<TT>ang2row</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>lng, lat</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lng' Line='lng, lat'>
  <DD>Spherical coordinate consisting of a longitude and latitude.
  These are used as input if the direction
  is "<TT>ang2row</TT>" or is used to store the value if the direction is
  "<TT>row2ang</TT>".  The units are interpreted as selected by the <I>cunits</I>
  parameter.  The type of coordinates appropriate for a particular map
  is defined by the map provider.
  </DD>
  </DL>
  <DL>
  <DT><B>nside = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nside' Line='nside = 512'>
  <DD>The number of pixels per face side.
  </DD>
  </DL>
  <DL>
  <DT><B>cunits = "<TT>degrees</TT>" (degrees|hourdegree|radians)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cunits' Line='cunits = "degrees" (degrees|hourdegree|radians)'>
  <DD>The units of the longitude and latitude.  The "<TT>hourdegree</TT>" is for
  longitude in hours and latitude in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>maptype = "<TT>nest</TT>" (nest|ring)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maptype' Line='maptype = "nest" (nest|ring)'>
  <DD>The map pixelization type which may be "<TT>nest</TT>" or "<TT>ring</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>direction = "<TT>ang2row</TT>" (ang2row|row2ang)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='direction' Line='direction = "ang2row" (ang2row|row2ang)'>
  <DD>The conversion direction.  "<TT>ang2row</TT>" converts a spherical coordinate
  to a map row or pixel number.  "<TT>row2ang</TT>" converts a map row or pixel
  number to a spherical coordinate.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  HEALPix is an acronym for Hierarchical Equal Area isoLatitude Pixelization
  of a sphere.  See the reference section for a technical description of the
  pixelization and mathematics.  As suggested in the name, this pixelization,
  or tiling, produces a subdivision of a spherical surface in which each
  "<TT>pixel</TT>" covers the same surface area as every other pixel.  A HEALPix FITS
  "<TT>map</TT>" is a table where each row contains "<TT>pixel</TT>" data for a region on the
  sphere.  It is a table because the pixels don't form a raster as in an
  image.
  <P>
  The pixelization is defined by a resolution parameter which may be expressed
  in various ways.  This task uses the number of pixels along a side of one of
  the 12 basic faces.  The number of pixels/rows is 12 * nside * nside.  The
  pixelization has two forms supported by this task.  These are called
  "<TT>nested</TT>" and "<TT>ring</TT>".
  <P>
  The HEALPix WCS task, <B>hpctran</B>, provides a translation between
  the table row number and a spherical coordinate.  It is up to the
  creator of the table to choose the spherical coordinate system.  This
  might be an equatorial, galactic, or super-galactic system.  There may
  be a keyword specifying the system.  This is the case with WMAP data.
  <P>
  This task only provides the conversion.  Access to the "<TT>pixel</TT>" data
  requires other tools.  For binary tables the <B>tables</B> may be used.
  <P>
  This task allows the spherical coordinates to be input and output in three
  forms, as hours and degrees (e.g. RA/DEC), as degrees (e.g.  l/b), and as
  radians.  On input one may use sexagesimal since IRAF automatically converts
  this to decimal.  On output the values are produced in decimal form.
  <P>
  The output is provide in two ways to provide flexibility in scripting.  One
  is writing the results to the task parameters.  Note that it is recommended
  that tasks which write to there parameter be "<TT>cached</TT>" with the <B>cache</B>
  command to avoid problems with background submission or multiple scripts
  running in parallel.  The other output is printed to the standard output.
  Regardless of the direction of conversion the printed output is in the same
  order of row number, longitude, and latitude.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  A CMB WMAP file is obtained and one wants the temperature at a particular
  point on the sky.  Note that the WMAP format is "<TT>nested</TT>" and
  coordinate system is galactic.
  <P>
  <PRE>
  cl&gt; hpctran lng=50.12 lat=-33.45
  2298092 50.12 -33.45000000000001
  cl&gt; = hpctran.row
  2298092
  cl&gt; tdump wmap_iqusmap_r9_5yr_K1_v3.fits col=TEMPERATURE row=2298092
  cl&gt; tdump ("wmap_iqusmap_r9_5yr_K1_v3.fits", col="TEMPERATURE",
  &gt;&gt;&gt; row=hpctran.row)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Reference</H3>
  <! BeginSection: 'REFERENCE'>
  <UL>
  <I>HEALPIX - a Framework for High Resolution Discretization, and Fast
  Analysis of Data Distributed on the Sphere</I>,
  by K.M. Gorski, Eric Hivon, A.J. Banday, B.D. Wandelt, F.K. Hansen, M.
  Reinecke, M. Bartelmann, 2005, ApJ 622, 759.
  </UL>
  <! EndSection:   'REFERENCE'>
  <H3>Credit</H3>
  <! BeginSection: 'CREDIT'>
  <UL>
  Some code from the HEALPix distribution at http://healpix.jpl.nasa.gov
  was translated to SPP for use in this routine.
  </UL>
  <! EndSection:   'CREDIT'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ttools
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REFERENCE' 'CREDIT' 'SEE ALSO'  >
  
