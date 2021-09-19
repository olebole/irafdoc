.. _urand:

urand: Uniform random number generator
======================================

**Package: utilities**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  urand -- uniform random number generator
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  urand nlines ncols
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>nlines</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines' -->
  <dd>The number of lines of output to be generated.
  </dd>
  </dl>
  <dl>
  <dt><b>ncols</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols' -->
  <dd>The number of random numbers per output line.
  </dd>
  </dl>
  <dl>
  <dt><b>ndigits = 4</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ndigits' Line='ndigits = 4' -->
  <dd>Number of digits of precision in each random number.
  </dd>
  </dl>
  <dl>
  <dt><b>scale_factor = 1.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='scale_factor' Line='scale_factor = 1.0' -->
  <dd>Factor by which the numbers are to be scaled (multiplied).
  </dd>
  </dl>
  <dl>
  <dt><b>seed = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1' -->
  <dd>Seed for the random number generator.  If the value is <tt>"INDEF"</tt> then
  the clock time (integer seconds since 1980) is used as the seed
  value giving different random numbers for different executions.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The system random number generator is called to generate a sequence of
  random numbers in list form.  By default, the random numbers will
  be uniformly distributed over the range 0 to 1.  The number of lines
  of output, number of columns (random numbers) per line, and number of
  significant digits in each number may all be set by the caller.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Generate a sequence of 100 random numbers and graph them on the graphics
  terminal in point plot mode.  Autoscaling is turned off so that the plot
  will be scaled to the rand 0-1 (the <b>graph</b> defaults) in both axes.
  </p>
  <p>
  	cl&gt; urand 100 2 | graph po+ xa- ya-
  </p>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
