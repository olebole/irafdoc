.. _scoords:

scoords — Set spectral coordinates as a pixel array (1D spectra only)
=====================================================================

**Package: onedspec**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  scoords -- set spectrum coordinates from a pixel array (1D only)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  scoords images coords
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of one dimensional spectrum image names.
  </DD>
  </DL>
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>List of file names containing the coordinate values.  There may be
  one file which applies to all input images or a matching list
  of one coordinate file for each input image.  The coordinate files
  are a list of coordinate values with one coordinate per line.
  The coordinates must be ordered in increasing or decreasing value.
  The number of coordinates must match the number of pixels in the image.
  </DD>
  </DL>
  <DL>
  <DT><B>label = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='label' Line='label = ""'>
  <DD>Optional coordinate axis label.  A typical value is "<TT>Wavelength</TT>"
  for wavelength coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>units = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>Optional coordinate axis units.  A typical value is "<TT>Angstroms</TT>".  In
  order to allow coordinate conversions by other IRAF spectra tasks
  the value should be specified as one of the known units
  (see units description in <B>onedspec.package</B>).
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print a line as each spectrum is processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Scoords</B> sets spectral coordinates in one dimensional spectral
  images as a list of coordinates in the image header.  The
  coordinate file(s) consists of coordinate values given one per line.
  Each coordinate value is assigned to an image pixel in the order given
  and so the number of coordinate values must match the number of pixels
  in the spectrum.  Also the coordinates must be monotonically increasing
  or decreasing.
  <P>
  When multiple spectra are to be set a matching list of coordinates can
  be specified or a single coordinate file for all images may be used.
  <P>
  The coordinate system set in the header is an example of the "<TT>multispec</TT>"
  world coordinate system.  This is understood by all the standard
  IRAF tasks.  It is described under the help topic "<TT>onedspec.specwcs</TT>".
  Once the coordinates are set one may resample the spectrum to a
  more compact linear description using the task <B>dispcor</B>.
  <P>
  Since the coordinate values are stored in the header (double
  precision numbers) the header can become quite large if the spectrum
  is long.  Be sure the environment variable "<TT>min_lenuserarea</TT>" which
  defines the maximum size of the image header in number of characters
  is large enough to hold all the coordinates.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Set the coordinates for a spectrum.
  <P>
  <PRE>
      cl&gt; type coords.dat
      4000.
      4010.123
      4020.246
      4031.7
      &lt;etc&gt;
      cl&gt; scoords spec coords.dat label=Wavelength units=Angstroms
      cl&gt; listpix spec wcs=world
      4000.  	124.
      4010.123	543
      &lt;etc&gt;
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SCOORDS V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SCOORDS' Line='SCOORDS V2.11'>
  <DD>This is a new task with this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rtextimage, dispcor, specwcs, onedspec.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
