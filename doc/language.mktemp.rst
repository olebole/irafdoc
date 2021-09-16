.. _mktemp:

mktemp — Make a temporary (unique) file name
============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mktemp -- make a unique file name
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mktemp root
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>root</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='root' Line='root'>
  <DD><BR>
  The root (prefix) for the generated filename.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Mktemp</I> returns a unique filename string which may be used to create
  a temporary file name.  The string is the concatenation of three elements: the
  input argument, the process id, and a final character which changes on
  each call.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a unique filename with the root "<TT>sav</TT>" in the logical
  directory "<TT>tmp</TT>".
  <P>
  	savefile = mktemp ("<TT>tmp$sav</TT>")
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Since some time may elapse between the creation of the filename and the
  creation of a file with that name, there is no guarantee that the name
  will still be unique when it is actually used, however the algorithm used
  to generate the name makes filename collisions unlikely.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
