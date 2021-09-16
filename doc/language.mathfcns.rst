.. _mathfcns:

mathfcns — Mathematical routines
================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mathfcns -- math functions available in the CL
  </UL>
  <! EndSection:   'NAME'>
  <H3>Synopsis</H3>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  <P>
  <PRE>
  Function    Return value		  Description
  <P>
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
  </PRE>
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A number of mathematical functions are available under the CL.  In general
  they return real values and may be used wherever a real expression is
  valid.  The input arguments may be integer or real and may be mixed in
  cases where the function has more than one argument.
  Exceptions:
  <P>
  <PRE>
      abs(x) 	returns real or integer depending on its argument
      int(x)	returns an integer
      min,max	return a copy of the min/max operand, no type change
  </PRE>
  <P>
  Note that the intrinsic functions <I>int</I> and <I>real</I> may be called
  to decode string valued arguments.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  y = sin (x)
    = 180 / 3.1415927 * atan2 (x, y)
  i = int (max (4.3, x, y, 2))
    = 1. - (sin(.5)**2 + cos(.5)**2)
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  An invalid argument list to a math function (e.g. log(-1)) will terminate
  a script.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  strings
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
