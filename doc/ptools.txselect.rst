.. _txselect:

txselect — Select records from a list of apphot/daophot text databases
======================================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  txselect - select records from an APPHOT/DAOPHOT text database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  txselect textfiles outfiles expr
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles'>
  <DD>The APPHOT/DAOPHOT text database(s) containing the records from which the
  selection is to be made.
  </DD>
  </DL>
  <DL>
  <DT><B>outfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outfiles' Line='outfiles'>
  <DD>The output APPHOT/DAOPHOT text database(s) containing the selected records.
  </DD>
  </DL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression to be evaluated once for each record.
  Each input record for which <I>expr</I> evaluates as "<TT>yes</TT>" will be
  written to the output file.
  If <I>expr</I> = yes, a copy is made of the input file.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TXSELECT selects a subset of the records
  from a set of  APPHOT/DAOPHOT text databases
  and writes the new records out to another set of text databases.
  <P>
  The output records are selected on the basis of an input boolean
  expression <I>expr</I> whose variables are the field names
  specified by the #N keywords or the parameters specified by the
  #K keywords in the APPHOT/DAOPHOT text database.
  If after substituting the values associated
  with a particular record into the field name variables the
  expression evaluates
  to yes, that record is included in the output database.
  <P>
  The supported
  operators and functions are briefly described below. A detailed description
  of the boolean expression evaluator and its syntax can be found
  in the manual page for the IMAGES package HEDIT task.
  <P>
  The following logical operators can be used in the boolean expression. 
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
  character.  The meta-characters listed below. 
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
  The boolean expression may also include arithmetic operators and functions.
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
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Select the records from the output of the APPHOT CENTER task for
  which 100. &lt;= XCENTER &lt;= 200. and 300. &lt;= YCENTER &lt;= 400.
  <P>
  <PRE>
  	pt&gt; txselect m92.ctr.1 m92out \<BR>
  	    "XCE &gt;= 100. &amp;&amp; XCE &lt;= 200. &amp;&amp; YCE &gt;= 300. &amp;&amp; YCE &lt;= 400."
  </PRE>
  <P>
  2. Select the records from the output of the APPHOT PHOT task for which
  the first magnitude is not equal to INDEF.
  <P>
  <PRE>
  	pt&gt; txselect n4147.mag.2 n4147out "MAG[1] != INDEF"
  </PRE>
  <P>
  3. Select the records from the output of the DAOPHOT ALLSTAR task
     for which CHI &lt;= 5.0 and MERR &lt;= .10 magnitudes.
  <P>
  <PRE>
  	pt&gt; txselect m92b.al.1 m92out "CHI &lt;= 5.0 &amp;&amp; MERR &lt;= 1.0"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  TXSELECT does not allow arrays in the expression field.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.hselect,images.hedit,ptools.tbselect,tables.tselect,ptools.pselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
