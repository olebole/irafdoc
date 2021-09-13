thistogram — Make a histogram of a column in a table.
=====================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>thistogram (Mar94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>thistogram (Mar94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>thistogram</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  thistogram -- Make a histogram of a table column.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  thistogram intable outtable column
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task generates a histogram of the values in a column.
  The histogram may be written to STDOUT or to a table.
  If there is more than one table in the input list then a separate histogram
  is generated for each table.
  If there is more than one input table and the histogram of the values
  in all the tables combined is needed, then the tables should first be
  merged using the 'tmerge' task with the 'option' parameter set to "<TT>append</TT>".
  <P>
  If x1 and x2 are the lower and upper limits of a particular bin,
  a value X will be included in the bin if x1 &lt;= X &lt; x2.
  Note that this also applies to the upper limit ('highval') of the last bin.
  <P>
  There are six interrelated parameters
  having to do with the number of bins, bin width, and bin locations.
  Any number of these may be specified as long as the values are consistent.
  As a minimum, only one value is required, either 'nbins' or 'dx'.
  The task computes what it doesn't have
  based on the parameters that were specified,
  or based on the minimum and maximum data values
  in the table column if necessary.
  If the minimum (maximum) column data value is used,
  that value will normally be reduced (increased) a bit
  before being used as 'lowval' ('highval')
  to ensure that the value is included in the range.
  The relationships between the parameters is as follows:
  <P>
  <PRE>
      dx = (highval - lowval) / nbins
      dx = (chigh - clow) / (nbins - 1)
      clow = lowval + dx / 2
      chigh = highval - dx / 2
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of input tables.
  A histogram will be generated for one column in the table;
  the same column name is used for each table in the list.
  The name of the column is specified using the 'column' parameter,
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable = STDOUT [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable = STDOUT [file name template]'>
  <DD>Output tables or STDOUT.
  If the value of this parameter is "<TT>STDOUT</TT>"
  then the histogram will be written to the standard output
  preceded by a header line (beginning with "<TT>#</TT>")
  that gives the number of rows included in the histogram
  and the name of the table.
  If 'outtable' is passed a file name,
  then the number of names must match the number of file names in 'intable',
  and the histogram of each input table 
  will be written to an output table of the specified name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name in input tables that will be used to generate the histogram.
  Only the values in the column with this name will be used.
  The same column name is used for each input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(nbins = 100) [integer, min=1]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(nbins = 100) [integer, min=1]'>
  <DD>Number of bins in the histogram.
  Normally either 'nbins' or 'dx' (or both) must be given.
  You could also give both 'lowval' and 'clow',
  or both 'chigh' and 'highval',
  since the bin width can be computed from these.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(lowval = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(lowval = INDEF) [real]'>
  <DD>Lower limit for histogram.
  Values below 'lowval' will not be used in generating the histogram.
  If 'lowval = INDEF', then the minimum value in the table column will be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(highval = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(highval = INDEF) [real]'>
  <DD>Upper limit for histogram.
  Values equal to or greater than 'highval' will not be used in generating
  the histogram.
  If 'highval = INDEF', then the maximum value in the table column will be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(dx = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(dx = INDEF) [real]'>
  <DD>Bin width.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(clow = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(clow = INDEF) [real]'>
  <DD>Value at the center of the first bin.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(chigh = INDEF) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(chigh = INDEF) [real]'>
  <DD>Value at the center of the last bin.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(rows = -) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rows = -) [string]'>
  <DD>Range of rows to use for generating the histogram.
  The default "<TT>-</TT>" means that all rows are used.
  (Type "<TT>help xtools.ranges</TT>" for more information.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(outcolx = value) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(outcolx = value) [string]'>
  <DD>Column name for bin centers.
  If the output is written to a table rather than to STDOUT, then 'outcolx'
  is the column name containing the bin centers.
  This column will be double precision.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(outcoly = counts) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(outcoly = counts) [string]'>
  <DD>Column name for histogram values.
  If the output is written to a table then 'outcoly' is the column name
  containing the number of counts in the bin.
  This column will be of integer data type.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Generate a histogram of the values in the 'flux' column in every table
  whose name begins with "<TT>hr</TT>"; put all the histograms in the ASCII file
  'hist.lis'.
  <P>
  <PRE>
  	tt&gt; thistogram hr*.tab STDOUT flux &gt; hist.lis
  </PRE>
  <P>
  2.  Generate the same histograms as in the previous example, but put the
  results in tables rather than displaying them on the terminal screen. 
  One output file is produced for each input table; for example,
  the histogram for an input table 'hr465.tab' would be put in 'hr465h.tab'.
  <P>
  <PRE>
  	tt&gt; thistogram hr*.tab hr*%%h%.tab flux
  </PRE>
  <P>
  3.  Plot the histogram of column <TT>'V'</TT> in 'bs.tab':
  <P>
  <PRE>
  	tt&gt; thistogram bs STDOUT V | sgraph (crvstyle="pseudohist")
  </PRE>
  <P>
  4.  Plot the same histogram as in the previous example,
  but set the spacing between bins to be 0.1.
  <P>
  <PRE>
  	tt&gt; thistogram bs STDOUT V nbins=INDEF dx=0.1 | \\<BR>
  	&gt;&gt;&gt;   sgraph (crvstyle="pseudohist")
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
  ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>