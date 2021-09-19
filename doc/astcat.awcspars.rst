.. _awcspars:

awcspars: Default image wcs parameters
======================================

**Package: astcat**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  awcspars -- edit the default world coordinate system parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  awcspars 
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>wxref = <tt>"INDEF"</tt>, wyref = <tt>"INDEF"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wxref' Line='wxref = "INDEF", wyref = "INDEF"' -->
  <dd>The image header keyword names or the numerical values of the x and y reference
  point in pixels. If wxref = <tt>"INDEF"</tt> and wyref = <tt>"INDEF"</tt> the reference
  point defaults to the center of the image.
  </dd>
  </dl>
  <dl>
  <dt><b>wxmag = <tt>"INDEF"</tt>, wymag = <tt>"INDEF"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wxmag' Line='wxmag = "INDEF", wymag = "INDEF"' -->
  <dd>The image header keyword names or the numerical values of the x and y scale
  factors in arcseconds per pixel. If wxmag  or wymag = are undefined a new
  wcs cannot be created.
  </dd>
  </dl>
  <dl>
  <dt><b>wxrot = <tt>"180.0"</tt>, wyrot = <tt>"0.0"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wxrot' Line='wxrot = "180.0", wyrot = "0.0"' -->
  <dd>The image header keyword names or the numerical values of the x and y rotation
  angles in degrees measured counter-clockwise to the positive x and y image
  axes. The default orientation is east=left, north=up. Wxrot values of 0.0,
  90.0, 180.0, and 270.0 correspond to east=right, up, left, and down
  respectively. Wyrot values of 0.0, 90.0, 180.0, and 270.0 correspond to
  north=up, left, down, and right respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>wraref = <tt>"RA"</tt>, wdecref = <tt>"DEC"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wraref' Line='wraref = "RA", wdecref = "DEC"' -->
  <dd>The image header keyword names or the numerical values of the reference
  point in celestial coordinates. If wraref and wdecref are undefined
  a new wcs cannot be created.
  </dd>
  </dl>
  <dl>
  <dt><b>wraunits = <tt>""</tt>, wdecunits = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wraunits' Line='wraunits = "", wdecunits = ""' -->
  <dd>The units of the reference point celestial coordinates. The options are
  <tt>"hours"</tt>, <tt>"degrees"</tt>, and <tt>"radians"</tt> for the ra coordinate and <tt>"degrees"</tt>
  and <tt>"radians"</tt> for the dec coordinate. If wraunits and wdecunits are undefined
  they default to the preferred units of the reference system.
  </dd>
  </dl>
  <dl>
  <dt><b>wproj = <tt>"tan"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wproj' Line='wproj = "tan"' -->
  <dd>The sky projection geometry. The most commonly used projections are <tt>"tan"</tt>,
  <tt>"arc"</tt>, <tt>"sin"</tt>, and <tt>"lin"</tt>. Other supported projections are <tt>"ait"</tt>,<tt>"car"</tt>, <tt>"csc"</tt>,
  <tt>"gls"</tt>, <tt>"mer"</tt>, <tt>"mol"</tt>, <tt>"par"</tt>, <tt>"pco"</tt>, <tt>"qsc"</tt>, <tt>"stg"</tt>, <tt>"tsc"</tt>, and <tt>"zea"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>wsystem = <tt>"EQUINOX"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wsystem' Line='wsystem = "EQUINOX"' -->
  <dd>The image header keyword name or string defining the celestial coordinate
  system of the reference point. The most common values for wsystem are
  <tt>"2000.0"</tt>, <tt>"1950.0"</tt>, <tt>"J2000.0"</tt>, and <tt>"B1950.0"</tt>. Type <tt>"help ccssytems"</tt> to get
  a full list of options.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The default wcs parameters are used to create an approximate  FITS wcs for
  an images which do not have one. Creating an approximate header
  from the telescope pointing position and the known scale and orientation
  of the detector can make later steps like locating the catalog stars
  for computing an accurate plate solution simpler.
  </p>
  <p>
  In coordinates of the reference point in pixels and celestial coordinates
  <i>wxref</i>, <i>wyref</i>, <i>wraref</i>, <i>wdecref</i>, the scale factors
  <i>wxmag</i> and <i>wymag</i>, and the orientation <i>wxrot</i> and <i>wyrot</i>
  can be read from the image header or set by value. The coordinate system
  and units of the celestial coordinates of the reference point <i>wsystem</i>
  and <i>wraunits</i> and <i>wdecunits</i> must be set explicitly. The image
  projection function <i>wproj</i> must also be set separately.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the default wcs parameters.
  </p>
  <pre>
  cl&gt; lpar awcspars
  </pre>
  <p>
  2. Edit the default wcs parameters.
  </p>
  <pre>
  cl&gt; awcspars
  </pre>
  <p>
  3. Edit the default wcs parameters from the agetim task.
  </p>
  <pre>
  cl&gt; epar agetim
  </pre>
  <p>
  4. Save the current awcspars parameter values in a text file called
  awcs1.par.  Use the saved parameter set in the next call to the agetim
  task.
  </p>
  <pre>
  cl&gt; epar awcspars
  cl&gt; agetim ... awcspars=awcs1.par ...
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  agetim, ahedit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
