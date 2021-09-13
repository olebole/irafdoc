.. _mkcwcs:

mkcwcs — Make or update a simple celestial wcs
==============================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkcwcs -- make or update a simple celestial wcs
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkcwcs wcsname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>wcsname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsname' Line='wcsname'>
  <DD>Image to be created or modified.  If a new (non-existent) image is specified
  then a data-less image (NDIM=0) is created.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsref = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsref' Line='wcsref = ""'>
  <DD>Image whose WCS is first inherited and then updated.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>equinox = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='equinox' Line='equinox = INDEF'>
  <DD>Equinox of the coordinates specified in decimal years.  If INDEF then the
  current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B>ra = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = INDEF'>
  <DD>Right ascension in hours.  This may be typed in standard sexagesimal
  notation though it will be converted to decimal hours in EPARAM and
  to decimal degrees in the WCS as required by the standard.  If INDEF
  then the current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B>dec = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec = INDEF'>
  <DD>Declination in degrees.  This may be typed in standard sexagesimal
  notation though it will be converted to decimal degrees in EPARAM.
  If INDEF then the current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = INDEF, pa = 0., lefthanded = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = INDEF, pa = 0., lefthanded = yes'>
  <DD>Celestial pixel scale in arc seconds per pixel, the position angle in
  degrees, and the handedness of the axes.  These are all represented by
  the WCS rotation matrix.  If the scale is INDEF the current
  rotation matrix is unchanged and the position angle is ignored.  If the
  scale is not INDEF then orthogonal axes are defined with the same scale on
  both axes.  The handedness of the axes are specified by the
  <I>lefthanded</I> parameter.  The position angle is measured from north
  increasing with the image lines (up in a standard display) and rotated
  towards east.  Note that if the axes are lefthanded the angle is
  counterclockwise and if not it is clockwise.
  </DD>
  </DL>
  <DL>
  <DT><B>projection = "<TT>tan</TT>" (tan|sin|linear)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan" (tan|sin|linear)'>
  <DD>WCS projection function which may be "<TT>tan</TT>", "<TT>sin</TT>", or "<TT>linear</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>rapix = INDEF, decpix = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rapix' Line='rapix = INDEF, decpix = INDEF'>
  <DD>The reference pixel for the right ascension (first image axis) and for
  the declination (second image axes).  The reference pixel may be fractional
  and lie outside the size of the image as allowed by the standard.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKCWCS creates or modifies a celestial (RA/DEC) WCS in an image header.  If a
  new image is specified the WCS is created in a data-less image header.  A
  data-less WCS may be used in various tasks as a template.  If a reference
  WCS is specified it is copied in whole and then desired elements of the WCS
  are modified.  If a new WCS is created without a reference the initial values
  are for the pixel coordinates.
  <P>
  The elements of the WCS which may be set are the coordinate equinox,
  the right ascension and declination, the pixel scale, the axes orientation,
  and the reference pixel in the image which corresponds to the specified
  right ascension and declination.  If values are specified they WCS elements
  are left unchanged.
  <P>
  The WCS is simple and not completely general because it defines the first
  coordinate axis to be right ascension and the second to be declination and
  that the axes are orthogonal with a uniform pixel scale (apart from the
  projection function).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a data-less header by specifying a new wcs name.
  <P>
  <PRE>
      cl&gt; mkcwcs new ra=1:20:23.1 dec=-12:11:13 scale=0.25
  </PRE>
  <P>
  The reference pixel will be (0,0).  To apply it later to an actual
  image (say with WCSCOPY) would require assigning the reference pixel.
  Note the use of sexagesimal notation.
  <P>
  2. Modify the WCS of an existing image by changing the reference value
  and pixel.
  <P>
  <PRE>
      cl&gt; mkcwcs old ra=1:20:23.1 dec=-12:11:13 rapix=1234 decpix=345
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wcsedit,wcscopy,mkcwwcs
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
