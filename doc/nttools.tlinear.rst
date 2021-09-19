.. _tlinear:

tlinear: Use linear regression to fit one or two table columns.
===============================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tlinear -- Fit a linear function to one or two table columns by linear
  regression.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tlinear intable outtable xcol ycol
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task generates fitted Y values and their residuals in two columns.
  These columns may be written to an output table, but cannot be written
  to STDOUT--only the fit parameters can be written to STDOUT.
  If there is more than one table in the input list then a separate fit
  is made for each table.
  </p>
  <p>
  When a column of weights is used (see 'wcol'),
  the weights will be applied when computing the
  coefficients of the fit (a, b),
  their standard deviations (siga2, sigb2),
  and chi squared (chi2),
  where the names in parentheses are the headings in
  the output printed to STDOUT.
  If any row has a weight that is exactly zero,
  that row will not be counted in the <tt>"pts in fit"</tt> value.
  The weights will NOT be used when computing
  the RMS of the residuals and mean of the residuals
  (residual rms, residual mean);
  these are unweighted averages
  except that rows with exactly zero weight will not be included.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]' -->
  <dd>A list of input tables containing the columns to be fit.
  A fit will be made of the columns specified by the 'xcol' and 'ycol'
  parameters.  If more than one file name is passed to 'intable', all of
  the files must use the same column names.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable = STDOUT [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable = STDOUT [file name template]' -->
  <dd>File names for creating output files, or STDOUT to send output to the screen.
  If the value of this parameter is <tt>"STDOUT"</tt> then the parameters of the fit will
  be written to STDOUT preceded by a header line (beginning with #) in tabular
  form.
  If 'outtable' is not <tt>"STDOUT"</tt> then the number of file
  names must match the number
  of names in 'intable', and the fitted Y values and residuals will be written
  to an output table with the specified name.  The parameters of the fit will
  be written to the table header.
  </dd>
  </dl>
  <dl>
  <dt><b>xcol [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xcol' Line='xcol [string]' -->
  <dd>Column name in the input tables to be fit.
  The values in this column will be fit for the X axis.
  (The same column name is used for each input table.)  If a name is not specified
  for the X values then row number is used.  The values in the 'xcol' column will
  be copied to 'outtable' unless the output is being directed to STDOUT.
  </dd>
  </dl>
  <dl>
  <dt><b>ycol [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ycol' Line='ycol [string]' -->
  <dd>Column name in the input tables containing value to be fit for the Y axis.
  (The same column name is used for each input table.)  Values in 'ycol' will
  be copied to 'outtable' unless 'outtable = STDOUT'.
  </dd>
  </dl>
  <dl>
  <dt><b>(wcol) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(wcol) [string]' -->
  <dd>Column name in 'intable' that contains weight values for X and Y.
  (The same column name is used for each input table.)  If no column
  name is passed to either the 'wcol' or 'scol' parameters, then a weight
  of 1. is used.  The value of the 'wcol' column is copied to 'outtable' unless
  'outtable = STDOUT'.
  </dd>
  </dl>
  <dl>
  <dt><b>(scol) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(scol) [string]' -->
  <dd>Column in 'intable' containing the standard deviation of X and Y.
  The X and Y values are weighted by the values in 'scol'
  as the reciprocal of the values squared.  (The same column name is used for each
  input table.)  If no value is passed to 'wcol' or 'scol', then
  a weight of 1. is used.  This task can accept either a weight value or a
  standard deviation value, but not both.  If both 'wcol' and 'scol' are
  specified, then the weight column (i.e., 'wcol') will be used.
  The value in the 'scol' column is written to 'outtable' unless 'outtable'
  = STDOUT.
  </dd>
  </dl>
  <dl>
  <dt><b>(rows = <tt>"-"</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(rows = "-") [string]' -->
  <dd>Range of rows to use for fitting the data.
  The default <tt>"-"</tt> means that all rows are used.
  (Type <tt>"help xtools.ranges"</tt> for more information.)
  </dd>
  </dl>
  <dl>
  <dt><b>(outcoly = <tt>"yfit"</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(outcoly = "yfit") [string]' -->
  <dd>Column name for fitted Y values.
  This parameter is not used if 'outtable' = STDOUT.
  This column will be double data type.
  </dd>
  </dl>
  <dl>
  <dt><b>(outcolr = <tt>"yres"</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(outcolr = "yres") [string]' -->
  <dd>Name of the column to contain residuals.
  This parameter is ignored if 'outtable' = STDOUT.
  This column will be of double data type.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Fit the values in the <tt>"flux"</tt> column in every table whose name begins with
  <tt>"hr"</tt>; put all parameters of the fits in the ASCII file <tt>"fit.lis"</tt>.
  </p>
  <pre>
    tt&gt; tlinear hr*.tab STDOUT "" flux &gt; fit.lis
  </pre>
  <p>
  2. Generate the same fits as in the previous example, but put the
  results in tables, one output for each input table.  For example,
  the fitted Y values and
  residuals for an input table named <tt>"hr465.tab"</tt> would be put in <tt>"hr465h.tab"</tt>.
  </p>
  <pre>
    tt&gt; tlinear hr*.tab hr*%%h%.tab "" flux
  </pre>
  <p>
  3. Fit the values in the <tt>"flux"</tt> column as a function of the values in the
  <tt>"wavelength"</tt> column and write all the parameters of the fit to STDOUT.
  </p>
  <pre>
    tt&gt; tlinear hr*.tab STDOUT wavelength flux
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Betty Stobie.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ranges
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
