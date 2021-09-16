.. _radix:

radix — Encode a number in the specified radix
==============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  radix -- encode a number in any radix
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  string = radix (number, newradix)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>number</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='number' Line='number'>
  <DD>The integer number to be encoded.
  </DD>
  </DL>
  <DL>
  <DT><B>newradix</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newradix' Line='newradix'>
  <DD>The radix or base in which the number is to be printed,
  e.g., 2 (binary), 8 (octal), 10 (decimal), 16 (hex), and so on.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Radix</I> is a string valued intrinsic function which formats an integer
  number in the indicated radix, return the encoded string as the function
  value.  Note that the CL permits numbers to be input in octal or hex format
  (trailing B or X suffix respectively), allowing common numeric conversions
  to decimal to be done directly.  The <I>radix</I> function is however the
  only CL function currently available for printing numbers in bases other
  than 10.  <I>Radix</I> can only be called as a function.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the hex number 7cde in binary.
  <P>
  	cl&gt; = radix (7cdex, 2)
  <P>
  2. Print the hex number 7cde in decimal.
  <P>
  	cl&gt; = 7cdex
  <P>
  3. Print the number in variable I in decimal, octal, and hex.
  <P>
  	cl&gt; print (i, radix(i,8), "<TT> </TT>", radix(i,16))
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Very large bases produce strange results.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  print
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
