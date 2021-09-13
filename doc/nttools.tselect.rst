tselect — Create a new table from selected rows of a table.
===========================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tselect (Jul92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tselect (Jul92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tselect</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tselect -- Create a new table from selected rows of an old table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tselect intable outtable expr
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates a new table from a subset of rows in an input table.  
  The rows are selected on the basis of a boolean expression whose
  variables are table column names.  If, after substituting the values associated
  with a particular row into the column name variables, the expression evaluates
  to yes, that row is included in the output table.  Boolean operators can be used
  in the expression in either their Fortran or SPP forms.  The following boolean
  operators can be used in the expression: 
  <P>
  <PRE>
  equal		.eq.  ==	not equal		.ne.  !=
  less than	.lt.  &lt;		less than or equal	.le.  &lt;=
  greater than	.gt.  &gt;		greater than or equal	.ge.  &gt;=
  or		.or.  ||	and			.and. &amp;&amp;
  negation	.not. !		pattern match		      ?=
  </PRE>
  <P>
  The pattern match operator (?=) has no corresponding Fortran form.  It takes a
  string expression as its first argument and a pattern as its second argument.
  The result is "<TT>yes</TT>" if the pattern is contained in the string expression.
  Patterns are strings which may contain meta-characters (i.e., wildcard 
  characters used in pattern matching).
  The meta-characters themselves can be matched by preceeding them with the escape
  character (\).
  The meta-characters are: 
  <P>
  <PRE>
  beginning of string	^	end of string		$
  one character		?	zero or more characters	*
  white space		#	escape character	\<BR>
  begin ignoring case	{	end ignore case		}
  begin character class	[	end character class	]
  not, in char class	^	range, in char class	-
  </PRE>
  <P>
  The expression may also include arithmetic operators and functions.
  Trigonometric functions use degrees, not radians.  The following arithmetic
  operators and functions can be used in the expression:
  <P>
  <PRE>
  addition		+	subtraction		-
  multiplication		*	division		/
  negation		-	exponentiation		**
  concatenation		//	date difference		delta(x,y)
  absolute value		abs(x)	cosine			cos(x)
  sine			sin(x)	tangent			tan(x)
  arc cosine		acos(x)	arc sine		asin(x)
  arc tangent		atan(x)	arc tangent		atan2(x,y)
  exponential		exp(x)	square root		sqrt(x)
  natural log		log(x)	common log		log10(x)
  modulo			mod(x)	minimum			min(x,y)
  row number		row()	maximum			max(x,y)
  nearest integer		nint(x)	convert to integer	int(x)
  convert to real		real(x) convert to string	str(x)
  </PRE>
  <P>
  The row number function returns an integer value corresponding to the
  row number in the table.  The date difference function returns a real
  value corresponding to the Julian date of the first argument minus the
  Julian date of the second argument; the arguments to the data function
  must be in CDBS date format:  i.e., character strings of the form
  YYYYMMDD:HHMMSSCC.  Any field after the colon is optional.  The last
  date field (CC) is hundreths of a second.
  <P>
  One concept in most databases and in STSDAS tables is the concept of a
  null value: a value which indicates that the element is unknown or
  non-existent.  An element in an STSDAS table is null if it is INDEF in a
  numeric column or a zero length string in a text column. Evaluating
  expressions involving nulls requires a three valued logic:  true,
  false, and unknown. Any arithmetic operation on a null element should
  return another null and any comparison operation should return an
  unknown.  Unfortunately, tselect does not implement a true three
  valued logic correctly.  The code instead evaluates any expression
  containing a null element as unknown.  Since tselect only returns rows
  for which the expression is true, all such rows are excluded from the
  output of tselect.  This is usually right, but sometimes wrong, as in
  the case where two comparisons are joined by an or and one evaluates
  to true and the other evaluates to unknown.  It also sometimes returns
  nonintuitive results, as when checking that a column is not equal to
  INDEF.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>Table(s) from which rows are copied. If input is redirected, this
  parameter will ignored and input will be read from STDIN instead.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>The new table(s) containing the copied rows.
  If more than one input table was used, then the number of output 
  tables must equal the number of input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expr">expr [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr [string]'>
  <DD>The boolean expression which determines which rows are copied to the new
  table.  The expression may be placed in a list file and the name of the file
  passed to this parameter (preceded by the "<TT>@</TT>" character).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract all binary stars brighter than fifth magnitude from a catalog:
  <P>
  <PRE>
  tt&gt; tselect starcat.tab binary.tab "binary &amp;&amp; mag &lt;= 5."
  </PRE>
  <P>
  2. Create a new set of spectra where all measurements with errors greater
  than ten percent are excluded. Use file name editing to create new tables
  with the extension "<TT>.tbl</TT>" instead of "<TT>.tab</TT>":
  <P>
  <PRE>
  tt&gt; tselect  *.tab  *.%tab%tbl%  "ERROR / (FLUX + .001) &lt; .1"
  </PRE>
  <P>
  3. Create a table of engineering parameters whose names begin with a digit:
  <P>
  <PRE>
  tt&gt; tselect datalog.tab sublog.tab "name ?= '^[0-9]'"
  </PRE>
  <P>
  4. Return all observations in a schedule for the day of Dec 31, 1989:
  <P>
  <PRE>
  tt&gt; tselect schedule.tab week.tab "abs(delta(date,'19891231:12'))&lt;.5"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Column names must be set off from operators by blanks in the
  expression so that they can be correctly parsed by the expression
  evaluator.  Expressions involving nulls may evaluate incorrectly, see
  above for a discussion.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tproject, tjoin, tproduct
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>