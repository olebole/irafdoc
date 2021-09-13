.. _tscopy:

tscopy — Copy row/column subsets of tables using selectors.
===========================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tscopy -- Copy tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tscopy intable outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is used to copy tables.  The input may be a filename
  template, including wildcard characters or the name of a file (preceded
  by an @ sign) containing table names.  The output may be either a directory
  specification or a list of table names.  If the output is a list of tables
  then there must be the same number of names in the input and output lists,
  and the names are taken in pairs, one from input and one from output.
  The input and output tables must not be the same.
  <P>
  This task supports row/column selectors in the input table name. These
  may be used to select subsets of both rows and columns from the input table.
  Type 'help selectors' to see a description of the selector syntax. 
  <P>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files 'table.tab' and 'table.lis' in the current directory,
  for example, then the command "<TT>tscopy tab* test/</TT>" would copy both files to the subdirectory
  'test'.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of one or more tables to be copied. Row/column selectors are supported.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>Either a directory name or a list of output table names. The standard
  value "<TT>STDOUT</TT>" generates ASCII output that can be redirected to a file.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display names of input and output tables as files are copied?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To simply copy a table:
  <P>
  <PRE>
        cl&gt; tscopy table tablecopy
  </PRE>
  <P>
  2. To copy a table into an ASCII table:
  <P>
  <PRE>
        cl&gt; tscopy table STDOUT &gt; table.txt
  </PRE>
  <P>
  3. To copy several tables:
  <P>
  <PRE>
        cl&gt; tscopy table1,table2,tab67 a,b,c
        cl&gt; tscopy tab*.tab a,b,c
  </PRE>
  In the latter case the extension is given explicitly in case there
  are other files beginning with "<TT>tab</TT>" that are not tables; there must
  be exactly three tables beginning with "<TT>tab</TT>" because the output list
  has three names.
  <P>
  4. To copy a set of tables to a new directory:
  <P>
  <PRE>
        cl&gt; tscopy table*.tab directory
  			or
        cl&gt; tscopy table*.tab directory$
  			or
        cl&gt; tscopy table*.tab osdirectory
  </PRE>
  <P>
  where "<TT>directory</TT>" is an IRAF environment variable for a directory name,
  and "<TT>osdirectory</TT>" is an operating system directory name
  (e.g., "/user/me/"<TT> in UNIX).
  <P>
  5. To copy a subset of rows and columns:
  <P>
  <PRE>
        cl&gt; tscopy "table.tab[c:wave,flux][r:wave=(4000:5000)]" tableout
  </PRE>
  <P>
  This command will copy only columns named </TT>"wave"<TT> and </TT>"flux"<TT> from the input
  table to the output. It will also select and copy only the rows in which
  the </TT>"wave"<TT> value lies between 4000 and 5000.
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
  selectors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
