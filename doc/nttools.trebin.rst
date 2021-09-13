.. _trebin:

trebin — Resample a table to uniform spacing.
=============================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  trebin -- Resample tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  trebin intable outtable column start end step
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task resamples tables.
  The grid on which to interpolate an input table
  may be specified either by a table giving explicit values
  or by start, end, and step values for uniform spacing.
  The column names in the output table
  will be the same as in the input table.
  <P>
  If the independent variable column ('column')
  in the input table contains scalar values,
  each numeric column in the input table will be rebinned
  to the values of the output independent variable.
  Character and boolean columns
  will not be copied to the output table.
  Columns that contain arrays will also not be copied to output.
  On the other hand,
  if the input independent variable column contains arrays
  rather than scalar values,
  then each row of the input table will be rebinned individually.
  Scalar columns will be copied to output unchanged.
  Array columns which have the same length as 'column'
  will be rebinned and written to the output table;
  if the array size is not the same,
  the column will not be copied to output.
  <P>
  Except for function = "<TT>linear</TT>",
  the output values are obtained by interpolation, not by fitting.
  The distinction is important when rebinning to a spacing ('step')
  that is significantly coarser than the spacing of the input data.
  For functions other than linear,
  each interpolated value is obtained as follows.
  The values of the input data
  nearest the current output independent variable value (X) are selected;
  the input data are then interpolated at X
  to obtain the value to write to the output table.
  For function = "<TT>nearest</TT>", only one input point is used;
  for function = "<TT>poly3</TT>" or "<TT>spline</TT>", four input points are used.
  This is appropriate for rebinning
  to a spacing not much different from the input data.
  For resampling noisy data
  to a significantly wider spacing than the input data, however,
  these options will give very poor results.
  In the latter case, function = "<TT>linear</TT>" (the default) should be used.
  This option uses a linear fit to all the data
  within an interval of width 'step' centered on each output X value.
  If there are fewer than two input points in a given interval, however,
  the value is interpolated the same way as is done for the other functions;
  that is, the two input points nearest to X are selected,
  and the value is interpolated at X
  (note that these two points can be outside the 'step' interval).
  <P>
  A significant limitation to this task is that
  there is no option to conserve total counts.
  'trebin' averages the data values,
  rather than summing the input bins.
  What 'trebin' does is appropriate for flux-calibrated spectra,
  or for time series data expressed as count rate,
  but it would not be correct for data in counts,
  or for count rate spectra.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>List of input tables to be resampled.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>Output tables or directory.
  The number of output tables must match the number of input tables unless
  'outtable' is a directory name.
  </DD>
  </DL>
  <DL>
  <DT><B>column [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Name of the independent variable column in the input table,
  i.e., the column on which the data are being resampled.
  The same column name is used for all input tables.
  The values in this column must be
  either monotonically increasing or decreasing.
  INDEF values and trailing 'padvalue' (described below) will be ignored.
  <P>
  The data type of the column is assumed to be a numeric type.
  </DD>
  </DL>
  <DL>
  <DT><B>start [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start' Line='start [real]'>
  <DD>If the independent variable values at which to interpolate the input values
  are to be uniformly spaced,
  they may be specified using 'start', 'end', and 'step'.
  'start' is the first value of the output independent variable.
  <P>
  See also 'xtable';
  'start', 'end', and 'step' will be ignored if 'xtable' was specified.
  </DD>
  </DL>
  <DL>
  <DT><B>end [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='end' Line='end [real]'>
  <DD>Last value of the independent variable.
  This may be rounded up by a fraction of 'step' to ensure that the entire
  range from 'start' to 'end' is included in the output table.
  </DD>
  </DL>
  <DL>
  <DT><B>step [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step [real]'>
  <DD>Increment in independent variable.
  The sign of 'step' is ignored;
  internally to 'trebin' the sign will be set to negative
  if 'start' is larger than 'end'.
  <P>
  If 'start' and 'end' are the same,
  the output table will contain one row,
  and 'step' will only be used for the case of function = "<TT>linear</TT>".
  For other values of 'function',
  since the data will be interpolated at just the one point 'start',
  the step size will not be needed.
  </DD>
  </DL>
  <DL>
  <DT><B>(xtable) [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(xtable) [file name template]'>
  <DD>The independent variable values at which to interpolate the input values
  can either be specified explicitly with 'xtable'
  or computed using 'start', 'end', 'step'.
  If 'xtable' is specified,
  there must either be just one table name,
  or the number of names must be the same as
  the number of names in 'intable'.
  If there is only one 'xtable',
  it will be used for all input tables.
  <P>
  'xtable' must contain only one column.
  The name of the column does not matter;
  it does not need to be the same as given by 'column'.
  If the actual table contains more than one column,
  use the column selector syntax to specify which one to use.
  The column may contain either scalar values or arrays.
  If the column contains arrays,
  there must be only one row;
  if the actual table contains more than one row,
  use the row selector syntax to specify which one to use.
  <P>
  The data type of the column is assumed to be a numeric type.
  </DD>
  </DL>
  <DL>
  <DT><B>(function = "<TT>linear</TT>") [string, allowed values: nearest | linear | </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(function = "linear") [string, allowed values: nearest | linear | '>
  <DD>poly3 | spline]
  <P>
  Interpolation function.
  There must be at least four rows in the input table
  for cubic polynomial or cubic spline interpolation.
  Two rows are required for linear interpolation,
  and only one for nearest-neighbor.
  <P>
  The "<TT>linear</TT>" option uses a linear fit,
  while all other functions are interpolations
  using only the required number of points
  nearest the value of the independent variable.
  <P>
  If an input table does not contain enough rows,
  or if a column being interpolated contains INDEF values
  so that the total number of values is insufficient for interpolation,
  the output column will be entirely INDEF;
  if verbose = yes, a message will be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>(extrapolate = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(extrapolate = no) [boolean]'>
  <DD>Extrapolate if out of bounds?  See 'value' below.
  </DD>
  </DL>
  <DL>
  <DT><B>(value = INDEF) [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(value = INDEF) [real]'>
  <DD>Value to use if out of bounds.
  The independent variable values
  at which the input table is to be interpolated
  may fall outside the range of values
  in the independent variable column in the input table.
  The value to write to the output table
  for out of bounds independent variables depends on
  the 'extrapolate' and 'value' parameters.
  If 'extrapolate' is yes, then 'value' is ignored,
  and the interpolation function is used for extrapolation.
  If 'extrapolate' is no,
  then 'value' is written to each dependent variable column
  for each row that the independent variable
  is outside the range of values in the input table.
  Note that for columns of type integer or short,
  'value' should be within the range of possible values of that type,
  and if 'value' contains a fractional part
  it will be rounded to the nearest integer.
  </DD>
  </DL>
  <DL>
  <DT><B>(padvalue = INDEF) [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(padvalue = INDEF) [real]'>
  <DD>Trailing INDEF values in the independent variable column
  (either in 'intable' or in 'xtable')
  will be ignored.
  'padvalue' can be used to specify an additional value,
  such as zero,
  which will also be ignored
  if it occurs at the end of an array of independent variable values.
  Values will be trimmed off the end of the array
  until a value that is neither INDEF nor 'padvalue' is encountered.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>If verbose = yes,
  the input and output table names will be printed as they are processed,
  and the names of columns that are not being copied to output
  will also be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>(Version) [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(Version) [string]'>
  <DD>This gives the date of installation of the current version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Resample all the columns in all tables beginning with "<TT>hr</TT>" so the values
  in the "<TT>Wavelength</TT>" column range from 3000 to 8000 in steps of 10.
  The output tables will have the same names, but will be written in the
  directory "<TT>home$spec</TT>" (which should be different from the default directory).
  <P>
  <PRE>
    tt&gt; trebin hr*.tab "home$spec/" Wavelength 3000. 8000. 10.
  </PRE>
  <P>
  2. Interpolate the text table "<TT>in</TT>" at a single point,
  where the value in column one is 5,
  and print the results on the standard output.
  <P>
  <PRE>
    tt&gt; trebin in STDOUT c1 5. 5. 0.
  </PRE>
  <P>
  3. Interpolate the table from example 2
  onto the array of independent variable values
  in column "<TT>wavelength</TT>" at row 37 of "<TT>x1d.fits</TT>".
  As in example 2,
  the independent variable in "<TT>in</TT>" is the first column, "<TT>c1</TT>".
  <P>
  <PRE>
    tt&gt; trebin in STDOUT c1 xtable="x1d.fits[r:row=37][c:wavelength]"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  A column which contains an integer bit mask
  will be interpolated as if it were an ordinary numeric column,
  which is not the correct behavior.
  <P>
  Sometimes a table contains array columns
  where the allocated array size is (or can be)
  larger than the number of elements actually used.
  In this case, a scalar column might be used
  to specify the effective array length.
  The array size in the output table
  will typically be different from the array size in the input table;
  'trebin' will update the allocated array size,
  but it will not modify any scalar column that gives the effective array size.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables'
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
