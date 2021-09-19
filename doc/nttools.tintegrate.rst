.. _tintegrate:

tintegrate: Numerically integrate one column with respect to another.
=====================================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tintegrate -- Calculate the integral of one table column with
  respect to another.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tintegrate table integrand independent
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The program evaluates the integral of the column name passed to
  'integrand' with respect to
  the column passed to 'independent' using the simple trapezoidal rule.
  The column passed to 'independent' must have values
  sorted in ascending order.
  INDEF values in either column are ignored, and there must be at least
  two good points common to both columns.
  The result is written to STDOUT and also recorded as a task parameter
  'integral'.
  </p>
  <p>
  If the 'independent' parameter is null or blank,
  the values in the 'integrand' column will simply be added up.
  Note that this is not exactly the same as the trapezoidal rule
  for integrating over row number.  (A row number column
  can be created using 'tcalc'.)  When integrating over a column
  that contains the row numbers,
  'tintegrate' adds together all rows except the first and last
  with unit weight;
  the first and last are included with a weight of one half.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]' -->
  <dd>The input table.
  </dd>
  </dl>
  <dl>
  <dt><b>integrand [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='integrand' Line='integrand [string]' -->
  <dd>Column name whose contents will be the integrand.
  </dd>
  </dl>
  <dl>
  <dt><b>independent [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='independent' Line='independent [string]' -->
  <dd>Column name whose contents will be the independent variable;
  the values in this column must be increasing with row number.
  If 'independent' is null,
  then 'tintegrate' will just sum the values in the 'integrand' column.
  </dd>
  </dl>
  <dl>
  <dt><b>(integral) [real]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(integral) [real]' -->
  <dd>The result returned by the task.
  This is an output parameter; it is not directly changed by the user.
  </dd>
  </dl>
  <dl>
  <dt><b>(ptsused) [integer]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(ptsused) [integer]' -->
  <dd>The number of points used in calculating the integral.
  This is also an output parameter and is not specified by the user.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Calculate the integral of flux over wavelength,
  printing the result to STDOUT
  (and also storing it in the 'integral' parameter).
  </p>
  <pre>
  tt&gt; tintegrate intab flux lambda
         integral= 0.8752311663155779 using 401 points
  </pre>
  <p>
  2.  Sum the values of flux, rather than integrating over wavelength.
  </p>
  <pre>
  tt&gt; tintegrate intab flux ""
         integral= 30.32557976245881 using 401 points
  
  as an alternative:
  
  tt&gt; tstat intab flux
  # civ  flux
  # nrows            mean     stddev   median       min      max
    401     0.07562488719   0.171107  -0.0381  -0.72729  0.22527
  tt&gt; =0.07562488719 * 401
  30.32557976319
  
  </pre>
  <p>
  3.  Integrate the flux over row number.
  This is the same as summing the flux except for the first and last rows.
  </p>
  <pre>
  tt&gt; tcalc intab row rownum datatype="real" colfmt="%8.1f"
  tt&gt; tintegrate intab flux row
        integral= 30.34466478228569 using 401 points
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by David Giaretta.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  tcalc
  tstat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
