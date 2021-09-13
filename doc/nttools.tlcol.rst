.. _tlcol:

tlcol — List column information for a table.
============================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tlcol -- Display column information.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tlcol table
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is used to list column information for a table.  The output is
  written to STDOUT, which may be redirected to a file.  There will be one line
  of output for each column in the table, and each output line may contain the
  column name, data type, print format, and units.
  The first line of output for each table in the input list is the table
  name preceded by a # sign.
  <P>
  The output from this task may be used as input to various tasks such
  as 'tcreate', 'tprint', and 'tproject'.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of tables for which column info is to be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>(nlist = 4) [integer, min=1, max=4]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(nlist = 4) [integer, min=1, max=4]'>
  <DD>The number of items to list.
  The output will consist of 'nlist' columns,
  one line for each column that is defined in the table.
  The items listed out are column name (displayed for all 'nlist' values),
  data type (displayed if 'nlist' is 2 or higher),
  display format (if 'nlist' is 3 or higher),
  units (if 'nlist' is 4).
  If 'nlist = 1', only the column name will be displayed;
  the output list may be edited and used as input to
  'tprint', 'tdump,<TT>' '</TT>tedit', 'tread', 'tproject', or 'tquery'.
  The default of 4 can be used to generate
  a column-description file for the 'tcreate' task.
  <P>
  If a column contains an array of values at each row,
  rather than just a single element,
  the array size is shown in square brackets appended to the data type.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Display the names, data types, print formats, and units of all the
  columns in the table "<TT>example.tab</TT>":
  <P>
  <PRE>
  	tt&gt; tlcol example.tab
  </PRE>
  <P>
  2.  Print (using the 'tprint' task) specific columns:
  <PRE>
  <P>
  	tt&gt; tlcol example.tab nlist=1 &gt;colnames.lis
  	tt&gt; edit colnames.lis
          (Rearrange the column names and perhaps delete some of them.)
  	tt&gt; tprint example.tab columns=@colnames.lis
  <P>
  3.  Create a new table based on the columns in "example.tab":
  <P>
  	tt&gt; tlcol example.tab nlist=4 &gt;colnames.lis
  	tt&gt; edit colnames.lis
          (Delete or modify some column descriptions and/or add new ones.)
  	tt&gt; tcreate ex2.tab cdfile=colnames.lis ...
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
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tinfo, tcreate, tdump
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
