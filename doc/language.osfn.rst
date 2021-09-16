.. _osfn:

osfn — Return the host system equivalent of an IRAF filename
============================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  osfn -- convert an IRAF filename to a host system filename
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  string = osfn (vfn)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>vfn  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vfn' Line='vfn  '>
  <DD>The IRAF virtual filename to be translated into a host filename.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Osfn</I> is a string valued intrinsic function which takes an IRAF virtual
  filename as input and returns the equivalent host system filename as output.
  <I>Osfn</I> can only be called as a function.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the host equivalent of the vfn "<TT>hlib$login.cl</TT>".
  <P>
  	cl&gt; = osfn ("<TT>hlib$login.cl</TT>")
  <P>
  2. Compute a host filename for use as an argument to a foreign task
  (see help <I>task</I> for more information on foreign tasks).
  <P>
  <PRE>
  	cl&gt; task $vdir = "$directory"	# VMS directory lister
  	cl&gt; vdir /size osfn("bin$")
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pathnames, task
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
