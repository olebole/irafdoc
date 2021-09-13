.. _tcalc:

tcalc — Perform arithmetic operations on table columns.
=======================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tcalc -- Perform arithmetic operations on table columns.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tcalc table outcol equals
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task evaluates an arbitrary expression that includes column names,
  constants, and operators, and creates a specified column in the 
  table---or overwrites an existing column if the specified name already exists.
  Variables in the expression are column names in either case. 
  <P>
  Columns
  may be of any type except string. If the column name contains
  non-alphanumeric characters, it should be preceded by a dollar sign
  and followed by a blank. For example, the expression "<TT>date-obs+1.</TT>"
  contains the column "<TT>date-obs</TT>", but the task thinks that it contains
  two column names, "<TT>date</TT>" and "<TT>obs</TT>".  To ensure that the expression is
  evaluated correctly, rewrite it as "<TT>$date-obs +1.</TT>". The variable
  "<TT>rownum</TT>" may also be used in an expression if there is no column in
  the table of the same name. Its value is the current row number. The
  expression will be evaluated using the data types of the columns and
  constants in the expression, with the usual rules of type promotion used in
  Fortran.  Please remember that integer division truncates.
  <P>
  The output value in any row will be set to INDEF if one or more column
  values used in the calculation is equal to INDEF. The result will be
  INDEF if either of the clauses in an if expression contains a row with
  an INDEF value. If the result of an operation is undefined (such as
  division by zero) the output column will also be set to INDEF.
  <P>
  The following Fortran-type arithmetic operators are supported.  If the
  second argument of the exponentiation is not an integer, the result
  will be undefined if the first argument is not positive.  Again, 
  remember that integer division truncates.
   
  <PRE>
  +	addition		-	subtraction
  *	multiplication		/	division
  -	negation		**	exponentiation
  </PRE>
  <P>
  The following logical operators are supported. Logical operators will
  return a value of 1 if true or 0 if false. Logical operators are
  supported in both their Fortran and SPP form.
  <P>
  <PRE>
  </DD>
  </DL>
  </PRE>
  <P>
  The following functions are supported. These functions all take a
  single argument, which may be an expression. The argument or result of
  trigonometric functions are in radians.
  <P>
  <PRE>
  abs 	absolute value		acos 	arc cosine
  asin 	arc sine		atan 	arc tangent
  cos 	arc cosine		cosh 	hyperbolic cosine
  cube 	third power		double	convert to double
  exp 	E raised to power	int 	convert to integer
  log 	natural logarithm	log10 	common logarithm
  nint 	nearest integer		real	convert to real
  sin 	sine			sinh 	hyperbolic sine
  sqr 	second power		sqrt 	square root
  tan 	tangent			tanh	hyperbolic tangent
  </PRE>
  <P>
  The following functions take two arguments.
  <P>
  <PRE>
  atan2 	arc tangent		dim 	positive difference
  max 	maximum			min 	minimum
  mod 	modulus			sign	sign transfer
  </PRE>
  <P>
  Conditional expressions of the form "<TT>if expr then expr else expr</TT>" are
  supported. The expression after the else may be another conditional
  expression.  The words "<TT>if</TT>", "<TT>then</TT>", and "<TT>else</TT>" must be surrounded by
  blanks.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table  [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='table' Line='table  [file name template]'>
  <DD>The input table, or tables; these files are modified in-place.
  Results will be written to a new column in the table unless an
  existing column name is specified, in which case the existing values
  will be overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B>outcol [string]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='outcol' Line='outcol [string]'>
  <DD>Output column name.  This is the column where results are written.
  Caution: if this column already exists, then it will be overwritten
  with the results of the calculation.  Note that column names are not
  case sensitive.
  </DD>
  </DL>
  <DL>
  <DT><B>equals [string]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='equals' Line='equals [string]'>
  <DD>The arithmetic expression to evaluate. If the expression is too long
  to pass as a parameter, place the expression in a file and set the
  value of this parameter to the file name preceded by an "<TT>@</TT>", for
  example, "<TT>@filename</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>(datatype = real) [string, allowed values: real | double | int ]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='' Line='(datatype = real) [string, allowed values: real | double | int ]'>
  <DD><P>
  Type of data stored in the output column, if it is a new column.
  </DD>
  </DL>
  <DL>
  <DT><B>(colunits) [string]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='' Line='(colunits) [string]'>
  <DD>Units for the output column, if it is a new column.  This parameter
  may be blank.
  </DD>
  </DL>
  <DL>
  <DT><B>(colfmt) [string]</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='' Line='(colfmt) [string]'>
  <DD>Print format for the output column, if it is a new column.  If this
  parameter is left blank then a default will be used.  Type "<TT>help
  ttools opt=sysdoc</TT>" for more information about print formats.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples </H3>
  <! BeginSection: 'EXAMPLES '>
  <UL>
  1.  Create a column called 'FLUX', which will contain a value equal to
  10.0**(-x/2.5) where x is the value in the column 'MAG'.  The new
  column will contain single precision data.
  <P>
  <PRE>
  tt&gt; tcalc "intab" "FLUX" "10.0**(-mag/2.5)"
  </PRE>
  <P>
  2.  Create a column called 'POLY', which will contain a value equal to
  x+x**2 where x is the row number in the table.
  <P>
  <PRE>
  tt&gt; tcalc "test" "POLY" "rownum+sqr(rownum)"
  </PRE>
  <P>
  3.  Set quotient to zero where divison by zero would otherwise occur:
  <P>
  <PRE>
  tt&gt; tcalc "test" "QUOT" "if y != 0 then x / y else 0."
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES '>
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
  imcalc
  <P>
  Type "<TT>help ttools opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES ' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
