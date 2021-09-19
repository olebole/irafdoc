.. _tcheck:

tcheck: Check STSDAS table element values.
==========================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tcheck -- Check STSDAS table values.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tcheck input chkfile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task allows the user to check the correctness of an STSDAS table by
  printing the rows, column names, and values of selected table
  elements.  The table elements selected are controlled by lines in the
  check file.  Table elements are printed by placing their names on a
  line in the check file followed by the word <tt>"when"</tt> and a logical
  expression. The values of all columns listed before the <tt>"when"</tt> will be
  printed for each row for which the expression is true. For example,
  </p>
  <pre>
  ylower, yupper when ylower &gt;= yupper
  </pre>
  <p>
  prints the values of the columns 'ylower' and 'yupper' for any row
  where 'ylower' is greater than or equal to 'yupper'.  If the column names
  and expression are too long to fit on a line, the line can be
  continued by placing a backslash as the last character on the line.
  Lines which are blank, or start with a comment character (#), are
  ignored.
  </p>
  <p>
  An expression may contain table column names and string or numerical
  constants. The table column names may be in either lower or upper
  case. If <tt>"when"</tt> is a column name, place it in upper case so its
  meaning will not be ambiguous. String constants may be surrounded by
  either single or double quotes. Numeric constants will be treated as
  real numbers if they contain a decimal point or integers if they do
  not.
  </p>
  <p>
  The expression must have a boolean (logical) value. Boolean operators 
  can be used in an expression in either their SPP or Fortran form:
  </p>
  <pre>
  equal		==	.eq.	not equal		!=	.ne.
  less than	&lt;	.lt.	less than or equal	&lt;=	.le.
  greater than	&gt;	.gt.	greater than or equal	&gt;=	.ge.
  or		||	.or.	and			&amp;&amp;	.and.
  negation	!	.not.	
  </pre>
  <p>
  The expression may also include the usual arithmetic operators and
  functions. Arguments to the trigonometric functions must be in
  degrees. The available operators are:
  </p>
  <pre>
  addition		+	 subtraction		-
  multiplication		*	 division		/
  negation		-	 exponentiation		**
  string concatenation	//
  </pre>
  <p>
  Three new functions are available in addition to the usual arithmetic
  functions:
  </p>
  <pre>
  
  row     takes no argument, returns current row number 
  delta   takes two dates (in CDBS format) and returns the
          number of days between them
  match   returns true if the first argument matches one or more
          of the remaining arguments of the function (the arguments 
          may be of any type, as long as all arguments have the
          same type. 
  </pre>
  <p>
  The
  following is a list of the available functions:
  </p>
  <pre>
  absolute value	abs(x)	     cosine		cos(x)
  sine		sin(x)	     tangent		tan(x)
  arc cosine	acos(x)	     arc sine		asin(x)
  arc tangent	atan(x)	     arc tangent	atan2(x,y)
  exponential	exp(x)	     square root	sqrt(x)
  natural log	log(x)	     common log		log10(x)
  minimum		min(x,y)     maximum		max(x,y)
  modulo		mod(x,y)     row number		row()
  date difference	delta(x,y)   equality		match (x,y,z,...)
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input [file name template]' -->
  <dd>List of tables that will be checked.
  </dd>
  </dl>
  <dl>
  <dt><b>chkfile [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='chkfile' Line='chkfile [file name]' -->
  <dd>Text file containing consistency checks.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The simplest check is when a table element has one legal
  value. This can be tested for as follows.
  </p>
  <pre>
  overscan when overscan != 5
  </pre>
  <p>
  2. A range of values can also be tested, as in the following expressions.
  </p>
  <pre>
  aper_area when aper_area &lt;= 0.0
  pass_dir when detnum &lt; 1 || detnum &gt; 2
  </pre>
  <p>
  3. If a keyword has several legal values and they do not form a range, it
  may be easier to use the match function.
  </p>
  <pre>
  fgwa_id when ! match(fgwa_id,"CAM","H13","H19","H27",\<br>
  "H40","H57","H78")
  </pre>
  <p>
  4. The value of one keyword may depend on the value of another. This can
  be tested by combining the conditions with an <tt>"and"</tt>:
  </p>
  <pre>
  aper_pos when aper_id == 'A-1' &amp;&amp; aper_pos != 'SINGLE'
  polar_id when fgwa_id == 'CAM' &amp;&amp; polar_id != <tt>'C'</tt>
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Bernie Simon.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hcheck
  </p>
  <p>
  Type <tt>"help tables opt=sys"</tt> for a description of the 'tables' package.
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
