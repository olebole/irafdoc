.. _txselect:

txselect: Select records from a list of apphot/daophot text databases
=====================================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  txselect - select records from an APPHOT/DAOPHOT text database
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txselect textfiles outfiles expr
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles' -->
  <dd>The APPHOT/DAOPHOT text database(s) containing the records from which the
  selection is to be made.
  </dd>
  </dl>
  <dl>
  <dt><b>outfiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outfiles' Line='outfiles' -->
  <dd>The output APPHOT/DAOPHOT text database(s) containing the selected records.
  </dd>
  </dl>
  <dl>
  <dt><b>expr</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='expr' Line='expr' -->
  <dd>The boolean expression to be evaluated once for each record.
  Each input record for which <i>expr</i> evaluates as <tt>"yes"</tt> will be
  written to the output file.
  If <i>expr</i> = yes, a copy is made of the input file.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TXSELECT selects a subset of the records
  from a set of  APPHOT/DAOPHOT text databases
  and writes the new records out to another set of text databases.
  </p>
  <p>
  The output records are selected on the basis of an input boolean
  expression <i>expr</i> whose variables are the field names
  specified by the #N keywords or the parameters specified by the
  #K keywords in the APPHOT/DAOPHOT text database.
  If after substituting the values associated
  with a particular record into the field name variables the
  expression evaluates
  to yes, that record is included in the output database.
  </p>
  <p>
  The supported
  operators and functions are briefly described below. A detailed description
  of the boolean expression evaluator and its syntax can be found
  in the manual page for the IMAGES package HEDIT task.
  </p>
  <p>
  The following logical operators can be used in the boolean expression. 
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
  character.  The meta-characters listed below. 
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
  The boolean expression may also include arithmetic operators and functions.
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
  1. Select the records from the output of the APPHOT CENTER task for
  which 100. &lt;= XCENTER &lt;= 200. and 300. &lt;= YCENTER &lt;= 400.
  </p>
  <pre>
  	pt&gt; txselect m92.ctr.1 m92out \<br>
  	    "XCE &gt;= 100. &amp;&amp; XCE &lt;= 200. &amp;&amp; YCE &gt;= 300. &amp;&amp; YCE &lt;= 400."
  </pre>
  <p>
  2. Select the records from the output of the APPHOT PHOT task for which
  the first magnitude is not equal to INDEF.
  </p>
  <pre>
  	pt&gt; txselect n4147.mag.2 n4147out "MAG[1] != INDEF"
  </pre>
  <p>
  3. Select the records from the output of the DAOPHOT ALLSTAR task
     for which CHI &lt;= 5.0 and MERR &lt;= .10 magnitudes.
  </p>
  <pre>
  	pt&gt; txselect m92b.al.1 m92out "CHI &lt;= 5.0 &amp;&amp; MERR &lt;= 1.0"
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  TXSELECT does not allow arrays in the expression field.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  images.hselect,images.hedit,ptools.tbselect,tables.tselect,ptools.pselect
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
