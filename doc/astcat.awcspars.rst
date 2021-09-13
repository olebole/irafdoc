.. _awcspars:

awcspars — Default image wcs parameters
=======================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  awcspars -- edit the default world coordinate system parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  awcspars 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>wxref = "<TT>INDEF</TT>", wyref = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxref' Line='wxref = "INDEF", wyref = "INDEF"'>
  <DD>The image header keyword names or the numerical values of the x and y reference
  point in pixels. If wxref = "<TT>INDEF</TT>" and wyref = "<TT>INDEF</TT>" the reference
  point defaults to the center of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>wxmag = "<TT>INDEF</TT>", wymag = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxmag' Line='wxmag = "INDEF", wymag = "INDEF"'>
  <DD>The image header keyword names or the numerical values of the x and y scale
  factors in arcseconds per pixel. If wxmag  or wymag = are undefined a new
  wcs cannot be created.
  </DD>
  </DL>
  <DL>
  <DT><B>wxrot = "<TT>180.0</TT>", wyrot = "<TT>0.0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxrot' Line='wxrot = "180.0", wyrot = "0.0"'>
  <DD>The image header keyword names or the numerical values of the x and y rotation
  angles in degrees measured counter-clockwise to the positive x and y image
  axes. The default orientation is east=left, north=up. Wxrot values of 0.0,
  90.0, 180.0, and 270.0 correspond to east=right, up, left, and down
  respectively. Wyrot values of 0.0, 90.0, 180.0, and 270.0 correspond to
  north=up, left, down, and right respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>wraref = "<TT>RA</TT>", wdecref = "<TT>DEC</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wraref' Line='wraref = "RA", wdecref = "DEC"'>
  <DD>The image header keyword names or the numerical values of the reference
  point in celestial coordinates. If wraref and wdecref are undefined
  a new wcs cannot be created.
  </DD>
  </DL>
  <DL>
  <DT><B>wraunits = "<TT></TT>", wdecunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wraunits' Line='wraunits = "", wdecunits = ""'>
  <DD>The units of the reference point celestial coordinates. The options are
  "<TT>hours</TT>", "<TT>degrees</TT>", and "<TT>radians</TT>" for the ra coordinate and "<TT>degrees</TT>"
  and "<TT>radians</TT>" for the dec coordinate. If wraunits and wdecunits are undefined
  they default to the preferred units of the reference system.
  </DD>
  </DL>
  <DL>
  <DT><B>wproj = "<TT>tan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wproj' Line='wproj = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections are "<TT>tan</TT>",
  "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported projections are "<TT>ait</TT>","<TT>car</TT>", "<TT>csc</TT>",
  "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>", "<TT>tsc</TT>", and "<TT>zea</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>wsystem = "<TT>EQUINOX</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wsystem' Line='wsystem = "EQUINOX"'>
  <DD>The image header keyword name or string defining the celestial coordinate
  system of the reference point. The most common values for wsystem are
  "<TT>2000.0</TT>", "<TT>1950.0</TT>", "<TT>J2000.0</TT>", and "<TT>B1950.0</TT>". Type "<TT>help ccssytems</TT>" to get
  a full list of options.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The default wcs parameters are used to create an approximate  FITS wcs for
  an images which do not have one. Creating an approximate header
  from the telescope pointing position and the known scale and orientation
  of the detector can make later steps like locating the catalog stars
  for computing an accurate plate solution simpler.
  <P>
  In coordinates of the reference point in pixels and celestial coordinates
  <I>wxref</I>, <I>wyref</I>, <I>wraref</I>, <I>wdecref</I>, the scale factors
  <I>wxmag</I> and <I>wymag</I>, and the orientation <I>wxrot</I> and <I>wyrot</I>
  can be read from the image header or set by value. The coordinate system
  and units of the celestial coordinates of the reference point <I>wsystem</I>
  and <I>wraunits</I> and <I>wdecunits</I> must be set explicitly. The image
  projection function <I>wproj</I> must also be set separately.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the default wcs parameters.
  <P>
  <PRE>
  cl&gt; lpar awcspars
  </PRE>
  <P>
  2. Edit the default wcs parameters.
  <P>
  <PRE>
  cl&gt; awcspars
  </PRE>
  <P>
  3. Edit the default wcs parameters from the agetim task.
  <P>
  <PRE>
  cl&gt; epar agetim
  </PRE>
  <P>
  4. Save the current awcspars parameter values in a text file called
  awcs1.par.  Use the saved parameter set in the next call to the agetim
  task.
  <P>
  <PRE>
  cl&gt; epar awcspars
  cl&gt; agetim ... awcspars=awcs1.par ...
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  agetim, ahedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
