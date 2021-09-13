.. _sapertures:

sapertures — Set or change aperture header information
======================================================

**Package: argus**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sapertures -- Set or change aperture header information
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sapertures input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of spectral images to be modified.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be modified.  The null list
  selects all apertures.  A list consists of comma separated
  numbers and ranges of numbers.  A range is specified by a hyphen.  An
  optional step size may be given by using the <TT>'x'</TT> followed by a number.
  See <B>xtools.ranges</B> for more information.
  </DD>
  </DL>
  <DL>
  <DT><B>apidtable = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apidtable' Line='apidtable = ""'>
  <DD>Aperture table.  This may be either a text file or an image.
  A text file consisting of lines with an aperture number,
  beam number, dispersion type code, coordinate of the first physical
  pixel, coordinate interval per physical pixel, redshift factor,
  lower extraction aperture position, upper extraction aperture position,
  and aperture title or identification.  An image will contain the
  keywords SLFIBnnn with string value consisting of aperture number,
  beam number, optional right ascension and declination, and aperture title.
  Any field except the aperture number may be given the value INDEF to
  indicate that the value is not to be changed from the current value.  Any
  apertures not in this table are assigned the values given by the task
  parameters described below.
  <P>
  As a special case a file having just the aperture number, beam number, and
  spectrum aperture identification may be used.  This file format as well as
  use of an image header is the same as that in the <B>apextract</B> package.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsreset = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsreset' Line='wcsreset = no'>
  <DD>Reset the world coordinate system (WCS) of the selected apertures to
  uncorrected pixels.  If this parameter is set the <I>apidtable</I> and task
  aperture parameters are ignored.  This option sets the dispersion type flag
  to -1, the starting coordinate value to 1, the interval per pixel to 1, and
  no redshift factor and leaves the other parameters unchanged.  The option
  is useful when it is desired to apply a second dispersion correction using
  <B>identify</B> and <B>dispcor</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a record of each aperture modified?  Only those apertures 
  in which the beam number or label are changed are printed.
  </DD>
  </DL>
  <P>
  If no aperture table is specified or if there is not an aperture
  entry in the table for a selected aperture the following parameter
  values are used.  A value of INDEF will leave the corresponding
  parameter unchanged.
  <DL>
  <DT><B>beam = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='beam' Line='beam = INDEF'>
  <DD>Beam number.
  </DD>
  </DL>
  <DL>
  <DT><B>dtype = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dtype' Line='dtype = INDEF'>
  <DD>Dispersion type.  The dispersion types are:
  <P>
  <PRE>
  	-1  Linear with dispersion correction flag off
  	 0  Linear with dispersion correction flag on
  	 1  Log-linear with dispersion correction flag on
  </PRE>
  <P>
  </DD>
  </DL>
  <DL>
  <DT><B>w1 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='w1' Line='w1 = INDEF'>
  <DD>Coordinate of the first physical pixel.  Note that it is possible
  that the physical pixels are not the same as the logical pixels if
  an image section has been extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>dw = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dw' Line='dw = INDEF'>
  <DD>Coordinate interval per physical pixel.  Note that it is possible
  that the physical pixels intervals are not the same as the logical pixels
  intervals if an image section has been extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>z = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z' Line='z = INDEF'>
  <DD>Redshift factor.  This is usually set with the task <B>dopcor</B>.
  Coordinates are divided by one plus the redshift factor (1+z).
  </DD>
  </DL>
  <DL>
  <DT><B>aplow = INDEF, aphigh = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aplow' Line='aplow = INDEF, aphigh = INDEF'>
  <DD>The aperture extraction limits.  These are set when the <B>apextract</B>
  package is used and it is unlikely that one would use this task to
  change them.
  </DD>
  </DL>
  <DL>
  <DT><B>title = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = INDEF'>
  <DD>Aperture title or identification string.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task sets or changes any of the aperture specific parameters except
  the aperture number and the number of  valid pixels.  It is particularly
  useful for images which use the "<TT>multispec</TT>" world coordinate system
  attribute strings which are not readily accessible with other header
  editors.  A list of images and a list of apertures is used to select which
  spectra are to be modified.  The default empty string for the apertures
  selects all apertures.  The new values are specified either in an aperture
  table file or with task parameters.  The aperture table is used to give
  different values to specific apertures.  If all apertures are to have the
  same values this file need not be used.
  <P>
  The aperture parameters which may be modified are the beam number, the
  dispersion type, the coordinate of the first physical pixel, the coordinate
  interval per physical pixel, the redshift factor, the aperture extraction
  limits, and the title.  The task has parameters for each of these and the
  aperture table consists of lines starting with an aperture number followed
  by the above parameters in the list order and separated by whitespace.  As
  a special case the aperture table may be a file abbreviated to aperture
  number, beam number, and title or an image with keywords SLFIBnnn
  containing the aperture number, beam number, optional right ascension and
  declination, and title.  These special cases allow use of the same file
  orimage used in the <B>apextract</B> package.  If any of the parameters are
  specified as INDEF then the value will be unchanged.
  <P>
  If the <I>wcsreset</I> parameter is set then the aperture table and
  task aperture parameters are ignored and the selected apertures are
  reset to have a dispersion type of -1, a starting coordinate of 1,
  a coordinate interval of 1, and a redshift factor of 0.  This other
  parameters are not changed.  These choice of parameters has the effect
  of resetting the spectrum to physical pixel coordinates and flagging
  the spectra as not being dispersion calibrated.  One use of this option
  is to allow the <B>dispcor</B> task to be reapplied to previously
  dispersion calibrated spectra.
  <P>
  The <I>verbose</I> parameter lists the old and new values when there is
  a change.  If there are no changes there will be no output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To add titles to a multifiber extraction and change one of the
  beam numbers:
  <P>
  <PRE>
  	cl&gt; type m33aps
  	36 2 Henear
  	37 0 Sky
  	38 1 New title
  	39 1 Another title
  	41 0 Sky
  	42 1 Yet another title
  	43 1 YAT
  	44 1 Was a sky but actually has an object
  	45 1 Wow
  	46 1 Important new discovery
  	47 0 Sky
  	48 2 Henear
  	cl&gt; saper m33.ms apid=m33aps v+
  	demoobj1.ms:
  	  Aperture 37:  --&gt; Sky
  	  Aperture 38:  --&gt; New title
  	  Aperture 39:  --&gt; Another title
  	  Aperture 41:  --&gt; Sky
  	  Aperture 42:  --&gt; Yet another title
  	  Aperture 43:  --&gt; YAT
  	  Aperture 44: beam 0 --&gt; beam 1
  	  Aperture 44:  --&gt; Was a sky but actually has an object
  	  Aperture 45:  --&gt; Wow
  	  Aperture 46:  --&gt; Important new discovery
  	  Aperture 47:  --&gt; Sky
  </PRE>
  <P>
  2.  To reset a dispersion calibrated multifiber spectrum:
  <P>
  <PRE>
  	cl&gt; saper test.ms wcsreset+ verbose+
  	test.ms:
  	  Aperture 1:
  	    w1 4321. --&gt; 1.
  	    dw 1.23 --&gt; 1.
  	  Aperture 2:
  	    w1 4321. --&gt; 1.
  	    dw 1.23 --&gt; 1.
  	  &lt;etc.&gt;
  </PRE>
  <P>
  3.  To set a constant wavelength length scale (with the default parameters):
  <P>
  <PRE>
  	cl&gt; saper test.ms dtype=0 w1=4321 dw=1.23 v+
  	test.ms:
  	  Aperture 1:
  	    w1 1. --&gt; 4321.
  	    dw 1. --&gt; 1.23
  	  Aperture 2:
  	    w1 1. --&gt; 4321.
  	    dw 1. --&gt; 1.23
  	  &lt;etc.&gt;
  </PRE>
  <P>
  4. To reset the wavelengths and title of only aperture 3:
  <P>
  <PRE>
  	cl&gt; saper test.ms aper=3 w1=4325 dw=1.22 title=HD12345 v+
  	test.ms:
  	  Aperture 3:
  	    w1 4321. --&gt; 4325.
  	    dw 1.23 --&gt; 1.22
  	    apid  --&gt; HD12345
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SAPERTURES V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SAPERTURES' Line='SAPERTURES V2.11'>
  <DD>This task has been modified to allow use of image header keywords
  as done in the APEXTRACT package.
  </DD>
  </DL>
  <DL>
  <DT><B>SAPERTURES V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SAPERTURES' Line='SAPERTURES V2.10.3'>
  <DD>This task has been greatly expanded to allow changing any of the WCS
  parameters as well as the beam number and aperture title.
  </DD>
  </DL>
  <DL>
  <DT><B>SAPERTURES V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SAPERTURES' Line='SAPERTURES V2.10'>
  <DD>This task is new.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  specshift, imcoords.wcsreset, hedit, ranges, onedspec.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
