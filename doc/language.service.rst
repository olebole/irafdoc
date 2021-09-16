.. _service:

service — Service a query from a background job
===============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  service -- respond to a parameter request from a bkg job
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  service [job]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>job</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='job' Line='job'>
  <DD>A background job number (defaults to 1).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  When a background job requires input from the terminal (e.g. if it queries
  for a parameter), the job enters a stopped state, and a message is
  displayed on the terminal.  At the user's convenience, he should respond
  with a <I>service</I> command specifying the appropriate job number.  The
  <I>jobs</I> command can also be used to see what jobs require attention.
  <P>
  After entering the <I>service</I> command, any prompt sent by the background
  job is displayed, and the user may return a single line
  of input to the background task.  Should more lines be needed several
  <I>service</I> calls may be necessary.  The user may service jobs in
  any order, regardless of how the requests from the background jobs were
  received.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  1. Respond to a parameter request from job 3.
  <P>
  	cl&gt; service 3
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  If one never responds to a request for service from a background job, the job
  will eventually time out and abort.  In principle it is possible to service
  queued background jobs as well as interactive (subprocess) background jobs,
  but in practice the request for service never reaches the terminal (and thus
  the user), hence all parameters should be specified before submitting a job
  to execute in a queue.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  jobs, kill
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'BUGS' 'SEE ALSO'  >
  
