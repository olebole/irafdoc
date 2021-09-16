.. _update:

update — Update a task's parameters (flush to disk)
===================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  update -- update the parameters for a task on disk
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  update task [task ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>An IRAF task name.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Normally when a task terminates the values of the task parameters used
  are stored for the next invocation of the task in a disk file in the
  users UPARM directory.  However if the task parameters have been
  cached by the <I>cache</I> command, this will not be done until the
  CL terminates.  In the case of a background job, automatic updating of
  parameters is disabled.  The <I>update</I> command is used to force the
  parameters for a task to be updated on disk.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  1. Update the parameters for the <I>page</I> task.
  <P>
  	cl&gt; update page
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The parameter set is only updated on disk if a parameter has been modified
  since the last update.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cache, unlearn
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'BUGS' 'SEE ALSO'  >
  
