tbcalc — Do arithmetic on a list of apphot/daophot tables databases
===================================================================

**Package: ptools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tbcalc (May93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tbcalc (May93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tbcalc</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tbcalc - perform an arithmetic operation on a column in a list of apphot/daophot
  	 ST tables databases
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tbcalc textfiles column value
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_textfiles">textfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles'>
  <DD>The APPHOT/DAOPHOT ST tables database(s) containing the column to be recomputed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column'>
  <DD>The column to be recomputed. Column must be an integer or real column
  in the input file(s).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_value">value</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>The arithmetic expression used to recompute the specified column.
  Value may be an integer or real expression but must match the data
  type of column.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  TBCALC reads in the value of the <I>column</I> 
  from a set of  APPHOT/DAOPHOT ST tables databases, replaces it with a new
  value specified by the arithmetic expression <I>value</I>,
  and updates the ST tables databases(s).
  <P>
  The expression <I>value</I> consists of variables which are column names
  in the APPHOT/DAOPHOT ST tables database.
  TBCALC uses the TABLES package task TCALC to actually perform the
  arithmetic operation.
  <P>
  The supported
  arithmetic operators and functions are briefly described below.
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Change the XCENTER and YCENTER fields to XCENTER + 5.4 and YCENTER + 10.3
  respectively in a file produced by the daophot package allstar task.
  <P>
  <PRE>
  	pt&gt; tbcalc m92.als.1 xcenter "xcenter+5.4"
  	pt&gt; tbcalc m92.als.1 ycenter "ycenter+10.3"
  </PRE>
  <P>
  2.  Add a constant to the computed magnitudes produced by the daophot
  package nstar task.
  <P>
  <PRE>
  	pt&gt; tbcalc n4147.nst.2 mag "mag+3.457"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txcalc,tables.tcalc,ptools.pcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>