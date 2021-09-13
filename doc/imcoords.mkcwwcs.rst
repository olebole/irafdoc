mkcwwcs — Make or update a simple celestial/wavelength 3D wcs
=============================================================

**Package: imcoords**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkcwwcs (Jun05)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imcoords</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkcwwcs (Jun05)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkcwwcs</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkcwwcs -- make or update a simple celestial/wavelength wcs
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkcwwcs wcsname
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_wcsname">wcsname</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsname' Line='wcsname'>
  <DD>Image to be created or modified.  If a new (non-existent) image is specified
  then a data-less image (NDIM=0) is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsref">wcsref = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsref' Line='wcsref = ""'>
  <DD>Image whose WCS is first inherited and then updated.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_equinox">equinox = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='equinox' Line='equinox = INDEF'>
  <DD>Equinox of the coordinates specified in decimal years.  If INDEF then the
  current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra">ra = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = INDEF'>
  <DD>Right ascension in hours.  This may be typed in standard sexagesimal
  notation though it will be converted to decimal hours in EPARAM and
  to decimal degrees in the WCS as required by the standard.  If INDEF
  then the current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec">dec = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec = INDEF'>
  <DD>Declination in degrees.  This may be typed in standard sexagesimal
  notation though it will be converted to decimal degrees in EPARAM.
  If INDEF then the current value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = INDEF, pa = 0., lefthanded = yes</A></B></DT>
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
  <DT><B><A NAME="l_projection">projection = "<TT>tan</TT>" (tan|sin|linear)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan" (tan|sin|linear)'>
  <DD>WCS projection function for the celestial axes which may be
  "<TT>tan</TT>", "<TT>sin</TT>", or "<TT>linear</TT>".
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_wave">wave = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave' Line='wave = INDEF'>
  <DD>Reference wavelength in arbitrary units.  If INDEF then the current
  value is not modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wscale">wscale = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wscale' Line='wscale = INDEF'>
  <DD>Wavelength scale in arbitrary units per pixel.  If INDEF then the current
  value is not modified.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_rapix">rapix = INDEF, decpix = INDEF, wpix = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rapix' Line='rapix = INDEF, decpix = INDEF, wpix = INDEF'>
  <DD>The reference pixel for the right ascension (first image axis), for
  the declination (second image axes), and for the wavelength
  (third axis).  The reference pixel may be fractional
  and lie outside the size of the image as allowed by the standard.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKCWWCS creates or modifies a celestial (RA/DEC) plus wavelength
  three-dimensional WCS in an image header.  If a
  new image is specified the WCS is created in a data-less image header.  A
  data-less WCS may be used in various tasks as a template.  If a reference
  WCS is specified it is copied in whole and then desired elements of the WCS
  are modified.  If a new WCS is created without a reference the initial values
  are for the pixel coordinates.
  <P>
  The elements of the WCS which may be set are the coordinate equinox,
  the right ascension and declination, the pixel scale, the axes orientation,
  the reference wavelength, the wavelength scale (i.e. dispersion),
  and the reference pixel in the image which corresponds to the specified
  right ascension and declination.  If values are specified the WCS elements
  are left unchanged.
  <P>
  The WCS is simple and not completely general because it defines the first
  coordinate axis to be right ascension, the second to be declination, and
  the third to be wavelength.  The axes are orthogonal and the celestial axes
  have a uniform pixel scale (apart from the effects of the projection
  function).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a data-less header by specifying a new wcs name.
  <P>
  <PRE>
      cl&gt; mkcwwcs new ra=1:20:23.1 dec=-12:11:13 wave=5500. \<BR>
      &gt;&gt;&gt; scale=0.25 wscale=1.23
  </PRE>
  <P>
  The reference pixel will be (0,0,0).  To apply it later to an actual
  image (say with WCSCOPY) would require assigning the reference pixel.
  Note the use of sexagesimal notation.
  <P>
  2. Modify the WCS of an existing image by changing the reference value
  and pixel.
  <P>
  <PRE>
      cl&gt; mkcwwcs old ra=1:20:23.1 dec=-12:11:13 wave=5500. \<BR>
      &gt;&gt;&gt; rapix=1234 decpix=345 wpix=1024
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wcsedit,wcscopy,mkcwcs
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>