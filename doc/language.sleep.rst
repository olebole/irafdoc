.. _sleep:

sleep — Hibernate for a specified time
======================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sleep -- suspend process execution for the specified interval
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sleep [nsec]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>nsec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsec' Line='nsec'>
  <DD>The number of seconds to sleep.  Defaults to 0.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>sleep</I> command causes the task to hibernate for the specified
  amount of time.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Sleep for 10 seconds, and then ring the bell.
  <P>
  	cl&gt; sleep 10; beep
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wait
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
