.. _bases:

bases: Convert an integer to hex, octal, and binary
===================================================

**Package: utilities**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  bases -- Convert an integer to hex, octal, and binary
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  bases i
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>i</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='i' Line='i' -->
  <dd>Integer for base conversion.
  </dd>
  </dl>
  <dl>
  <dt><b>nbyte = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nbyte' Line='nbyte = 0' -->
  <dd>Number of bytes of precision.  Allowed values are <span style="font-family: monospace;">"0"</span>, <span style="font-family: monospace;">"1"</span>, <span style="font-family: monospace;">"2"</span>, or <span style="font-family: monospace;">"4"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print labels for columns?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The BASES task converts an input integer value to equivalent values in
  other base systems.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Convert the number 256 (in various bases).  Note the <span style="font-family: monospace;">'x'</span> and <span style="font-family: monospace;">'b'</span> suffix
  appended to the value to change the input base value:
  </p>
  <pre>
  	ecl&gt; bases 256					# decimal input
  	  dec    hex    octal   7654 3210 7654 3210
  	  256   0100x  000400b  0000 0001 0000 0000
  	ecl&gt; bases 256x					# hex input
  	  dec    hex    octal   7654 3210 7654 3210
  	  598   0256x  001126b  0000 0010 0101 0110
  	ecl&gt; bases 256b					# octal input
  	  dec  hex  oct   7654 3210
  	  174  AEx  256b  1010 1110
  
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
