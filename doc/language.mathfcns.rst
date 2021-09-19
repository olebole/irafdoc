.. _mathfcns:

mathfcns: Mathematical routines
===============================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mathfcns -- math functions available in the CL
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Synopsis</h3>
  <!-- BeginSection: 'SYNOPSIS' -->
  <pre>
  Function    Return value		  Description
  
  sin(x)		real			sine
  cos(x)		real			cosine
  tan(x)		real			tangent
  atan2(x,y)	real			arc-tangent
  exp(x)		real			e**x
  log(x)		real			natural logarithm
  log10(x)	real			common logarithm
  frac(x)		real			fractional part
  abs(x)		type of argument	absolute value
  min(a,b,...)	type of min. arg	minimum of a list of values
  max(a,b,...)	type of max. arg	maximum of a list of values
  real(x)		real			convert to real
  int(x)		integer			integer part
  </pre>
  <!-- EndSection:   'SYNOPSIS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  A number of mathematical functions are available under the CL.  In general
  they return real values and may be used wherever a real expression is
  valid.  The input arguments may be integer or real and may be mixed in
  cases where the function has more than one argument.
  Exceptions:
  </p>
  <pre>
      abs(x) 	returns real or integer depending on its argument
      int(x)	returns an integer
      min,max	return a copy of the min/max operand, no type change
  </pre>
  <p>
  Note that the intrinsic functions <i>int</i> and <i>real</i> may be called
  to decode string valued arguments.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  y = sin (x)
    = 180 / 3.1415927 * atan2 (x, y)
  i = int (max (4.3, x, y, 2))
    = 1. - (sin(.5)**2 + cos(.5)**2)
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  An invalid argument list to a math function (e.g. log(-1)) will terminate
  a script.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  strings
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'SYNOPSIS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
