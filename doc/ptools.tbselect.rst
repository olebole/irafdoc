.. _tbselect:

tbselect — Select records from a list of apphot/daophot tables databases
========================================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tbselect -- create a new APPHOT/DAOPHOT table database from selected rows
  of an old APPHOT/DAOPHOT table database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tbselect intable outtable expr
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable '>
  <DD>The list of APPHOT/DAOPHOT STSDAS table databases from which rows are
  copied.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable '>
  <DD>The list of output APPHOT/DAOPHOT table databases to contain the copied rows.
  The number of output tables must equal the number of input tables.
  </DD>
  </DL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression which determines which rows are copied to the new
  table. <I>Expr</I> is evaluated once for each input row of data.
  If <I>expr</I> is "<TT>yes</TT>" a copy is made of the old input table.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TSELECT creates a new APPHOT/DAOPHOT table database containing a subset of
  the rows in the old table database.
  The rows are selected on the basis of an input boolean expression whose
  variables are table column names.
  If after substituting the values associated
  with a particular row into the column name variables the expression evaluates
  to yes, that row is included in the output table.
  <P>
  The supported
  operators and functions are briefly described below. A detailed description
  of the boolean expression evaluator and its syntax can be found
  in the manual page for the IMAGES package HEDIT task.
  <P>
  The following logical operators can be used in the expression. 
  <P>
  <PRE>
  	equal		  ==	not equal		!=
  	less than	  &lt;	less than or equal	&lt;=
  	greater than	  &gt;	greater than or equal	&gt;=
  	or		  ||	and			&amp;&amp;
  	negation	  !	pattern match		?=
  	concatenation	  //
  </PRE>
  <P>
  The pattern match character ?=  takes a
  string expression as its first argument and a pattern as its second argument.
  The result is yes if the pattern is contained in the string expression.
  Patterns are strings which may contain pattern matching meta-characters.
  The meta-characters themselves can be matched by preceeding them with the escape
  character.  The meta-characters are listed below. 
  <P>
  <PRE>
  	beginning of string	^	end of string		$
  	one character		?	zero or more characters	*
  	white space		#	escape character	\<BR>
  	ignore case		{	end ignore case		}
  	begin character class	[	end character class	]
  	not, in char class	^	range, in char class	-
  </PRE>
  <P>
  The expression may also include arithmetic operators and functions.
  The following arithmetic operators and functions are supported.
  <P>
  <PRE>
  addition		+		subtraction		-
  multiplication		*		division		/
  negation		-		exponentiation		**
  absolute value		abs(x)		cosine			cos(x)
  sine			sin(x)		tangent			tan(x)
  arc cosine		acos(x)		arc sine		asin(x)
  arc tangent		atan(x)		arc tangent		atan2(x,y)
  exponential		exp(x)		square root		sqrt(x)
  natural log		log(x)		common log		log10(x)
  minimum			min(x,y)	maximum			max(x,y)
  convert to integer	int(x)		convert to real		real(x)
  nearest integer		nint(x)		modulo			mod(x)
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Extract all stars brighter than twentieth magnitude from an
  the output of the DAOPHOT ALLSTAR task and create a new database.
  <P>
  <PRE>
     pt&gt; tbselect m92.al.1 m92out "MAG &lt;= 20.0"
  </PRE>
  <P>
  2. Create a new database from the output of the DAOPHOT NSTAR task by
  removing all INDEF valued magnitudes.
  <P>
  <PRE>
      pt&gt; tbselect  n2264b.nst.1 n2264out  "MAG != INDEF"
  <P>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Column names must be set off from operators by blanks in the expression so
  that they can be correctly parsed by the expression evaluator.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txselect,tables.tselect,ptools.tbselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
