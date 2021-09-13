.. _pconvert:

pconvert — Convert a text database to a tables database
=======================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pconvert -- convert an APPHOT/DAOPHOT text database into an STSDAS table
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pconvert textfile table fields
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfile' Line='textfile'>
  <DD>The APPHOT/DAOPHOT text database which is to be converted into an
  APPHOT/DAOPHOT STSDAS table database.
  </DD>
  </DL>
  <DL>
  <DT><B>table</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table'>
  <DD>The name of the output STSDAS table database.
  </DD>
  </DL>
  <DL>
  <DT><B>fields = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields = "*"'>
  <DD>Template defining the fields to be selected from each record. By default
  all the fields are output. Fields
  are specified by using the names defined in the APPHOT/DAOPHOT text
  database by the
  #N entries. Upper or lower case and minimum match abbreviations are
  permissible. For those fields which have multiple entries such as 
  magnitude, an individual value can be referenced by specifying an array
  index, e.g. MAG[2] or several values can be selected by specifying a
  range of elements, e.g. MAG[1-4].
  </DD>
  </DL>
  <DL>
  <DT><B>expr = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr = yes'>
  <DD>The boolean expression, evaluated independently for each record,
  which serves as a selection criterion. By default all records are selected.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>If append is yes then the converted APPHOT/DAOPHOT text file is appended to an 
  existing output STSDAS table database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PCONVERT selects a subset of the fields from each record of an
  APPHOT/DAOPHOT text database and writes these into an STSDAS tabl database.
  The #K keyword parameters in the text database are
  stored as header parameters in the STSDAS table while the selected fields
  are stored in fields (columns) with the names specified by the text
  database #N keywords, units specified
  by the #U keywords, and print format specified by the #F keywords.
  <P>
  The output records are selected on the basis of the boolean
  expression <I>expr</I> whose variables are the field (column) names
  specified by the #N keywords in the APPHOT/DAOPHOT text database.
  If after substituting the values associated
  with a particular record into the field name variables the
  expression evaluates to yes, that record is included in the output table.
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
  character.  The meta-characters are described below. 
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
  <P>
  If the append parameter is "<TT>yes</TT>" then the converted input text database is
  appended to the specified output table. When appending to a table each of the
  output fields must already exist in the output table.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Convert the text output from the DAOPHOT PHOT task in the file n4147.mag.1
  to an STSDAS table, selecting only the fields ID, XCENTER, YCENTER,
  MAG,and MSKY ncessary for input to the DAOPHOT fitting routines.
  Put the output in an STSDAS table named n4147.tmag.1.
  <P>
  <PRE>
     pt&gt; pconvert n4147.mag.1 n4147.tmag.1 "ID,XCENTER,YCENTER,MAG,MSKY"
  </PRE>
  <P>
  If there were 4 magnitude fields in n4147.mag.1
  then there would be 4 columns in the output table with names of 
  MAG[1], MAG[2], MAG[3] and MAG[4]
  <P>
  <P>
  2. Convert the same file as in example 1. but append the output to
     n4147.tmag.1 and only select records with YCENTER &lt;= 200.0.
  <P>
  <PRE>
     pt&gt; pconvert n4147.mag.1 n4147.tmag.1 "ID,XCENTER,YCENTER,MAG,MSKY" \<BR>
         expr="YCENTER &lt; 200.0" append+
  <P>
  </PRE>
  <P>
  3. Convert all the records in the NSTAR text database n4147.nst.1 to
     an STSDAS table.
  <P>
     pt&gt; pconvert n4147.nst.1 n4147.tnst.1 "<TT>*</TT>"
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Changes in the values of the #K keyword quantities which are permitted by
  the APPHOT/DAOPHOT text database format will be lost in the conversion to
  STSDAS table format which does not permit such changes. For example users
  who have
  set up and run PHOT interactively and changed the values of the parameters
  after writing the first record to the text database will see only the initial
  values of the #K keywords in the STSDAS table headers after conversion.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.hedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
