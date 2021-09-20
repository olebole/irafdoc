.. _interp:

interp: Interpolate for a value in a table of X,Y pairs
=======================================================

**Package: proto**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  interp -- compute an interpolated value from a table of x,y pairs
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  interp tbl_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>tbl_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tbl_file' Line='tbl_file' -->
  <dd>Text file containing X,Y pairs comprising the table.
  The pairs must be in either ascending or descending order.
  </dd>
  </dl>
  <dl>
  <dt><b>curve_gen = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='curve_gen' Line='curve_gen = no' -->
  <dd>If set to no, x-values are read from the file(s) specified by the parameter
  <span style="font-family: monospace;">"input"</span>. If set to yes, the parameters x1, x2, and dx are used to create
  a list of new x,y pairs interpolated at x1, x1+dx, ... x2.
  </dd>
  </dl>
  <dl>
  <dt><b>input = STDIN</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input = STDIN' -->
  <dd>File(s) containing x-values for the interpolation
  </dd>
  </dl>
  <dl>
  <dt><b>int_mode = 'linear'</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='int_mode' Line='int_mode = 'linear'' -->
  <dd>The interpolation mode may be either 'linear' or 'spline'.
  </dd>
  </dl>
  <dl>
  <dt><b>x1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='x1' Line='x1' -->
  <dd>The starting x-value for generating a series of new x,y pairs.
  </dd>
  </dl>
  <dl>
  <dt><b>x2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='x2' Line='x2' -->
  <dd>The ending x-value of the generated series of pairs.
  </dd>
  </dl>
  <dl>
  <dt><b>dx</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dx' Line='dx' -->
  <dd>The difference by which the x-values are incremented during the
  series generation.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The pairs of X,Y values are read from the tbl_file. There must be
  at least 1 pair in the file. The table is then used to interpolate
  or extrapolate new y-values for given x-values. The x-values may come
  from a file including STDIN (if curve_gen=no), or they may be
  internally generated (if curve_gen=yes) to produce a finely sampled
  version of the table. This may be useful for plotting a smooth curve
  through a series of points.
  </p>
  <p>
  The table X,Y values must be in a monotonic order, either ascending
  or descending. No restriction is made on spacing.
  </p>
  <p>
  If only one point is present in the table, all returned interpolated
  values will have the value at that point. If only two points are
  present, linear interpolation (or extrapolation) will be used.
  If additional points are present, an obscure but reliable algorithm
  is used to interpolate (or extrapolate).
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The following command reads the X,Y table from file testdata and waits for
     x-values from the terminal.
  </p>
  <pre>
      cl&gt; interp testdata STDIN
  </pre>
  <p>
  2. The following command generates points to plot (by piping to graph) in the
     range from x=10 to x=20 at intervals of 0.1 (10.0, 10.1 ... 19.9, 20.0).
  </p>
  <pre>
      cl&gt; interp testdata curve_gen=yes x1=10 x2=20 dx=.1 | graph
  </pre>
  <p>
  3. The curve will be displayed and the original points from the table
     may be overlaid by:
  </p>
  <pre>
      cl&gt; graph testdata pointmode=yes append=yes
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  If a blank (null) table filename is entered, a floating divide error
  occurs.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
