.. _error:

error — Print error code and message and abort
==============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  error -- abort a task
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  error errcode errmsg
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>errcode</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errcode' Line='errcode'>
  <DD>An integer code identifying the error (not used at present in the CL since
  error handlers are not supported).
  </DD>
  </DL>
  <DL>
  <DT><B>errmsg</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errmsg' Line='errmsg'>
  <DD>A string describing the error.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Error</I> may be used to force an error exit from a script.
  The error message will be displayed, and control will return to the
  most recent interactive cl.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Abort the current task if there is an attempt to compute a negative
  square root.
  <P>
  <PRE>
  	if (x &lt; 0)
  	    error (1, "sqrt of a negative number (x=" // x // ")")
  	else
  	    y = sqrt (x)
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  There is currently no way to post an error handler to receive control
  if <I>error</I> is called.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cl, bye, logout
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
