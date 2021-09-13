tstat — Get mean, standard deviation, min, and max for a column.
================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tstat (Jan2001)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tstat (Jan2001)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tstat</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tstat -- Get statistics for a table column.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tstat intable column
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task gets the mean, standard deviation, median, minimum and maximum
  values for a table column.
  The output will be written to cl parameters and may also be written either
  to the standard output (STDOUT) or to a table.
  When more than one table is specified as 'intable', the statistics are
  determined for each table separately, not cumulatively.  The values
  in the cl parameters therefore refer to the last table in the list.
  <P>
  If an input table contains only one column
  (either in fact or due to the use of a column selector with the table name),
  then the 'column' parameter is ignored,
  and statistics are computed for that one column.
  If 'intable' includes more than one table,
  the 'column' parameter may be required for some tables
  (those with more than one column) but not for others.
  <P>
  The range of rows to use for statistics
  may be restricted either by the 'rows' parameter
  or by use of a row selector with the table name.
  Both may be used, in which case 'rows'
  is interpreted to mean selected row numbers,
  rather than rows in the underlying table.
  That is, the row selector with the table name is applied first,
  then the 'rows' parameter is used to further restrict the rows.
  <P>
  For a column that contains arrays,
  this task reads all elements of all selected rows
  and computes statistics on all those elements together.
  Typical usage for array columns would be to specify just one row,
  but any number of rows may be included,
  limited only by memory.
  <P>
  Lower and upper limits may be set using the parameters 'lowlim' and 'highlim'
  such that table values outside that range are not used when computing
  the statistics.
  Either the lower or upper limit may be set individually.
  If there are no values within the range specified
  and within the range of rows given by the 'rows' parameter,
  then the average, etc, will be printed as INDEF.
  <P>
  For some tables, one can get statistics on the data in a row
  by using 'tdump' and piping the output to 'tstat'.
  See the examples for more information.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of input tables.
  Statistics will be obtained for one column, the same name in every table.
  If the input is redirected,
  this parameter need not be specified;
  that is, if there's only one command-line argument,
  it will be taken to be the column name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column in input tables.
  The statistics are gotten for the values in the column with this name.
  If an input table contains only one column,
  this parameter will be ignored,
  and you will not even be prompted for a value.
  If 'intable' includes more than one table with only one column,
  the column name does not need to be the same in each of these tables.
  For tables containing more than one column,
  this parameter is required,
  and the same column name will be used for each table in the list
  that contains more than one column.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(outtable = "<TT>STDOUT</TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(outtable = "STDOUT") [string]'>
  <DD>Output table, STDOUT, or null.
  If 'outtable' is null ("<TT></TT>") then the results will only be written to cl
  parameters (see 'nrows', 'mean', 'stddev', 'vmin', 'vmax').
  If 'outtable' is "<TT>STDOUT</TT>" then the results will be written to
  the standard output preceded by a header line (beginning with #)
  that gives the name of the table and the name of the column.
  If 'outtable' is not "<TT>STDOUT</TT>" and is not null then it is interpreted as
  a table name (just one name), and the statistics for the input tables
  will be written to separate rows of the output table.
  If the table already exists,
  the rows will be appended to what is already there.
  The output column names are given by
  the parameters 'n_tab', 'n_nam', 'n_nrows', etc.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(lowlim = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(lowlim = INDEF) [real]'>
  <DD>Values below this are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(highlim = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(highlim = INDEF) [real]'>
  <DD>Values above this are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(rows = -) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rows = -) [string]'>
  <DD>Range of rows to use for statistics.
  The default "<TT>-</TT>" means that all rows are used.
  See the help for RANGES in XTOOLS for a description of the syntax.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_tab = table) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_tab = table) [string]'>
  <DD>Column name for name of input table.
  This and other parameters that begin with "<TT>n_</TT>" are only used if the output values are
  written to a table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_nam = column) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_nam = column) [string]'>
  <DD>Column name for name of input column.
  This and other parameters that begin with "<TT>n_</TT>" are only used if the output values are
  written to a table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_nrows = nrows) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_nrows = nrows) [string]'>
  <DD>Column name for number of good rows.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_mean = mean) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_mean = mean) [string]'>
  <DD>Column name for mean.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_stddev = stddev) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_stddev = stddev) [string]'>
  <DD>Column name for standard deviation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_median = value) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_median = value) [string]'>
  <DD>Column name for median.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_min = min) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_min = min) [string]'>
  <DD>Column name for minimum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(n_max = max) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(n_max = max) [string]'>
  <DD>Column name for maximum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(nrows) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(nrows) [integer]'>
  <DD>The number of rows for which the column value was not INDEF and was
  within the range 'lowlim' to 'highlim'.
  This is a task output parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(mean) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(mean) [real]'>
  <DD>Mean value (of the last table in the input list 'intable').
  This is a task output parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(stddev) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(stddev) [real]'>
  <DD>Standard deviation of the values (not of the mean).
  This is a task output parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(median) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(median) [real]'>
  <DD>Median value.
  This is a task output parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vmin) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vmin) [real]'>
  <DD>Minimum.
  This is a task output parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vmax) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vmax) [real]'>
  <DD>Maximum.
  This is a task output parameter.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Get statistics on column "<TT>flux</TT>" in all tables, putting the output
  (assuming outtable="<TT>STDOUT</TT>") in the ASCII file 'flux.lis':
  <PRE>
  <P>
      tt&gt; tstat *.tab flux &gt; flux.lis
  </PRE>
  <P>
  2.  In order to get statistics on the data
  in a row rather than a column,
  you can use 'tdump' for one row
  and specify pwidth to be so small that
  each value will be printed on a separate line.
  The output of 'tdump' will then be a one-column table
  containing the row from the input table,
  and 'tstat' can be run on that one-column table.
  Since the input is redirected, we don't specify the table name.
  Note also that in this case the input contains only one column,
  so we don't specify the column name either.
  In this example, we get statistics on row 17 of "<TT>bs.fits</TT>":
  <PRE>
  <P>
      tt&gt; tdump bs.fits cdfile="" pfile="" \<BR>
      &gt;&gt;&gt; row=17 pwidth=15 | tstat
  </PRE>
  <P>
  3.  When the input is redirected and has multiple columns,
  the command-line argument should be the column name to use,
  not the table name.
  The table name in this case will internally be set to "<TT>STDIN</TT>".
  <PRE>
  <P>
      tt&gt; dir l+ | tstat c3
  </PRE>
  <P>
  4.  The statistics on column "<TT>flux</TT>" in 'hr465.tab' are put in parameters
  'tstat.nrows', 'tstat.mean', etc.,
  and are not written to STDOUT or to a table.
  We only include rows for which column V is no larger than 12.
  <PRE>
  <P>
      tt&gt; tstat "hr465.tab[r:v=:12][c:flux]" outtable=""
  </PRE>
  <P>
  5.  The output statistics are written to a table.  The default column name
  for the mean value is overridden:
  <PRE>
  <P>
      tt&gt; tstat hr465.tab flux outtable=hr465s.tab n_mean="mean_flux"
  </PRE>
  <P>
  6.  Get statistics on column "<TT>flux</TT>" in table 'hr465.tab', but only for
  rows 17 through 116, row 271, and row 952:
  <PRE>
  <P>
      tt&gt; tstat hr465.tab[c:flux] outtable="STDOUT" row="17-116,271,952"
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
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  thistogram, ranges
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>