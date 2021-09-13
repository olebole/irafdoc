pdump — Print selected fields from a list of apphot databases
=============================================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pdump (Feb93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pdump (Feb93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pdump</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pdump - print fields from an APPHOT/DAOPHOT database
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pdump infiles fields expr
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_infiles">infiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles'>
  <DD>The APPHOT/DAOPHOT databases containing the fields to be dumped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fields">fields</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields'>
  <DD>A template defining the fields to be dumped from each record.
  In the case of APPHOT/DAOPHOT text databases, the fields are specified by
  keywords defined by the
  #K and #N entries in the database. Upper or lower case and minimum match
  abbreviations are permissible. Some fields such as "<TT>mag</TT>" may have
  multiple entries. An individual entry can be referenced by specifying an
  array index, e.g. "<TT>MAG[2]</TT>" or several values can be selected by
  specifying a range of elements, e.g. "<TT>MAG[1-3]</TT>".
  In the case of STSDAS table APPHOT/DAOPHOT databases the fields are the
  column names. Names must be spelled in full but upper or lower case is allowed.
  In the case of STSDAS table databases, it may be necessary to escape the
  leading square bracket so that field "<TT>MAG[2]</TT>" would be referred to as
  "<TT>MAG\[2]</TT>".  The fields are output in
  the order in which they are specified in the template.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expr">expr</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression to be evaluated once per record.
  Only the fields in those records for which the boolean expression
  evaluates to yes are printed.
  If <I>expr</I> = "<TT>yes</TT>", the specified fields in all the records are
  printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_headers">headers = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='headers' Line='headers = no'>
  <DD>Dump the APPHOT/DAOPHOT database field headers. The selected
  fields are printed on the standard output, preceded by the parameters list,
  if <I>parameters</I> = yes, and the keyword, units,
  and format information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_parameters">parameters = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters = yes'>
  <DD>Print the keyword parameters records on the
  standard output if <I>headers</I> = yes.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PDUMP selects a subset of fields specified by the <I>fields</I>
  parameter from an APPHOT/DAOPHOT database or a list of databases
  and prints the results on the standard output.
  If <I>headers</I> = no, the output is in simple list format
  with adjacent fields
  separated by whitespace. The fields are printed in the order in
  which they appear in <I>ields</I>. If <I>headers</I> = yes, the
  selected fields are printed on the standard output, preceded by
  the parameter list, if <I>parameters</I> = yes, and the keyword, units,
  and format information.
  Newlines will not be inserted in the output if the input database
  was an APPHOT/DAOPHOT text file, so users should take
  care not specify so many output fields as to exceed the IRAF text file
  line limit of 161 characters.
  Newlines will be inserted if the original database was an
  STSDAS table.
  <P>
  PDUMP is a simple CL script which calls TXDUMP if the APPHOT/DAOPHOT
  database was a text file and TBDUMP if it was an STSDAS table.
  Although the parameters of TBDUMP and TXDUMP have been tailored to
  make the two tasks appear as similar as possible each task
  offers some capabilities that the other does not. In some
  situations users may wish to use the individual tasks instead of the
  generic script.
  <P>
  The output records are selected on the basis of an input boolean
  expression <I>expr</I> whose variables are the field names
  specified by the #N keywords or the parameters specified by the
  #K keywords in the APPHOT/DAOPHOT text database or the column names
  in an ST tables database.
  If after substituting the values associated
  with a particular record into the field name variables the
  expression evaluates
  to yes, that record is included in the output table.
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Select the fields XCENTER and YCENTER from the output of the APPHOT
  CENTER task.
  <P>
  <PRE>
      pt&gt; pdump image.ctr.3 "XCENTER,YCENTER" yes
  </PRE>
  <P>
  2. Select the fields XCENTER and YCENTER from the output of the APPHOT
  CENTER task for all records with YCENTER &gt; 100.0.
  <P>
  <PRE>
      pt&gt; pdump image.ctr.3 "XCENTER,YCENTER" "YCENTER &gt; 100.0"
  </PRE>
  <P>
  3. Select the fields ID, XCENTER, YCENTER and the first three magnitudes
  from the output of the APPHOT PHOT task. In the case of STSDAS table
  databases it may be necessary to escape the leading square bracket.
  <P>
  <PRE>
      pt&gt; pdump image.mag.3 "ID,XCEN,YCEN,MAG[1],MAG[2],MAG[3]" yes
  <P>
  		   or
  <P>
      pt&gt; pdump image.mag.3 "ID,XCEN,YCEN,MAG\[1],MAG\[2],MAG\[3]" yes
  </PRE>
  <P>
  <P>
  4. Select the ID, XCENTER, YCENTER, MSKY and MAG fields from the output
  of the DAOPHOT NSTAR task. Print the headers and parameters as well.
  <P>
  <PRE>
      pt&gt; pdump image.nst.3 "ID,XCENTER,YCENTER,MSKY,MAG"  \<BR>
  	yes headers+ parameters+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Users should not dump more fields than fill a 161 character textline
  as IRAF does not currently fully support longer text lines.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txdump,ptools.tbdump,tables.tdump
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>