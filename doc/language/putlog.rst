.. _putlog:

putlog: Put a message to the logfile
====================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  putlog logmsg
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>logmsg</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logmsg' Line='logmsg' -->
  <dd>A message to append to the logfile.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Putlog</i> is used to add user messages to the logfile.  The CL parameter
  <i>keeplog</i> must be set to `yes' for this to take effect.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  For executable tasks, the only way to call <i>putlog</i> currently is via
  the low-level CLIO routine clcmd().
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cl, logging
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  -->
  
