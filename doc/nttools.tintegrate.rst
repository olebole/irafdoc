tintegrate — Numerically integrate one column with respect to another.
======================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tintegrate (Jan96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tintegrate (Jan96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tintegrate</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tintegrate -- Calculate the integral of one table column with
  respect to another.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tintegrate table integrand independent
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The program evaluates the integral of the column name passed to
  'integrand' with respect to
  the column passed to 'independent' using the simple trapezoidal rule.
  The column passed to 'independent' must have values
  sorted in ascending order.
  INDEF values in either column are ignored, and there must be at least
  two good points common to both columns.
  The result is written to STDOUT and also recorded as a task parameter
  'integral'.
  <P>
  If the 'independent' parameter is null or blank,
  the values in the 'integrand' column will simply be added up.
  Note that this is not exactly the same as the trapezoidal rule
  for integrating over row number.  (A row number column
  can be created using 'tcalc'.)  When integrating over a column
  that contains the row numbers,
  'tintegrate' adds together all rows except the first and last
  with unit weight;
  the first and last are included with a weight of one half.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>The input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_integrand">integrand [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='integrand' Line='integrand [string]'>
  <DD>Column name whose contents will be the integrand.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_independent">independent [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='independent' Line='independent [string]'>
  <DD>Column name whose contents will be the independent variable;
  the values in this column must be increasing with row number.
  If 'independent' is null,
  then 'tintegrate' will just sum the values in the 'integrand' column.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(integral) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(integral) [real]'>
  <DD>The result returned by the task.
  This is an output parameter; it is not directly changed by the user.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ptsused) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ptsused) [integer]'>
  <DD>The number of points used in calculating the integral.
  This is also an output parameter and is not specified by the user.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Calculate the integral of flux over wavelength,
  printing the result to STDOUT
  (and also storing it in the 'integral' parameter).
  <P>
  <PRE>
  tt&gt; tintegrate intab flux lambda
         integral= 0.8752311663155779 using 401 points
  </PRE>
  <P>
  2.  Sum the values of flux, rather than integrating over wavelength.
  <P>
  <PRE>
  tt&gt; tintegrate intab flux ""
         integral= 30.32557976245881 using 401 points
  <P>
  as an alternative:
  <P>
  tt&gt; tstat intab flux
  # civ  flux
  # nrows            mean     stddev   median       min      max
    401     0.07562488719   0.171107  -0.0381  -0.72729  0.22527
  tt&gt; =0.07562488719 * 401
  30.32557976319
  <P>
  </PRE>
  <P>
  3.  Integrate the flux over row number.
  This is the same as summing the flux except for the first and last rows.
  <P>
  <PRE>
  tt&gt; tcalc intab row rownum datatype="real" colfmt="%8.1f"
  tt&gt; tintegrate intab flux row
        integral= 30.34466478228569 using 401 points
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by David Giaretta.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tcalc
  tstat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>