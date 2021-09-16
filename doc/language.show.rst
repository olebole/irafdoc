.. _show:

show — Show an environment variable
===================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  show -- show the current value of an IRAF environment variable
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  show [varname]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>varname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='varname' Line='varname'>
  <DD>The name of the environment variable to be displayed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>show</I> command shows the current values of all defined environment
  variables if called with no arguments, or the value of a specific variable
  if an argument is given.  Unlike <I>set</I>, only current values are shown,
  not the entire history of the definitions of environment variables.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Show the current default printer device.
  	
  	cl&gt; show printer
  <P>
  2. Show all "<TT>std</TT>" (standard i/o stream) related variables.
  <P>
  	cl&gt; show | match std
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  set
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
