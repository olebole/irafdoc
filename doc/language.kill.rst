.. _kill:

kill — Kill a background job
============================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  kill -- kill a background job
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  kill job [job ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>job</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='job' Line='job'>
  <DD>A background job number, as returned by <I>jobs</I>, or as printed when
  the job is submitted.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Kill</I> is used to forcibly terminate a background job.
  The user must specify the job number of the task to be killed.
  The job number is displayed when the job is started, and may also
  be seen using the <I>jobs</I> command.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  1. Kill job number 4.
  <P>
  	cl&gt; kill 4
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  jobs, service
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  >
  
