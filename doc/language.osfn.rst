.. _osfn:

osfn: Return the host system equivalent of an IRAF filename
===========================================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  osfn -- convert an IRAF filename to a host system filename
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  string = osfn (vfn)
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>vfn  </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vfn' Line='vfn  ' -->
  <dd>The IRAF virtual filename to be translated into a host filename.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Osfn</i> is a string valued intrinsic function which takes an IRAF virtual
  filename as input and returns the equivalent host system filename as output.
  <i>Osfn</i> can only be called as a function.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the host equivalent of the vfn <tt>"hlib$login.cl"</tt>.
  </p>
  <p>
  	cl&gt; = osfn (<tt>"hlib$login.cl"</tt>)
  </p>
  <p>
  2. Compute a host filename for use as an argument to a foreign task
  (see help <i>task</i> for more information on foreign tasks).
  </p>
  <pre>
  	cl&gt; task $vdir = "$directory"	# VMS directory lister
  	cl&gt; vdir /size osfn("bin$")
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  pathnames, task
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
