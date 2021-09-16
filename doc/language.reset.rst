.. _reset:

reset — Reset the value of an environment variable
==================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
    set -- set the value of an IRAF environment variable
  reset -- reset (overwrite) the value of an IRAF environment variable
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  set [varname = valuestring]
  reset [varname = valuestring]
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>varname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='varname' Line='varname'>
  <DD>The environment variable to be defined or set.
  </DD>
  </DL>
  <DL>
  <DT><B>valuestring</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='valuestring' Line='valuestring'>
  <DD>The new string value of the environment variable.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The CL maintains a list of environment variables, each of which consists
  of a keyword = value pair.  The <I>set</I> and <I>reset</I> operators are used
  to define new environment variables, or to set new values for old environment
  variables.  The two operators are equivalent with the exception that if the
  named environment variable is already defined, <I>set</I> will push a new,
  temporary value for the variable, whereas <I>reset</I> will overwrite the most
  recent definition of the variable.  Environment variables may be examined
  using the <I>show</I> task or the <I>envget</I> intrinsic function.
  <P>
  A particular use for the environment variables is in the definition
  of IRAF logical names for directories.  If an environment variable is set to
  a string corresponding to a system-dependent directory name,
  then the environment variable may then be used within the CL to
  refer to that directory.
  <P>
  For example,
  <P>
  <PRE>
  	set	testdir = "/usr/iraf/testdir"		# Unix
  	set	testdir = "dua2:[iraf.testdir]"		# VMS
  	task	tst1 = testdir$tst1.cl
  </PRE>
  <P>
  New IRAF logicals may be defined in terms or existing IRAF logical names,
  i.e., logical names are recursively expanded.
  <P>
  <PRE>
  	set	subdir1 = testdir$subdir1/
  	task	tst2 = subdir1$tst2.e
  </PRE>
  <P>
  If the <I>set</I> command is entered without any arguments the current
  environment list is printed in the reverse of the order in which the
  definitions were made.  If a variable has been redefined both the
  final and original definition are shown.   The <I>show</I> command can be
  used to show only the current value.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Define the data directory "<TT>dd</TT>" on a remote node, and call <I>implot</I>
  to make plots of an image which resides in the remote directory.
  <P>
  <PRE>
  	cl&gt; set dd = lyra!/u2/me/data
  	cl&gt; implot dd$picture
  </PRE>
  <P>
  2. Temporarily change the value of the variable <I>printer</I>.  The new
  value is discarded when the <I>bye</I> is entered.
  <P>
  <PRE>
  	cl&gt; cl
  	cl&gt; set printer = qms
  		...
  	cl&gt; bye
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  show, envget
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
