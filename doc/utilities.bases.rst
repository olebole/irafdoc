.. _bases:

bases — Convert an integer to hex, octal, and binary
====================================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  bases -- Convert an integer to hex, octal, and binary
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bases i
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>i</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='i' Line='i'>
  <DD>Integer for base conversion.
  </DD>
  </DL>
  <DL>
  <DT><B>nbyte = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbyte' Line='nbyte = 0'>
  <DD>Number of bytes of precision.  Allowed values are "<TT>0</TT>", "<TT>1</TT>", "<TT>2</TT>", or "<TT>4</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print labels for columns?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The BASES task converts an input integer value to equivalent values in
  other base systems.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert the number 256 (in various bases).  Note the <TT>'x'</TT> and <TT>'b'</TT> suffix
  appended to the value to change the input base value:
  <P>
  <PRE>
  	ecl&gt; bases 256					# decimal input
  	  dec    hex    octal   7654 3210 7654 3210
  	  256   0100x  000400b  0000 0001 0000 0000
  	ecl&gt; bases 256x					# hex input
  	  dec    hex    octal   7654 3210 7654 3210
  	  598   0256x  001126b  0000 0010 0101 0110
  	ecl&gt; bases 256b					# octal input
  	  dec  hex  oct   7654 3210
  	  174  AEx  256b  1010 1110
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
