.. _access:

access — Test if a file exists
==============================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  access -- test whether a file exists
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bool = access (filename)
  bool = imaccess (imagename)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>filename</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filename' Line='filename'>
  <DD>The name of the file whose existence is to be tested.
  </DD>
  </DL>
  <DL>
  <DT><B>imagename</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imagename' Line='imagename'>
  <DD>The name of the image whose existence is to be tested.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Access</I> is a boolean intrinsic function returning true ("<TT>yes</TT>") if the
  named file exists.  <I>Access</I> can only be called as a function in an
  expression, not as a task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Type a file if it exists.
  <P>
  <PRE>
      if (access ("lib$motd"))
  	type ("lib$motd")
      else
  	error (11, "File not found")
  </PRE>
  <P>
  2. Tell if a file and an image exists.
  <P>
  <PRE>
  	cl&gt; = access ("lib$motd")
  	cl&gt; = imaccess ("dev$pix")
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  An optional second argument should be added to test whether the named file
  can be accessed for reading or writing.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
