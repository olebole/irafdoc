.. _tlinear:

tlinear — Use linear regression to fit one or two table columns.
================================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tlinear -- Fit a linear function to one or two table columns by linear
  regression.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tlinear intable outtable xcol ycol
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task generates fitted Y values and their residuals in two columns.
  These columns may be written to an output table, but cannot be written
  to STDOUT--only the fit parameters can be written to STDOUT.
  If there is more than one table in the input list then a separate fit
  is made for each table.
  <P>
  When a column of weights is used (see 'wcol'),
  the weights will be applied when computing the
  coefficients of the fit (a, b),
  their standard deviations (siga2, sigb2),
  and chi squared (chi2),
  where the names in parentheses are the headings in
  the output printed to STDOUT.
  If any row has a weight that is exactly zero,
  that row will not be counted in the "<TT>pts in fit</TT>" value.
  The weights will NOT be used when computing
  the RMS of the residuals and mean of the residuals
  (residual rms, residual mean);
  these are unweighted averages
  except that rows with exactly zero weight will not be included.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of input tables containing the columns to be fit.
  A fit will be made of the columns specified by the 'xcol' and 'ycol'
  parameters.  If more than one file name is passed to 'intable', all of
  the files must use the same column names.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable = STDOUT [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable = STDOUT [file name template]'>
  <DD>File names for creating output files, or STDOUT to send output to the screen.
  If the value of this parameter is "<TT>STDOUT</TT>" then the parameters of the fit will
  be written to STDOUT preceded by a header line (beginning with #) in tabular
  form.
  If 'outtable' is not "<TT>STDOUT</TT>" then the number of file
  names must match the number
  of names in 'intable', and the fitted Y values and residuals will be written
  to an output table with the specified name.  The parameters of the fit will
  be written to the table header.
  </DD>
  </DL>
  <DL>
  <DT><B>xcol [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcol' Line='xcol [string]'>
  <DD>Column name in the input tables to be fit.
  The values in this column will be fit for the X axis.
  (The same column name is used for each input table.)  If a name is not specified
  for the X values then row number is used.  The values in the 'xcol' column will
  be copied to 'outtable' unless the output is being directed to STDOUT.
  </DD>
  </DL>
  <DL>
  <DT><B>ycol [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ycol' Line='ycol [string]'>
  <DD>Column name in the input tables containing value to be fit for the Y axis.
  (The same column name is used for each input table.)  Values in 'ycol' will
  be copied to 'outtable' unless 'outtable = STDOUT'.
  </DD>
  </DL>
  <DL>
  <DT><B>(wcol) [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wcol) [string]'>
  <DD>Column name in 'intable' that contains weight values for X and Y.
  (The same column name is used for each input table.)  If no column
  name is passed to either the 'wcol' or 'scol' parameters, then a weight
  of 1. is used.  The value of the 'wcol' column is copied to 'outtable' unless
  'outtable = STDOUT'.
  </DD>
  </DL>
  <DL>
  <DT><B>(scol) [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(scol) [string]'>
  <DD>Column in 'intable' containing the standard deviation of X and Y.
  The X and Y values are weighted by the values in 'scol'
  as the reciprocal of the values squared.  (The same column name is used for each
  input table.)  If no value is passed to 'wcol' or 'scol', then
  a weight of 1. is used.  This task can accept either a weight value or a
  standard deviation value, but not both.  If both 'wcol' and 'scol' are
  specified, then the weight column (i.e., 'wcol') will be used.
  The value in the 'scol' column is written to 'outtable' unless 'outtable'
  = STDOUT.
  </DD>
  </DL>
  <DL>
  <DT><B>(rows = "<TT>-</TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rows = "-") [string]'>
  <DD>Range of rows to use for fitting the data.
  The default "<TT>-</TT>" means that all rows are used.
  (Type "<TT>help xtools.ranges</TT>" for more information.)
  </DD>
  </DL>
  <DL>
  <DT><B>(outcoly = "<TT>yfit</TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(outcoly = "yfit") [string]'>
  <DD>Column name for fitted Y values.
  This parameter is not used if 'outtable' = STDOUT.
  This column will be double data type.
  </DD>
  </DL>
  <DL>
  <DT><B>(outcolr = "<TT>yres</TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(outcolr = "yres") [string]'>
  <DD>Name of the column to contain residuals.
  This parameter is ignored if 'outtable' = STDOUT.
  This column will be of double data type.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Fit the values in the "<TT>flux</TT>" column in every table whose name begins with
  "<TT>hr</TT>"; put all parameters of the fits in the ASCII file "<TT>fit.lis</TT>".
  <P>
  <PRE>
    tt&gt; tlinear hr*.tab STDOUT "" flux &gt; fit.lis
  </PRE>
  <P>
  2. Generate the same fits as in the previous example, but put the
  results in tables, one output for each input table.  For example,
  the fitted Y values and
  residuals for an input table named "<TT>hr465.tab</TT>" would be put in "<TT>hr465h.tab</TT>".
  <P>
  <PRE>
    tt&gt; tlinear hr*.tab hr*%%h%.tab "" flux
  </PRE>
  <P>
  3. Fit the values in the "<TT>flux</TT>" column as a function of the values in the
  "<TT>wavelength</TT>" column and write all the parameters of the fit to STDOUT.
  <P>
  <PRE>
    tt&gt; tlinear hr*.tab STDOUT wavelength flux
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Betty Stobie.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
