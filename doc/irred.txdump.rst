.. _txdump:

txdump — Select fields from the center task output text file
============================================================

**Package: irred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  txdump - print fields from selected records in an APPHOT/DAOPHOT text database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  txdump textfiles fields expr
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles'>
  <DD>The APPHOT/DAOPHOT text database whose fields from selected records are to
  be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>fields</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields'>
  <DD>A template defining the fields to be printed from each selected record.
  The fields are specified by keywords defined in the text database output
  files #K and #N entries. Upper or lower case and minimum match
  abbreviations are permissible. Some fields such as "<TT>mag</TT>" may have
  multiple entries. An individual entry can be referenced by specifying an
  array index, e.g. "<TT>mag[2]</TT>" or several values can be selected by
  specifying a range of elements, e.g. "<TT>mag[1-3]</TT>". The fields are output in
  the order in which they are specified in the template.
  </DD>
  </DL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression to be evaluated once per record.
  Only the fields in those records for which the boolean expression
  evaluates to yes are printed.
  If <I>expr</I> = "<TT>yes</TT>", the specified fields in all the records are
  printed.
  </DD>
  </DL>
  <DL>
  <DT><B>headers = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='headers' Line='headers = no'>
  <DD>Preserve the APPHOT/DAOPHOT text database output format. The selected
  fields are printed on the standard output, preceded by parameters list,
  if <I>parameters</I> = yes, and the keyword, units,
  and format information, exactly as they appear in the text database.
  </DD>
  </DL>
  <DL>
  <DT><B>parameters = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters = yes'>
  <DD>Print the keyword parameters records in APPHOT/DAOPHOT format on the
  standard output if <I>headers</I> = yes.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>TXDUMP</I> selects a subset of fields specified by the <I>fields</I>
  parameter from an APPHOT/DAOPHOT text database or a list of databases by
  evaluating a boolean expression supplied by the user and prints the
  results on the standard output.
  If <I>headers</I> = no, the resultant output is in simple list format
  with all the specified fields in one line of text and adjacent fields
  separated by whitespace. The fields are printed in the order in
  which they appear in <I>expr</I>. If <I>headers</I> = yes, the
  selected fields are printed on the standard output, preceded by
  the parameter list, if <I>parameters</I> = yes, and the keyword, units,
  and format information, exactly as they appear in the text database.
  Newlines will not be inserted in the output so users should take
  care not to exceed the IRAF text file line limit of 161 characters.
  <P>
  The output records are selected on the basis of an input boolean
  expression <I>expr</I> whose variables are the field names
  specified by the #N keywords or the parameters specified by the
  #K keywords in the APPHOT/DAOPHOT text database.
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
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the fields XCENTER and YCENTER from the output of the APPHOT
  CENTER task.
  <P>
  <PRE>
  	pt&gt; txdump image.ctr.1 XCENTER,YCENTER yes
  </PRE>
  <P>
  2. Select the fields ID, XCENTER, YCENTER and the first three magnitudes
  MAG{1-3] from the output of the APPHOT PHOT task.
  <P>
  <PRE>
  	pt&gt; txdump image.mag.2 "ID,XCEN,YCEN,MAG[1-3]" yes
  </PRE>
  <P>
  3. Print all fields for all records in the above file with a magnitude
  through the first aperture of less than 20.0.
  <P>
  <PRE>
  	pt&gt; txdump image.mag.2 * "MAG[1] &lt; 20.0"
  </PRE>
  <P>
  4. Print the id and all magnitudes for which magnitudes 1 and 2 are &lt; 20.0
  from a file which is the output of the APPHOT PHOT task.
  <P>
  <PRE>
  	pt&gt; txdump image.mag.3 ID,MAG "MAG[1] &lt; 20.0 &amp;&amp; MAG[2] &lt; 20.0"
  </PRE>
  <P>
  5. Select the ID, XCENTER, YCENTER, MSKY and MAG fields from the output
     of the DAOPHOT NSTAR task for records where the magnitude is not
     INDEF, while preserving the format of the text database so it
     is suitable for input into a rerun of NSTAR.
  <P>
  <PRE>
  	pt&gt; txdump image.nst.1 "ID,XCENTER,YCENTER,MSKY,MAG"  \<BR>
  	    "MAG[1] != INDEF" headers+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  TXDUMP does not allow arrays in the expression field.
  <P>
  Users should not dump more fields than fill a 161 character textline
  as IRAF does not currently fully support longer text lines.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.hedit,ptools.tbdump,tables.tdump,ptools.pdump
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
