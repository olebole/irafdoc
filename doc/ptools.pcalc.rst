pcalc — Do arithmetic on a list of apphot/daophot tables databases
==================================================================

**Package: ptools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pcalc (May93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pcalc (May93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pcalc</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pcalc - perform an arithmetic operation on a field in a list of apphot/daophot
  databases
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pcalc infiles field value
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_infiles">infiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles'>
  <DD>The APPHOT/DAOPHOT database(s) containing the field to be recomputed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_field">field </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='field' Line='field '>
  <DD>The field to be recomputed. Field must be an integer or real field
  in the input file(s).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_value">value</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>The arithmetic expression used to recompute the specified field.
  Value may be an integer or real expression but must match the data
  type of field. The functions real and int may be used to do type
  conversions.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PCALC reads in the values of the <I>field</I> keyword 
  from a set of  APPHOT/DAOPHOT databases, replaces the old values
  with new values equal to the value of the arithmetic expression <I>value</I>,
  and updates the databases(s).
  <P>
  PCALC is script task which calls TXCALC is the input file is an
  APPHOT/DAOPHOT text database or TBCLAC if APPHOT/DAOPHOT is a tables
  database.
  If the input file is a text database, the expression <I>value</I> consists
  of variables which are the field names
  specified by the #N keywords or the parameters specified by the
  #K keywords in the APPHOT/DAOPHOT text databases.
  Only keywords beginning with #N can actually be replaced.
  If the input file is an ST tables database, the expression <I>value</I>
  consists of the table column names.
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
  respectively in a file produced by the apphot package center task.
  <P>
  <PRE>
  	pt&gt; pcalc m92.ctr.1 xcenter "xcenter+5.4"
  	pt&gt; pcalc m92.ctr.1 ycenter "ycenter+10.3"
  </PRE>
  <P>
  2.  Add a constant to the computed magnitudes produced by nstar.
  <P>
  <PRE>
  	pt&gt; pcalc n4147.nst.2 mag "mag+3.457"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  TXCALC does not allow arrays in the expression field.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.tbcalc,tables.tcalc,ptools.pcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>