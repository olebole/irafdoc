.. _error:

error: Print error code and message and abort
=============================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  error -- abort a task
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  error errcode errmsg
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>errcode</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='errcode' Line='errcode' -->
  <dd>An integer code identifying the error (not used at present in the CL since
  error handlers are not supported).
  </dd>
  </dl>
  <dl>
  <dt><b>errmsg</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='errmsg' Line='errmsg' -->
  <dd>A string describing the error.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Error</i> may be used to force an error exit from a script.
  The error message will be displayed, and control will return to the
  most recent interactive cl.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Abort the current task if there is an attempt to compute a negative
  square root.
  </p>
  <pre>
  	if (x &lt; 0)
  	    error (1, "sqrt of a negative number (x=" // x // ")")
  	else
  	    y = sqrt (x)
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  There is currently no way to post an error handler to receive control
  if <i>error</i> is called.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cl, bye, logout
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
