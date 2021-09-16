.. _wait:

wait — Wait for all background jobs to complete
===============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wait -- wait for a background job to terminate
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wait [job job ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>job</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='job' Line='job'>
  <DD>A background job number, as printed when the job is submitted,
  or as given by the <I>jobs</I> command.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>wait</I> task causes the CL to hibernate until a background job or
  jobs terminates.  No arguments, or a job number of 0 means to wait
  until all background jobs finish, while other arguments can be
  specified to wait for a particular job.  If a background job is
  not running the wait returns immediately.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Wait for any background jobs to finish, beeping the terminal when done.
  <P>
  	cl&gt; wait;beep
  <P>
  2. Wait for job 3 to terminate.
  <P>
  	cl&gt; wait 3
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Deadlock is possible.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  jobs, kill, service
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
