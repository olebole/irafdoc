.. _dematch:

dematch: Match a list of density values to exposure values
==========================================================

**Package: dtoi**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  dematch -- match density to log exposure values
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  dematch database 
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>database</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='database' Line='database' -->
  <dd>Database containing density list, probably from <i>spotlist</i>.
  </dd>
  </dl>
  <dl>
  <dt><b>wedge = <span style="font-family: monospace;">""</span>, filter = <span style="font-family: monospace;">""</span>, emulsion = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wedge' Line='wedge = "", filter = "", emulsion = ""' -->
  <dd>Information used to retrieve log exposure values from <b>wedgefile</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>wedgefile = <span style="font-family: monospace;">"noao$lib/hdwedge.dat"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wedgefile' Line='wedgefile = "noao$lib/hdwedge.dat"' -->
  <dd>Name of file containing wedge intensity information.
  </dd>
  </dl>
  <dl>
  <dt><b>nskip = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nskip' Line='nskip = 0' -->
  <dd>Number of faint spots skipped, used as an offset into the list of
  log exposure values.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print the log exposure information to STDOUT as well as to <b>database</b>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>dematch</i> matches density values to log exposure values.  A database
  of density values is input, as well as information needed to 
  retrieve log exposure values from a reference file.  The two sources of 
  information are matched, and the matching log exposure values are added 
  as a record in the database.
  </p>
  <p>
  Parameter <b>nskip</b> tells how many faint spots were not
  included in the density <b>database</b>.  This information is
  used to align the density, exposure values.  It doesn't matter if the 
  densities are listed in a monotonically increasing or decreasing
  order, as long as no spots were omitted between the first and last
  measured.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Match densities in db1 to log exposure values for wedge#117
  with a IIIAJ emulsion and a GG385 filter.
  </p>
  <pre>
  
  	cl&gt; dematch db1 wedge=117 filt=gg385 emulsion=IIIAJ
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  spotlist, hdfit, hdtoi
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
