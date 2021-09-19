.. _jobs:

jobs: Display status of background jobs
=======================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  jobs -- display the status of background jobs
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  jobs
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  None.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Jobs</i> is used to display the status of background jobs.
  If no job number is specified then all the status of all background
  jobs is displayed.  For each job there is one line of output, e.g.
  </p>
  <p>
      [2]  0:14 +Running  copy file1 file2 &amp;
  </p>
  <p>
  Here 2 is the job number of the job; 0:14 is the clock time in minutes and
  seconds since the job was submitted; `Running' indicates that the task is
  currently running while the <tt>`+'</tt> indicates that this was the last background
  job started.   The remainder of the line is a copy of the actual command
  used to start the job.
  </p>
  <p>
  The possible states for a background job are:
  </p>
  <pre>
  	Done    -- the job has finished normally
  	Exit N  -- the job terminated with exit code N
  	Stopped -- the job is waiting for input from the user
  			(see the <i>service</i> command)
  	Running -- the job is currently executing
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  cl&gt; jobs
      [1]  21:13  Done      mkhelp &gt;&amp; dev$null &amp; 
      [2]   0:05 +Running   count *.hlp &gt; _junk &amp; 
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Exit codes are rarely displayed when jobs terminate abnormally.
  The CL checks for background job termination only when a command is
  entered, hence the elapsed time shown will often be greater than it
  should be.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  kill, service
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
