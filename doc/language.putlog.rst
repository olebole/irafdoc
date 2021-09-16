.. _putlog:

putlog — Put a message to the logfile
=====================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  putlog -- put a message to the logfile
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  putlog logmsg
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>logmsg</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmsg' Line='logmsg'>
  <DD>A message to append to the logfile.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Putlog</I> is used to add user messages to the logfile.  The CL parameter
  <I>keeplog</I> must be set to `yes' for this to take effect.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  For executable tasks, the only way to call <I>putlog</I> currently is via
  the low-level CLIO routine clcmd().
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cl, logging
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  >
  
