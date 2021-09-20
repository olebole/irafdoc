.. _aregpars:

aregpars: Default region parameter set
======================================

**Package: astcat**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  aregpars
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>rcra = <span style="font-family: monospace;">"00:00:00.0"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcra' Line='rcra = "00:00:00.0"' -->
  <dd>The right ascension / longitude of the center of the region to be extracted.
  </dd>
  </dl>
  <dl>
  <dt><b>rcdec = <span style="font-family: monospace;">"+00:00.00"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcdec' Line='rcdec = "+00:00.00"' -->
  <dd>The declination / latitude of the center of the region to be extracted.
  </dd>
  </dl>
  <dl>
  <dt><b>rrawidth = 10.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rrawidth' Line='rrawidth = 10.0' -->
  <dd>The right ascension / longitude width in minutes of arc of the region to
  be extracted.
  </dd>
  </dl>
  <dl>
  <dt><b>rdecwidth = 10.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rdecwidth' Line='rdecwidth = 10.0' -->
  <dd>The declination / latitude width in minutes of arc of the region to
  be extracted.
  </dd>
  </dl>
  <dl>
  <dt><b>rcsystem = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcsystem' Line='rcsystem = ""' -->
  <dd>The input celestial coordinate system. This is the celestial coordinate system
  of the region center. If the input celestial coordinate system is undefined it
  defaults to the query celestial coordinate system. Popular options are
  <span style="font-family: monospace;">"icrs"</span>, <span style="font-family: monospace;">"j2000.0"</span>, and <span style="font-family: monospace;">"b1950.0"</span>. The full set of options can be examined
  by typing <span style="font-family: monospace;">"help ccsystems"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>rcraunits = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcraunits' Line='rcraunits = ""' -->
  <dd>The units of rcra. Permitted values are <span style="font-family: monospace;">"hours"</span>, <span style="font-family: monospace;">"degrees"</span>, and radians. If
  rcraunits is undefined it defaults to the preferred units of the
  input celestial coordinate system, e.g. hours for equatorial coordinate
  system, degrees for ecliptic, galactic, and super-galactic coordinate
  systems.
  </dd>
  </dl>
  <dl>
  <dt><b>rcdecunits = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcdecunits' Line='rcdecunits = ""' -->
  <dd>The units of rcdec. Permitted values are <span style="font-family: monospace;">"degrees"</span> and <span style="font-family: monospace;">"radians"</span>. If rcdecunits
  is undefined it defaults to the preferred units of the input celestial
  coordinate system, e.g. degrees for all systems.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The region to extracted from the selected astrometric catalog or image survey
  is defined by the aregpars parameters <i>rcra</i>, <i>rcdec</i>, <i>rcrawidth</i>,
  and <i>rcdecwidth</i>.
  </p>
  <p>
  <i>rcra</i> and <i>rcdec</i> are defined in the input celestial coordinate system
  specified by <i>rcsystem</i>.  If <i>rcsystem</i> is undefined it defaults to the
  query celestial coordinate system defined by the qsystem query parameter in
  the catalog configuration file.
  </p>
  <p>
  <i>rcra</i> and <i>rcdec</i> are expressed in the units specified by 
  <i>rcraunits</i>, and <i>rcdecunits</i>.  If undefined <i>rcraunits</i> and
  <i>rcdecunits</i> are expressed in the preferred units of the input
  celestial coordinate system, e.g. hours and degrees for equatorial coordinate
  systems, and degrees and degrees for ecliptic, galactic,
  and super-galactic coordinate systems.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the region extraction parameters.
  </p>
  <pre>
  cl&gt; lpar aregpars
  </pre>
  <p>
  2. Edit the region extraction parameters.
  </p>
  <pre>
  cl&gt; aregpars
  </pre>
  <p>
  3. Edit the region extraction parameters from the agetcat task.
  </p>
  <pre>
  cl&gt; epar agetcat
  </pre>
  <p>
  4. Save the current aregpars parameter values in a text file called
  areg1.par.  Use the saved parameter set in the next call to the agetcat 
  task.
  </p>
  <pre>
  cl&gt; epar aregpars
  cl&gt; agetcat ... aregpars=areg1.par ...
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
  agetcat, agetim, help ccsystems
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
