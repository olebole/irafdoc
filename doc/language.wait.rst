.. _wait:

wait: Wait for all background jobs to complete
==============================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  wait -- wait for a background job to terminate
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  wait [job job ...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>job</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='job' Line='job' -->
  <dd>A background job number, as printed when the job is submitted,
  or as given by the <i>jobs</i> command.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>wait</i> task causes the CL to hibernate until a background job or
  jobs terminates.  No arguments, or a job number of 0 means to wait
  until all background jobs finish, while other arguments can be
  specified to wait for a particular job.  If a background job is
  not running the wait returns immediately.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Wait for any background jobs to finish, beeping the terminal when done.
  </p>
  <p>
  	cl&gt; wait;beep
  </p>
  <p>
  2. Wait for job 3 to terminate.
  </p>
  <p>
  	cl&gt; wait 3
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Deadlock is possible.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  jobs, kill, service
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
