.. _tbselect:

tbselect: Select records from a list of apphot/daophot tables databases
=======================================================================

**Package: ptools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tbselect intable outtable expr
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable ' -->
  <dd>The list of APPHOT/DAOPHOT STSDAS table databases from which rows are
  copied.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable ' -->
  <dd>The list of output APPHOT/DAOPHOT table databases to contain the copied rows.
  The number of output tables must equal the number of input tables.
  </dd>
  </dl>
  <dl>
  <dt><b>expr</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='expr' Line='expr' -->
  <dd>The boolean expression which determines which rows are copied to the new
  table. <i>Expr</i> is evaluated once for each input row of data.
  If <i>expr</i> is <span style="font-family: monospace;">"yes"</span> a copy is made of the old input table.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TSELECT creates a new APPHOT/DAOPHOT table database containing a subset of
  the rows in the old table database.
  The rows are selected on the basis of an input boolean expression whose
  variables are table column names.
  If after substituting the values associated
  with a particular row into the column name variables the expression evaluates
  to yes, that row is included in the output table.
  </p>
  <p>
  The supported
  operators and functions are briefly described below. A detailed description
  of the boolean expression evaluator and its syntax can be found
  in the manual page for the IMAGES package HEDIT task.
  </p>
  <p>
  The following logical operators can be used in the expression. 
  </p>
  <pre>
  	equal		  ==	not equal		!=
  	less than	  &lt;	less than or equal	&lt;=
  	greater than	  &gt;	greater than or equal	&gt;=
  	or		  ||	and			&amp;&amp;
  	negation	  !	pattern match		?=
  	concatenation	  //
  </pre>
  <p>
  The pattern match character ?=  takes a
  string expression as its first argument and a pattern as its second argument.
  The result is yes if the pattern is contained in the string expression.
  Patterns are strings which may contain pattern matching meta-characters.
  The meta-characters themselves can be matched by preceeding them with the escape
  character.  The meta-characters are listed below. 
  </p>
  <pre>
  	beginning of string	^	end of string		$
  	one character		?	zero or more characters	*
  	white space		#	escape character	\<br>
  	ignore case		{	end ignore case		}
  	begin character class	[	end character class	]
  	not, in char class	^	range, in char class	-
  </pre>
  <p>
  The expression may also include arithmetic operators and functions.
  The following arithmetic operators and functions are supported.
  </p>
  <pre>
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
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Extract all stars brighter than twentieth magnitude from an
  the output of the DAOPHOT ALLSTAR task and create a new database.
  </p>
  <pre>
     pt&gt; tbselect m92.al.1 m92out "MAG &lt;= 20.0"
  </pre>
  <p>
  2. Create a new database from the output of the DAOPHOT NSTAR task by
  removing all INDEF valued magnitudes.
  </p>
  <pre>
      pt&gt; tbselect  n2264b.nst.1 n2264out  "MAG != INDEF"
  
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Column names must be set off from operators by blanks in the expression so
  that they can be correctly parsed by the expression evaluator.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ptools.txselect,tables.tselect,ptools.tbselect
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
