.. _envget:

envget — Get the string value of an environment variable
========================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  envget -- get the string value of an environment variable
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  envget varname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>varname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='varname' Line='varname'>
  <DD>The environment variable whose value is to be returned.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Envget</I> returns the string value of the named environment variable.
  The user is prompted for the value if the variable has not yet been defined.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Construct a filename using the value of the environment variable
  "<TT>editor</TT>", and page the file thus named.
  <P>
  	cl&gt; page ("<TT>dev$" // envget (</TT>"editor"<TT>) // </TT>".ed"<TT>)
  <P>
  2. Compute and print the center line on the terminal screen.
  <P>
  	cl&gt; = ((int (envget (</TT>"ttynlines"<TT>)) + 1) / 2)
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  set, show
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
