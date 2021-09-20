.. _kill:

kill: Kill a background job
===========================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  kill job [job ...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>job</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='job' Line='job' -->
  <dd>A background job number, as returned by <i>jobs</i>, or as printed when
  the job is submitted.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Kill</i> is used to forcibly terminate a background job.
  The user must specify the job number of the task to be killed.
  The job number is displayed when the job is started, and may also
  be seen using the <i>jobs</i> command.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  1. Kill job number 4.
  </p>
  <p>
  	cl&gt; kill 4
  </p>
  <!-- EndSection:   'EXAMPLE' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  jobs, service
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  -->
  
