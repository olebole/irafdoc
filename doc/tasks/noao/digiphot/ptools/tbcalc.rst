.. _tbcalc:

tbcalc: Do arithmetic on a list of apphot/daophot tables databases
==================================================================

**Package: ptools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tbcalc textfiles column value
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles' -->
  <dd>The APPHOT/DAOPHOT ST tables database(s) containing the column to be recomputed.
  </dd>
  </dl>
  <dl>
  <dt><b>column</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column' -->
  <dd>The column to be recomputed. Column must be an integer or real column
  in the input file(s).
  </dd>
  </dl>
  <dl>
  <dt><b>value</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value' -->
  <dd>The arithmetic expression used to recompute the specified column.
  Value may be an integer or real expression but must match the data
  type of column.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TBCALC reads in the value of the <i>column</i> 
  from a set of  APPHOT/DAOPHOT ST tables databases, replaces it with a new
  value specified by the arithmetic expression <i>value</i>,
  and updates the ST tables databases(s).
  </p>
  <p>
  The expression <i>value</i> consists of variables which are column names
  in the APPHOT/DAOPHOT ST tables database.
  TBCALC uses the TABLES package task TCALC to actually perform the
  arithmetic operation.
  </p>
  <p>
  The supported
  arithmetic operators and functions are briefly described below.
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
  1. Change the XCENTER and YCENTER fields to XCENTER + 5.4 and YCENTER + 10.3
  respectively in a file produced by the daophot package allstar task.
  </p>
  <pre>
  	pt&gt; tbcalc m92.als.1 xcenter "xcenter+5.4"
  	pt&gt; tbcalc m92.als.1 ycenter "ycenter+10.3"
  </pre>
  <p>
  2.  Add a constant to the computed magnitudes produced by the daophot
  package nstar task.
  </p>
  <pre>
  	pt&gt; tbcalc n4147.nst.2 mag "mag+3.457"
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ptools.txcalc,tables.tcalc,ptools.pcalc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
