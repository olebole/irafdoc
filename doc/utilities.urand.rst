.. _urand:

urand — Uniform random number generator
=======================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  urand -- uniform random number generator
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  urand nlines ncols
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>nlines</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines'>
  <DD>The number of lines of output to be generated.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols'>
  <DD>The number of random numbers per output line.
  </DD>
  </DL>
  <DL>
  <DT><B>ndigits = 4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ndigits' Line='ndigits = 4'>
  <DD>Number of digits of precision in each random number.
  </DD>
  </DL>
  <DL>
  <DT><B>scale_factor = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale_factor' Line='scale_factor = 1.0'>
  <DD>Factor by which the numbers are to be scaled (multiplied).
  </DD>
  </DL>
  <DL>
  <DT><B>seed = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Seed for the random number generator.  If the value is "<TT>INDEF</TT>" then
  the clock time (integer seconds since 1980) is used as the seed
  value giving different random numbers for different executions.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The system random number generator is called to generate a sequence of
  random numbers in list form.  By default, the random numbers will
  be uniformly distributed over the range 0 to 1.  The number of lines
  of output, number of columns (random numbers) per line, and number of
  significant digits in each number may all be set by the caller.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Generate a sequence of 100 random numbers and graph them on the graphics
  terminal in point plot mode.  Autoscaling is turned off so that the plot
  will be scaled to the rand 0-1 (the <B>graph</B> defaults) in both axes.
  <P>
  	cl&gt; urand 100 2 | graph po+ xa- ya-
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
