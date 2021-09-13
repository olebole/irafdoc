.. _texpand:

texpand — Expand tables according to a set of rules.
====================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  texpand -- Expand table rows according to a set of rules.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  texpand input output rbase
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task uses a set of rules to convert each row in the input table
  into one or more rows in the output table. Except for these
  conversions, the output table is identical to the input table. The set
  of rules is contained in a text file specified by the 'rbase' parameter. 
  Each rule has two parts, the target and
  the action.
  <P>
  Rules are applied in the following ways.  The task reads a row
  from the input table. It then looks at the target part of each rule in
  the rules file in the order that they were placed in the file. If the
  input row does not match the target part of any rule, it is written to
  the output table without being changed.  
  Otherwise, the first rule whose target matches the
  input row is used to convert the input row. The columns and values
  contained in the action part of the rule are used to modify the
  input row to produce a new output row. After the new row is produced, the set
  of rules is searched again to see if any of the rules can be applied
  to the new row. This process continues until no further matches can be
  found, at which point the new rows are written to the output table.
  <P>
  For example, suppose the following rules are contained in the rules
  file:
  <PRE>
  <P>
  SEX = M &amp;&amp; NAME = ANY =&gt; NAME = Tom || NAME = Dick || NAME = Harry;
  SEX = F &amp;&amp; NAME = ANY =&gt; NAME = Mary || NAME = Jane;
  SEX = X =&gt; SEX = M || SEX = F;
  <P>
  </PRE>
  And suppose the input table contains the following information:
  <PRE>
  <P>
  NAME		SEX		TITLE
  ANY		X		Astronomer
  <P>
  </PRE>
  The first two rules impose two conditions, the first on the value of
  the 'SEX' column and the second on the value of the 'NAME' column. While
  the value of the 'NAME' column matches the conditions in the first two
  rules, the value of 'SEX' does not. The third rule only imposes one
  condition, which does match the row in the input table. Thus the third
  rule of the rule file is applied to the input table and the following
  intermediate result is produced:
  <P>
  <PRE>
  <P>
  NAME		SEX		TITLE
  ANY		M		Astronomer
  ANY		F		Astronomer
  <P>
  </PRE>
  The rules file is searched again, and now the first rule matches the
  first row and the second rule matches the second row. So the following
  result is produced when these two rules are applied:
  <PRE>
  <P>
  NAME		SEX		TITLE
  Tom		M		Astronomer
  Dick		M		Astronomer
  Harry		M		Astronomer
  Mary		F		Astronomer
  Jane		F		Astronomer
  <P>
  </PRE>
  The rules file is searched again, and because no matches are found,
  the results are written to the output table.
  <P>
  The above example shows some of the syntax of the rules file. The
  target and action parts of a rule are separated by the symbol "<TT>=&gt;</TT>" and
  the entire rule is terminated by a semicolon. Unlike the above
  example, a rule need not be contained on a single line; it can be
  split among as many lines as desired, since the semicolon marks the
  end of the rule. The amount of white space used is also optional,
  symbols and identifiers may be run together or separated by blanks,
  tabs, and blank lines. Comments may be placed on any line; they begin
  with the "<TT>#</TT>" character and run to the end of the line. The different
  conditions in the target part of a rule are separated by the symbol
  "<TT>&amp;&amp;</TT>". Each condition consists of a column name and a column value
  separated by an equals sign. The different results in the action part
  of a rule are separated by the symbol "<TT>||</TT>". Each result consists of a
  set of column names and values separated by equals signs. If there is
  more than one column name and value in the result, the different
  name/value pairs are separated by "<TT>&amp;&amp;</TT>" symbols. An example of a rule
  with all these syntax elements is:
  <PRE>
  <P>
  TARGET = ANY &amp;&amp; OBSERVER = ANY =&gt;		   # Two conditions
  	TARGET=M31 &amp;&amp; OBSERVER = HUBBLE ||	   # First result
  	TARGET='OMEGA CENT' &amp;&amp; OBSERVER = STRUVE ; # Second result
  <P>
  </PRE>
  Notice that in the above example that an identifier containing a blank
  can be used if the identifier is enclosed in quotes. Double quotes
  could also have been used. Case is significant in an identifier. If a
  syntax error is detected in a rules file or a column is named which
  does occur in the input table, the task is terminated with a syntax
  error. The error message contains the line and line number where the
  error was detected and a brief message indicating the type of error.
  <P>
  This task can also be used to process more than one table by using file
  name templates for the 'input' and 'output' parameters instead of file names.
  Because processing each table takes a relatively long time, the
  parameter 'verbose' can be set to "<TT>yes</TT>" so that the name of each table
  will be displayed when it is processed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [file name template]'>
  <DD>Name of a table, or list of tables, used as input to the task
  </DD>
  </DL>
  <DL>
  <DT><B>output [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output [file name template]'>
  <DD>Name of a table, or list of tables, to be produced as output to the task. The
  number of input and output tables must be equal.
  </DD>
  </DL>
  <DL>
  <DT><B>rbase [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rbase' Line='rbase [file name]'>
  <DD>The file containing the rules used to expand the tables.
  </DD>
  </DL>
  <DL>
  <DT><B>(debug = "<TT></TT>") [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(debug = "") [file name]'>
  <DD>The file containing the debugging output. If the file name is blank or null,
  no debugging output is produced. When creating a set of rules, the output
  produced by this task is not always what you expect. Turning on the debugging
  output prints all the intermediate rule expansions to the designated file
  as an aid in debugging the set of rules.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = no) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = no) [boolean]'>
  <DD>Display the names of the input and output tables on the terminal screen (i.e.,
  STDOUT) after each file is processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Expand the table 'example' into 'example_2' using the rules in
  'xrules.txt':
  <P>
  <PRE>
  tt&gt; texpand example.tab example_2.tab xrules.txt
  </PRE>
  <P>
  2. Expand a set of fos tables using the rules in 'fosrules.txt':
  <P>
  <PRE>
  tt&gt; texpand y*.tab y*%%_2%.tab fosrules.txt verbose+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The task cannot expand tables with boolean columns.
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
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
