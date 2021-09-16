.. _imaccess:

imaccess — Test if an image exists
==================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imaccess -- test whether an image exists
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bool = imaccess (image)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The name of the image whose existence is to be tested.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Imaccess</I> is a boolean intrinsic function returning true ("<TT>yes</TT>") if the
  named image exists.  The function will return false ("<TT>no</TT>") if the image doesn't
  exist, or if no image extension is supplied and the image name is ambiguous.
  <I>Imaccess</I> can only be called as a function in an expression, not as a task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the header of an image if it exists.
  <P>
  <PRE>
      if (imaccess ("dev$wpix"))
  	imheader ("dev$wpix",long+)
      else
  	error (11, "Image not found")
  </PRE>
  <P>
  2. Tell if a image exists.
  <P>
  	cl&gt; = imaccess ("<TT>dev$pix</TT>")
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
  
