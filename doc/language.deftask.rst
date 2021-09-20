.. _deftask:

deftask: Test if a task is defined
==================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <pre>
  defpac  -- test if the named package is defined
  deftask -- test if the named task is defined
  defpar  -- test if the named parameter is defined
  defvar  -- test if the named environment variable is defined
  </pre>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <pre>
  defpac  (pacname)
  deftask (taskname)
  defpar  (param)
  defvar  (variable)
  </pre>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>pacname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pacname' Line='pacname' -->
  <dd>An IRAF package name.
  </dd>
  </dl>
  <dl>
  <dt><b>taskname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='taskname' Line='taskname' -->
  <dd>An IRAF taskname.  It may be specified as <span style="font-family: monospace;">"taskname"</span> or as
  <span style="font-family: monospace;">"packagename.taskname"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>param</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='param' Line='param' -->
  <dd>An IRAF parameter name.  It may be specified as <span style="font-family: monospace;">"paramname"</span>,
  <span style="font-family: monospace;">"taskname.paramname"</span> or <span style="font-family: monospace;">"packagename.taskname.paramname"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>variable</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='variable' Line='variable' -->
  <dd>An environment variable name.  It may be specified as <span style="font-family: monospace;">"varname"</span>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  These routines return a boolean value indicating whether the
  relevant parameter, task or package has been defined.
  A task becomes defined when the package to which it belongs is <span style="font-family: monospace;">"loaded"</span>
  by entering the name of the package as a command, or whenever a <i>task</i>
  declaration is input to the CL.  A parameter becomes defined when the
  task to which it belongs is defined; the task need not be currently
  executing for its parameters to be defined.  When a package is exited,
  e.g., after entry of the <i>bye</i> command, all the task and parameter
  declarations for the package are discarded.  Environment variables may
  be either in the host environment, or in the CL environment as a result
  of a <i>set</i> or <i>reset</i> statement.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Test if a task exists.
  </p>
  <pre>
  	cl&gt; if (deftask ("system.page"))
  	&gt;&gt;&gt;	print ("task page exists")
  	&gt;&gt;&gt; else
  	&gt;&gt;&gt;	print ("task page not found")
  	task page exists
  	cl&gt;
  </pre>
  <p>
  2. Add the value of the named parameter into a sum, but only if the parameter
  exists (the example is for a script).
  </p>
  <pre>
  	sum = 0
  	for (i=0;  i &lt;= 10;  i+=1) {
  	    parname = "data" // i
  	    if (defpar (parname)
  		sum += parname
  	}
  </pre>
  <p>
  3. Checked whether the 'IRAFARCH' environment variable is defined.
  </p>
  <pre>
  	cl&gt; if (defvar("IRAFARCH")) {
  	&gt;&gt;&gt;    print ("IRAFARCH is " // envget("IRAFARCH")
  	&gt;&gt;&gt; }
  	&gt;&gt;&gt; ;
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  package, task, redefine, lparam
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
