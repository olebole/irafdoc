.. _defpac:

defpac — Test if a package is defined
=====================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  defpac  -- test if the named package is defined
  deftask -- test if the named task is defined
  defpar  -- test if the named parameter is defined
  defvar  -- test if the named environment variable is defined
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  defpac  (pacname)
  deftask (taskname)
  defpar  (param)
  defvar  (variable)
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pacname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pacname' Line='pacname'>
  <DD>An IRAF package name.
  </DD>
  </DL>
  <DL>
  <DT><B>taskname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='taskname' Line='taskname'>
  <DD>An IRAF taskname.  It may be specified as "<TT>taskname</TT>" or as
  "<TT>packagename.taskname</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>param</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='param' Line='param'>
  <DD>An IRAF parameter name.  It may be specified as "<TT>paramname</TT>",
  "<TT>taskname.paramname</TT>" or "<TT>packagename.taskname.paramname</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>variable</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='variable' Line='variable'>
  <DD>An environment variable name.  It may be specified as "<TT>varname</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  These routines return a boolean value indicating whether the
  relevant parameter, task or package has been defined.
  A task becomes defined when the package to which it belongs is "<TT>loaded</TT>"
  by entering the name of the package as a command, or whenever a <I>task</I>
  declaration is input to the CL.  A parameter becomes defined when the
  task to which it belongs is defined; the task need not be currently
  executing for its parameters to be defined.  When a package is exited,
  e.g., after entry of the <I>bye</I> command, all the task and parameter
  declarations for the package are discarded.  Environment variables may
  be either in the host environment, or in the CL environment as a result
  of a <I>set</I> or <I>reset</I> statement.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Test if a task exists.
  <P>
  <PRE>
  	cl&gt; if (deftask ("system.page"))
  	&gt;&gt;&gt;	print ("task page exists")
  	&gt;&gt;&gt; else
  	&gt;&gt;&gt;	print ("task page not found")
  	task page exists
  	cl&gt;
  </PRE>
  <P>
  2. Add the value of the named parameter into a sum, but only if the parameter
  exists (the example is for a script).
  <P>
  <PRE>
  	sum = 0
  	for (i=0;  i &lt;= 10;  i+=1) {
  	    parname = "data" // i
  	    if (defpar (parname)
  		sum += parname
  	}
  </PRE>
  <P>
  3. Checked whether the 'IRAFARCH' environment variable is defined.
  <P>
  <PRE>
  	cl&gt; if (defvar("IRAFARCH")) {
  	&gt;&gt;&gt;    print ("IRAFARCH is " // envget("IRAFARCH")
  	&gt;&gt;&gt; }
  	&gt;&gt;&gt; ;
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  package, task, redefine, lparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
