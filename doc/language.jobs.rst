.. _jobs:

jobs — Display status of background jobs
========================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  jobs -- display the status of background jobs
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  jobs
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  None.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Jobs</I> is used to display the status of background jobs.
  If no job number is specified then all the status of all background
  jobs is displayed.  For each job there is one line of output, e.g.
  <P>
      [2]  0:14 +Running  copy file1 file2 &amp;
  <P>
  Here 2 is the job number of the job; 0:14 is the clock time in minutes and
  seconds since the job was submitted; `Running' indicates that the task is
  currently running while the <TT>`+'</TT> indicates that this was the last background
  job started.   The remainder of the line is a copy of the actual command
  used to start the job.
  <P>
  The possible states for a background job are:
  <P>
  <PRE>
  	Done    -- the job has finished normally
  	Exit N  -- the job terminated with exit code N
  	Stopped -- the job is waiting for input from the user
  			(see the <I>service</I> command)
  	Running -- the job is currently executing
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  cl&gt; jobs
      [1]  21:13  Done      mkhelp &gt;&amp; dev$null &amp; 
      [2]   0:05 +Running   count *.hlp &gt; _junk &amp; 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Exit codes are rarely displayed when jobs terminate abnormally.
  The CL checks for background job termination only when a command is
  entered, hence the elapsed time shown will often be greater than it
  should be.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  kill, service
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
