.. _radix:

radix: Encode a number in the specified radix
=============================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  radix -- encode a number in any radix
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  string = radix (number, newradix)
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>number</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='number' Line='number' -->
  <dd>The integer number to be encoded.
  </dd>
  </dl>
  <dl>
  <dt><b>newradix</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newradix' Line='newradix' -->
  <dd>The radix or base in which the number is to be printed,
  e.g., 2 (binary), 8 (octal), 10 (decimal), 16 (hex), and so on.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Radix</i> is a string valued intrinsic function which formats an integer
  number in the indicated radix, return the encoded string as the function
  value.  Note that the CL permits numbers to be input in octal or hex format
  (trailing B or X suffix respectively), allowing common numeric conversions
  to decimal to be done directly.  The <i>radix</i> function is however the
  only CL function currently available for printing numbers in bases other
  than 10.  <i>Radix</i> can only be called as a function.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the hex number 7cde in binary.
  </p>
  <p>
  	cl&gt; = radix (7cdex, 2)
  </p>
  <p>
  2. Print the hex number 7cde in decimal.
  </p>
  <p>
  	cl&gt; = 7cdex
  </p>
  <p>
  3. Print the number in variable I in decimal, octal, and hex.
  </p>
  <p>
  	cl&gt; print (i, radix(i,8), <tt>" "</tt>, radix(i,16))
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Very large bases produce strange results.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  print
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
