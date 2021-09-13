.. _mkdir:

mkdir — Create a new directory
==============================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkdir -- make a new directory
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkdir newdir
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>newdir</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newdir' Line='newdir'>
  <DD>New directory or subdirectory to be made.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Mkdir</I> creates a new directory with the given name.
  <I>Newdir</I> may be an IRAF virtual directory name (not a logical name)
  or a host directory name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Make a subdirectory named "<TT>sub1</TT>".
  <P>
  	cl&gt; mkdir sub1
  <P>
  2. Make a subdirectory "<TT>sub2</TT>" below "<TT>sub1</TT>".  The subdirectory "<TT>sub1</TT>" must
  already exist.
  <P>
  	cl&gt; mkdir sub1/sub2
  <P>
  3. Make a directory "<TT>blue</TT>" at the same level in the directory hierarchy as
  the current directory ("<TT>..</TT>" is a synonym for the previous directory).
  <P>
  	cl&gt; mkdir ../blue
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
