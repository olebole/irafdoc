.. _dparam:

dparam — Dump a pset as a series of task.param=value assignments
================================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  dparam -- dump the parameters of a pset as a series of assignments
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  dparam pset [pset ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pset</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pset' Line='pset'>
  <DD>The name of the parameter set to be listed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Dparam</I> lists one or more parameter sets.  Psets are specified either by
  the name of the task with which the pset is associated, or by filename (pset
  files have the "<TT>.par</TT>" extension).  If a file type pset is listed the extension
  must be included, since it is the presence or absence of the filename
  extension which <B>dparam</B> uses to distinguish between task-psets and named
  (file) psets.
  <P>
  Each parameter is listed on a single line with the following format.
  The list of assignments is terminated by the string "<TT># EOF</TT>" so that programs
  reading the list from a stream can easily distinguish the end of the variable
  length list of parameters.
  <P>
  	task.param = value
  <P>
  Here "<TT>task.param</TT>" is the name of the parameter, and "<TT>value</TT>" is the current
  value of the parameter.  The assignment is skipped if the value is undefined.
  There is no way to distinguish between hidden parameters and query parameters.
  <P>
  The output from <B>dparam</B> is often used as input to programs, whereas
  the output from <B>lparam</B> is formatted in a way which makes it easier for
  humans to read.  For example, the output from <B>dparam</B> may be redirected
  into a file and used on the IRAF main command line to set the task's
  parameters, when debugging a task standalone.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the parameter for the task <I>delete</I>.  Note that the positional
  parameters are listed first, in the order in which they must be specified
  on the command line, followed by the hidden parameters.
  <P>
  <PRE>
  	cl&gt; dparam delete
  	delete.files = "temp"
  	delete.go_ahead = yes
  	delete.verify = no
  	delete.default_action = yes
  	delete.allversions = yes
  	delete.subfiles = yes
  	delete.mode = "ql"
  	# EOF
  </PRE>
  <P>
  2. List the contents of the file pset "<TT>delete.par</TT>".  Named psets such as this
  are most commonly produced using the <B>":w filename"</B> colon command in
  <B>eparam</B>, e.g., to prepare several different versions of the parameter
  set for a task.
  <P>
  	cl&gt; dparam delete.par
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  You cannot list the parameters of a task that does not have a parameter
  file (e.g., all builtin tasks).
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  eparam, lparam, cache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
