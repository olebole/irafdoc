.. _tcheck:

tcheck — Check STSDAS table element values.
===========================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tcheck -- Check STSDAS table values.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tcheck input chkfile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task allows the user to check the correctness of an STSDAS table by
  printing the rows, column names, and values of selected table
  elements.  The table elements selected are controlled by lines in the
  check file.  Table elements are printed by placing their names on a
  line in the check file followed by the word "<TT>when</TT>" and a logical
  expression. The values of all columns listed before the "<TT>when</TT>" will be
  printed for each row for which the expression is true. For example,
  <P>
  <PRE>
  ylower, yupper when ylower &gt;= yupper
  </PRE>
  <P>
  prints the values of the columns 'ylower' and 'yupper' for any row
  where 'ylower' is greater than or equal to 'yupper'.  If the column names
  and expression are too long to fit on a line, the line can be
  continued by placing a backslash as the last character on the line.
  Lines which are blank, or start with a comment character (#), are
  ignored.
  <P>
  An expression may contain table column names and string or numerical
  constants. The table column names may be in either lower or upper
  case. If "<TT>when</TT>" is a column name, place it in upper case so its
  meaning will not be ambiguous. String constants may be surrounded by
  either single or double quotes. Numeric constants will be treated as
  real numbers if they contain a decimal point or integers if they do
  not.
  <P>
  The expression must have a boolean (logical) value. Boolean operators 
  can be used in an expression in either their SPP or Fortran form:
  <P>
  <PRE>
  equal		==	.eq.	not equal		!=	.ne.
  less than	&lt;	.lt.	less than or equal	&lt;=	.le.
  greater than	&gt;	.gt.	greater than or equal	&gt;=	.ge.
  or		||	.or.	and			&amp;&amp;	.and.
  negation	!	.not.	
  </PRE>
  <P>
  The expression may also include the usual arithmetic operators and
  functions. Arguments to the trigonometric functions must be in
  degrees. The available operators are:
  <P>
  <PRE>
  addition		+	 subtraction		-
  multiplication		*	 division		/
  negation		-	 exponentiation		**
  string concatenation	//
  </PRE>
  <P>
  Three new functions are available in addition to the usual arithmetic
  functions:
  <PRE>
  <P>
  row     takes no argument, returns current row number 
  delta   takes two dates (in CDBS format) and returns the
          number of days between them
  match   returns true if the first argument matches one or more
          of the remaining arguments of the function (the arguments 
          may be of any type, as long as all arguments have the
          same type. 
  </PRE>
  <P>
  The
  following is a list of the available functions:
  <P>
  <PRE>
  absolute value	abs(x)	     cosine		cos(x)
  sine		sin(x)	     tangent		tan(x)
  arc cosine	acos(x)	     arc sine		asin(x)
  arc tangent	atan(x)	     arc tangent	atan2(x,y)
  exponential	exp(x)	     square root	sqrt(x)
  natural log	log(x)	     common log		log10(x)
  minimum		min(x,y)     maximum		max(x,y)
  modulo		mod(x,y)     row number		row()
  date difference	delta(x,y)   equality		match (x,y,z,...)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [file name template]'>
  <DD>List of tables that will be checked.
  </DD>
  </DL>
  <DL>
  <DT><B>chkfile [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='chkfile' Line='chkfile [file name]'>
  <DD>Text file containing consistency checks.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The simplest check is when a table element has one legal
  value. This can be tested for as follows.
  <P>
  <PRE>
  overscan when overscan != 5
  </PRE>
  <P>
  2. A range of values can also be tested, as in the following expressions.
  <P>
  <PRE>
  aper_area when aper_area &lt;= 0.0
  pass_dir when detnum &lt; 1 || detnum &gt; 2
  </PRE>
  <P>
  3. If a keyword has several legal values and they do not form a range, it
  may be easier to use the match function.
  <P>
  <PRE>
  fgwa_id when ! match(fgwa_id,"CAM","H13","H19","H27",\<BR>
  "H40","H57","H78")
  </PRE>
  <P>
  4. The value of one keyword may depend on the value of another. This can
  be tested by combining the conditions with an "<TT>and</TT>":
  <P>
  <PRE>
  aper_pos when aper_id == 'A-1' &amp;&amp; aper_pos != 'SINGLE'
  polar_id when fgwa_id == 'CAM' &amp;&amp; polar_id != <TT>'C'</TT>
  </PRE>
  <P>
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
  hcheck
  <P>
  Type "<TT>help tables opt=sys</TT>" for a description of the 'tables' package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
