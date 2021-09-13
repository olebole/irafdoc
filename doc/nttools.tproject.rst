.. _tproject:

tproject — Create new table from selected columns in a table.
=============================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tproject -- Create a new table from selected columns of an old table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tproject intable outtable columns
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task will create a new table containing a subset of the columns in an
  old table. The column names are given as a column name template. There is an
  optional parameter, 'uniq', that filters out duplicate rows from the
  new table.
  <P>
  If you do not need to eliminate duplicate rows, you can also use tcopy 
  with a column selector on the input table name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>The table(s) from which the columns are to be copied. If input is
  redirected, this parameter will ignored and input will be read from
  STDIN instead.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>The new table(s) containing the copied columns.
  The number of output tables must equal the number of input tables.
  </DD>
  </DL>
  <DL>
  <DT><B>columns [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns [string]'>
  <DD>This is the column template describing those columns that should be
  selected from the old table and put in the new table.
  A column template consists of a list
  of either column names or column name templates that include wildcard
  characters.  Column names (or templates) are separated by commas or white space.
  This parameter will accept the name of a list file (preceded by the "<TT>@</TT>"
  character) containing all of the column names to be selected.
  If the first non-white character in the column template
  is the negation character (either "<TT>~</TT>" or "<TT>!</TT>"),
  the new table will contain those columns
  whose names DO NOT match rest of the column template.
  </DD>
  </DL>
  <DL>
  <DT><B>(uniq = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(uniq = no) [boolean]'>
  <DD>Eliminate duplicate rows from the output table?
  <P>
  If 'unique' is set to "<TT>yes</TT>", only one of each set of duplicate rows is
  included in the output table.  All columns in the output table must be
  identical for the row to be removed.  String comparisons are case
  sensitive. Care should be used in setting this option for
  large tables, as it significantly increases the running time.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract the star names, magnitudes, and colors from a catalog:
  <P>
  <PRE>
  tt&gt; tproject starcat.tab starmag.tab "name,mag,color"
  </PRE>
  <P>
  2. Exclude the measurement error from a set of spectra.  Change the file name
  extensions from "<TT>.tab</TT>" to "<TT>.tbl</TT>":
  <P>
  <PRE>
  tt&gt; tproject  *.tab  *.%tab%tbl%  "!error"
  </PRE>
  <P>
  3. Create a new table of engineering parameters using a column template stored
  in the file 'columns.dat'.  Eliminate duplicate rows:
  <P>
  <PRE>
  tt&gt; tproject datalog.tab sublog.tab @columns.dat uniq+
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
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tselect, tjoin, tproduct,tcopy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
