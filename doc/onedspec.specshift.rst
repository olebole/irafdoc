.. _specshift:

specshift — Shift spectral dispersion coordinate systems
========================================================

**Package: onedspec**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  specshift -- Shift dispersion coordinate systems
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  specshift spectra shift
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>spectra</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra'>
  <DD>List of spectra to be modified.
  </DD>
  </DL>
  <DL>
  <DT><B>shift</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift'>
  <DD>Dispersion coordinate shift to be added to the current dispersion coordinate
  system.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be modified.  The null list
  selects all apertures.  A list consists of comma separated
  numbers and ranges of numbers.  A range is specified by a hyphen.  An
  optional step size may be given by using the <TT>'x'</TT> followed by a number.
  See <B>xtools.ranges</B> for more information.  This parameter is ignored
  for N-dimensional spatial spectra such as long slit and Fabry-Perot.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a record of each aperture modified?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task applies a shift to the dispersion coordinate system of selected
  spectra.  The image data is not modified as with <B>imshift</B> but rather
  the coordinate system is shifted relative to the data.  The spectra to be
  modified are selected by specifying a list of images and apertures.  If no
  aperture list is specified then all apertures in the images are modified.
  For N-dimensional spatial spectra such as long slit and Fabry-Perot the
  aperture list is ignored.
  <P>
  The specified shift is added to the existing world coordinates.  For linear
  coordinate systems this has the effect of modifying CRVAL1, for linear
  "<TT>multispec</TT>" coordinate systems this modifies the dispersion coordinate of
  the first physical pixel, and for nonlinear "<TT>multispec</TT>" coordinate systems
  this modifies the shift coefficient(s).
  <P>
  It is also possible to shift the linearized coordinate systems (but not the
  nonlinear coordinate systems) with <B>sapertures</B> or possibly with
  <B>wcsedit</B> or <B>hedit</B> if the coordinate system is stored with a
  global linear system.
  <P>
  The <I>verbose</I> parameter lists the images, the apertures, the shift, and
  the old and new values for the first physical pixel are printed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To add 1.23 Angstroms to the coordinates of all apertures in the
  image "<TT>ngc456.ms</TT>":
  <P>
  <PRE>
  	cl&gt; specshift ngc456.ms 1.23
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SPECSHIFT V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SPECSHIFT' Line='SPECSHIFT V2.10.3'>
  <DD>First version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  sapertures, dopcor, imcoords.wcsreset, hedit, ranges, onedspec.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
