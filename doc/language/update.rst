.. _update:

update: Update a task's parameters (flush to disk)
==================================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  update task [task ...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>task</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='task' Line='task' -->
  <dd>An IRAF task name.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Normally when a task terminates the values of the task parameters used
  are stored for the next invocation of the task in a disk file in the
  users UPARM directory.  However if the task parameters have been
  cached by the <i>cache</i> command, this will not be done until the
  CL terminates.  In the case of a background job, automatic updating of
  parameters is disabled.  The <i>update</i> command is used to force the
  parameters for a task to be updated on disk.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  1. Update the parameters for the <i>page</i> task.
  </p>
  <p>
  	cl&gt; update page
  </p>
  <!-- EndSection:   'EXAMPLE' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The parameter set is only updated on disk if a parameter has been modified
  since the last update.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cache, unlearn
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'BUGS' 'SEE ALSO'  -->
  
