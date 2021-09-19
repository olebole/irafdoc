.. _set:

set: Set an environment variable
================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <pre>
    set -- set the value of an IRAF environment variable
  reset -- reset (overwrite) the value of an IRAF environment variable
  </pre>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <pre>
  set [varname = valuestring]
  reset [varname = valuestring]
  </pre>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>varname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='varname' Line='varname' -->
  <dd>The environment variable to be defined or set.
  </dd>
  </dl>
  <dl>
  <dt><b>valuestring</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='valuestring' Line='valuestring' -->
  <dd>The new string value of the environment variable.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The CL maintains a list of environment variables, each of which consists
  of a keyword = value pair.  The <i>set</i> and <i>reset</i> operators are used
  to define new environment variables, or to set new values for old environment
  variables.  The two operators are equivalent with the exception that if the
  named environment variable is already defined, <i>set</i> will push a new,
  temporary value for the variable, whereas <i>reset</i> will overwrite the most
  recent definition of the variable.  Environment variables may be examined
  using the <i>show</i> task or the <i>envget</i> intrinsic function.
  </p>
  <p>
  A particular use for the environment variables is in the definition
  of IRAF logical names for directories.  If an environment variable is set to
  a string corresponding to a system-dependent directory name,
  then the environment variable may then be used within the CL to
  refer to that directory.
  </p>
  <p>
  For example,
  </p>
  <pre>
  	set	testdir = "/usr/iraf/testdir"		# Unix
  	set	testdir = "dua2:[iraf.testdir]"		# VMS
  	task	tst1 = testdir$tst1.cl
  </pre>
  <p>
  New IRAF logicals may be defined in terms or existing IRAF logical names,
  i.e., logical names are recursively expanded.
  </p>
  <pre>
  	set	subdir1 = testdir$subdir1/
  	task	tst2 = subdir1$tst2.e
  </pre>
  <p>
  If the <i>set</i> command is entered without any arguments the current
  environment list is printed in the reverse of the order in which the
  definitions were made.  If a variable has been redefined both the
  final and original definition are shown.   The <i>show</i> command can be
  used to show only the current value.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Define the data directory <tt>"dd"</tt> on a remote node, and call <i>implot</i>
  to make plots of an image which resides in the remote directory.
  </p>
  <pre>
  	cl&gt; set dd = lyra!/u2/me/data
  	cl&gt; implot dd$picture
  </pre>
  <p>
  2. Temporarily change the value of the variable <i>printer</i>.  The new
  value is discarded when the <i>bye</i> is entered.
  </p>
  <pre>
  	cl&gt; cl
  	cl&gt; set printer = qms
  		...
  	cl&gt; bye
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  show, envget
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
