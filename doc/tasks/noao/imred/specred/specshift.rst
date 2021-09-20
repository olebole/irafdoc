.. _specshift:

specshift: Shift spectral dispersion coordinate systems
=======================================================

**Package: specred**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  specshift spectra shift
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>spectra</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra' -->
  <dd>List of spectra to be modified.
  </dd>
  </dl>
  <dl>
  <dt><b>shift</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='shift' Line='shift' -->
  <dd>Dispersion coordinate shift to be added to the current dispersion coordinate
  system.
  </dd>
  </dl>
  <dl>
  <dt><b>apertures = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""' -->
  <dd>List of apertures to be modified.  The null list
  selects all apertures.  A list consists of comma separated
  numbers and ranges of numbers.  A range is specified by a hyphen.  An
  optional step size may be given by using the <span style="font-family: monospace;">'x'</span> followed by a number.
  See <b>xtools.ranges</b> for more information.  This parameter is ignored
  for N-dimensional spatial spectra such as long slit and Fabry-Perot.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print a record of each aperture modified?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task applies a shift to the dispersion coordinate system of selected
  spectra.  The image data is not modified as with <b>imshift</b> but rather
  the coordinate system is shifted relative to the data.  The spectra to be
  modified are selected by specifying a list of images and apertures.  If no
  aperture list is specified then all apertures in the images are modified.
  For N-dimensional spatial spectra such as long slit and Fabry-Perot the
  aperture list is ignored.
  </p>
  <p>
  The specified shift is added to the existing world coordinates.  For linear
  coordinate systems this has the effect of modifying CRVAL1, for linear
  <span style="font-family: monospace;">"multispec"</span> coordinate systems this modifies the dispersion coordinate of
  the first physical pixel, and for nonlinear <span style="font-family: monospace;">"multispec"</span> coordinate systems
  this modifies the shift coefficient(s).
  </p>
  <p>
  It is also possible to shift the linearized coordinate systems (but not the
  nonlinear coordinate systems) with <b>sapertures</b> or possibly with
  <b>wcsedit</b> or <b>hedit</b> if the coordinate system is stored with a
  global linear system.
  </p>
  <p>
  The <i>verbose</i> parameter lists the images, the apertures, the shift, and
  the old and new values for the first physical pixel are printed.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  To add 1.23 Angstroms to the coordinates of all apertures in the
  image <span style="font-family: monospace;">"ngc456.ms"</span>:
  </p>
  <pre>
  	cl&gt; specshift ngc456.ms 1.23
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>SPECSHIFT V2.10.3</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='SPECSHIFT' Line='SPECSHIFT V2.10.3' -->
  <dd>First version.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  sapertures, dopcor, imcoords.wcsreset, hedit, ranges, onedspec.package
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
