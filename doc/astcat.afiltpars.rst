afiltpars — Default astrometry file filtering parameters
========================================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>afiltpars (Mar00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>afiltpars (Mar00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>afiltpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  afiltpars -- edit the catalog filtering parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  afiltpars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_fsort">fsort = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fsort' Line='fsort = ""'>
  <DD>The field or field expression on which to sort the catalog / file records.
  The sort may be numeric or character. Sort fields may be expressed by name,
  e.g. "<TT>mag1</TT>" or field number, e.g. "<TT>f3</TT>". Sort expressions must be a combination
  of existing fields, e. g. "<TT>mag2 - mag1</TT>" or "<TT>f4 - f3</TT>". By default the records
  are not sorted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_freverse">freverse = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='freverse' Line='freverse = no'>
  <DD>Sort in descending order ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fexpr">fexpr = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fexpr' Line='fexpr = yes'>
  <DD>The boolean record selection expression. By default all catalog / file records
  are selected, otherwise only records matching the selection expression
  are selected. Selection expressions must be combination of existing fields
  and field expressions, e.g. "<TT>mag1 &lt; 16.0</TT>", or "<TT>(f4 - f3) &lt; 1.5</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fields">fields = "<TT>f[*]</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields = "f[*]"'>
  <DD>The list of output fields and field expressions. By default the sorted and
  selected records are output as is. Output fields may be field names, e.g.
  "<TT>mag1</TT>", field numbers e.g. "<TT>f3</TT>", or field ranges e.g. "<TT>f[1-4]</TT>". Output field
  expressions must be a combination of existing fields, e.g. "<TT>mag2 - mag1</TT>",
  or "<TT>f4 - f3</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fnames">fnames = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnames' Line='fnames = ""'>
  <DD>The list of new field names separated by commas. By default new fields, e.g.
  fields that are expressions of existing fields are assigned names of the form
  "<TT>f#</TT>" where # is the field sequence number. Field names must be valid tokens,
  i.e. they cannot be expressions or contain embedded blanks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fntypes">fntypes = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fntypes' Line='fntypes = ""'>
  <DD>The list of new field types separated by commas. By default new fields are
  assigned type real. Permitted field types are "<TT>s</TT>" for string, "<TT>i</TT>" for
  integer, "<TT>r</TT>" for real, or "<TT>d</TT>" for double"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fnunits">fnunits = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnunits' Line='fnunits = ""'>
  <DD>The list of new field units separated by commas. By default new fields are
  assigned units of INDEF. Units specifications may not contain embedded blanks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fnformats">fnformats = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnformats' Line='fnformats = ""'>
  <DD>The list of new field formats. By default string, integer, and floating
  point fields are assigned formats of </TT>"%10s"<TT>, </TT>"%10d"<TT>, and </TT>"%10g"<TT> respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fosystem">fosystem = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fosystem' Line='fosystem = ""'>
  <DD>The output celestial coordinate system. If fosystem is undefined
  it defaults to the catalog celestial coordinate system. Popular options
  are </TT>"icrs"<TT>, </TT>"j2000.0"<TT>, </TT>"b1950.0"<TT>. The full set of options can be examined
  by typing </TT>"help ccsystems"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fira">fira = </TT>"ra"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fira' Line='fira = "ra"'>
  <DD>The name of the catalog field containing the right ascension / longitude
  of an object. Most users should leave fira set to </TT>"ra"<TT>. If the user knows
  the number of the right ascension / longitude field the generic field name
  </TT>"f#"<TT>, e.g. </TT>"f1"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fidec">fidec = </TT>"dec"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fidec' Line='fidec = "dec"'>
  <DD>The name of the catalog field containing the declination / latitude
  of an object. Most users should leave fidec set to </TT>"dec"<TT>. If the user knows
  the number of the declination / latitude field the generic field name </TT>"f#"<TT>,
  e.g. </TT>"f2"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_foraunits">foraunits = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='foraunits' Line='foraunits = ""'>
  <DD>The units of fira. Permitted values are </TT>"hours"<TT>, </TT>"degrees"<TT>, and </TT>"radians"<TT>. If
  foraunits is undefined it defaults to the preferred units of the
  output celestial coordinate system fosystem, e.g. hours for equatorial
  coordinate systems and degrees for ecliptic, galactic, and super-galactic
  coordinate systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fodecunits">fodecunits = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fodecunits' Line='fodecunits = ""'>
  <DD>The units of fidec. Permitted values are </TT>"degrees"<TT> and </TT>"radians"<TT>. If 
  fodecunits is undefined it defaults to the preferred units of the
  output celestial coordinate system fosystem, e.g. degrees for all systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_foraformat">foraformat = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='foraformat' Line='foraformat = ""'>
  <DD>The format of fira. If undefined foraformat defaults to the equivalent catalog
  format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fodecformat">fodecformat = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fodecformat' Line='fodecformat = ""'>
  <DD>The format of fidec. If undefined fodecformat defaults to the equivalent
  catalog format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fixp">fixp = </TT>"xp"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixp' Line='fixp = "xp"'>
  <DD>The name of the catalog field containing the predicted x coordinate
  of an object. Most users should leave fixp set to </TT>"xp"<TT>. If the user knows
  the number of the predicted x coordinate field the generic field name
  </TT>"f#"<TT>, e.g. </TT>"f1"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fiyp">fiyp = </TT>"yp"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fiyp' Line='fiyp = "yp"'>
  <DD>The name of the catalog field containing the predicted y coordinate
  of an object. Most users should leave fiyp set to </TT>"yp"<TT>. If the user knows
  the number of the predicted y coordinate field the generic field name
  </TT>"f#"<TT>, e.g. </TT>"f2"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fixc">fixc = </TT>"xc"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixc' Line='fixc = "xc"'>
  <DD>The name of the catalog field containing the centered x coordinate
  of an object. Most users should leave fixc set to </TT>"xc"<TT>. If the user knows
  the number of the centered x coordinate field the generic field name
  </TT>"f#"<TT>, e.g. </TT>"f1"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fiyc">fiyc = </TT>"yc"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fiyc' Line='fiyc = "yc"'>
  <DD>The name of the catalog field containing the centered y coordinate
  of an object. Most users should leave fiyc set to </TT>"yc"<TT>. If the user knows
  the number of the centered y coordinate field the generic field name
  </TT>"f#"<TT>, e.g. </TT>"f2"<TT> can be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_foxformat">foxformat = </TT>"%10.3f"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='foxformat' Line='foxformat = "%10.3f"'>
  <DD>The format of fixp and fixc. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_foyformat">foyformat = </TT>"%10.3f"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='foyformat' Line='foyformat = "%10.3f"'>
  <DD>The format of fiyp and fiyc.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The catalog / file filtering parameters  are used to filter the results
  of a catalog query before writing the results to disk. Catalog / file filtering
  options include: sorting on a field or field expression,
  selecting and rejecting records by evaluating a boolean expression
  for each record, selecting a subset of the fields for output,
  transforming the coordinates from the catalog / file celestial coordinate
  system to a user specified celestial coordinate system, and computing new
  fields from existing fields.
  <P>
  <I>fsort</I> and <I>freverse</I> define the sort field or field expression and
  the sort order. Sort fields may be field names or field numbers, e.g.
  "<TT>mag1</TT>" or "<TT>f3</TT>". By default the sort order is ascending.
  <P>
  Records are selected or rejected based on the value of the boolean expression
  <I>fexpr</I>. By default all catalog / file records are selected. The boolean 
  selection expression must be function of existing catalog fields, e.g.
  the expression "<TT>mag1 &lt;= 16.0</TT>" will select all records for which the mag1
  field is &lt;= 16.0, and the expression "<TT>(f4 - f3) &gt;= 0.0 &amp;&amp; (f4 - f3) &lt;= 1.0</TT>"
  will select all records for which the difference between fields 4 and 3
  is &gt;= 0.0 but &lt;= 1.0.
  <P>
  The <I>fields</I> parameter defines the list output fields and field 
  expressions. By default all the
  input fields are output. By setting <I>fields</I> appropriately the user
  can select a subset of the input fields for output, rearrange the order
  of the input fields, and compute new fields. For example setting
  fields to "<TT>f[2-5]</TT>" selects fields 2 to 5 for output; setting fields
  to "<TT>f[2-3],f5,f4</TT>" select fields 2 to 5 but reverses the order of fields
  4 and 5; setting fields to "<TT>f[2-5],f5-f4</TT>" selects fields 2 to 5 and
  adds a new field which is the difference between fields 5 and 4.
  <P>
  By default new fields are assigned names of the form "<TT>f#</TT>" where # is the field
  number, a data type of real, units of INDEF, and formats of %10s, %10d, or
  %10g if they are character, integer, or real respectively. Users can define
  names, data types, units, and formats for the new fields by  setting
  the <I>fnames</I>, <I>fntypes</I>, <I>fnunits</I>, and <I>fnformats</I>
  parameters.
  <P>
  The coordinate system, units, or format of the output coordinates may
  be changed by setting one or more of the <I>fosystem</I>, <I>foraunits</I>,
  <I>fodecunits</I>, <I>foraformat</I>, <I>fodecformat</I>. By default the
  filtering code expects the input coordinates to be located in fields
  called "<TT>ra</TT>" and "<TT>dec</TT>". If these fields do not have valid names then
  generic field names of the form "<TT>f#</TT>" can be substituted.
  <P>
  The names and format of any newly computed pixel coordinate fields may
  be specified by setting one or more of the <I>fixp</I>, <I>fiyp</I>,
  <I>fixc</I>, <I>fiyc</I>, <I>foxformat</I>, or <I>foyformat</I> parameters.
  By default the filtering code expects the pixel coordinates to be located
  in fields called "<TT>xp</TT>", "<TT>yp</TT>", 'xc"<TT>, and </TT>"yc"<TT>. If these fields do not have
  standard names then generic field names of the form </TT>"f#"<TT> can be substituted.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_expressions">EXPRESSIONS</A></H2>
  <! BeginSection: 'EXPRESSIONS'>
  <UL>
  <P>
  The output records are selected on the basis of the input boolean
  expression <I>fexpr</I> whose variables are the field names specified
  in the configuration file or the generic equivalents f#.  If after
  substituting the values associated with a particular record into the
  field name variables the expression evaluates to yes, that record is
  included in the output catalog. Numeric expressions can also be used
  to define the sort expression <I>fsort</I> or to define new fields in
  <I>fields</I>.
  <P>
  The supported operators and functions are briefly described below. A detailed
  description of the boolean expression evaluator and its syntax can be found
  in the manual page for the images package hedit task.
  <P>
  The following logical operators can be used in the boolean expression. 
  <P>
  <PRE>
          equal             ==    not equal               !=
          less than         &lt;     less than or equal      &lt;=
          greater than      &gt;     greater than or equal   &gt;=
          or                ||    and                     &amp;&amp;
          negation          !     pattern match           ?=
          concatenation     //
  </PRE>
  <P>
  The pattern match character ?=  takes a
  string expression as its first argument and a pattern as its second argument.
  The result is yes if the pattern is contained in the string expression.
  Patterns are strings which may contain pattern matching meta-characters.
  The meta-characters themselves can be matched by preceding them with the escape
  character.  The meta-characters listed below. 
  <P>
  <PRE>
          beginning of string     ^       end of string           $
          one character           ?       zero or more characters *
          white space             #       escape character        \<BR>
          ignore case             {       end ignore case         }
          begin character class   [       end character class     ]
          not, in char class      ^       range, in char class    -
  </PRE>
  <P>
  The expression may also include arithmetic operators and functions.
  The following arithmetic operators and functions are supported.
  <P>
  <PRE>
  addition                +               subtraction             -
  multiplication          *               division                /
  negation                -               exponentiation          **
  absolute value          abs(x)          cosine                  cos(x)
  sine                    sin(x)          tangent                 tan(x)
  arc cosine              acos(x)         arc sine                asin(x)
  arc tangent             atan(x)         arc tangent             atan2(x,y)
  exponential             exp(x)          square root             sqrt(x)
  natural log             log(x)          common log              log10(x)
  minimum                 min(x,y)        maximum                 max(x,y)
  convert to integer      int(x)          convert to real         real(x)
  nearest integer         nint(x)         modulo                  mod(x)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXPRESSIONS'>
  <H2><A NAME="s_formats">FORMATS</A></H2>
  <! BeginSection: 'FORMATS'>
  <UL>
  <P>
  A format  specification has the form "<TT>%w.dCn</TT>", where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code "<TT>r</TT>" only.  The w and d fields are optional.  The  format
  codes C are as follows:
  <P>
  <PRE>
  b       boolean (YES or NO)
  c       single character (c or '\c' or '\0nnn')
  d       decimal integer
  e       exponential format (D specifies the precision)
  f       fixed format (D specifies the number of decimal places)
  g       general format (D specifies the precision)
  h       hms format (hh:mm:ss.ss, D = no. decimal places)
  m       minutes, seconds (or hours, minutes) (mm:ss.ss)
  o       octal integer
  rN      convert integer in any radix N
  s       string (D field specifies max chars to print)
  t       advance To column given as field W
  u       unsigned decimal integer
  w       output the number of spaces given by field W
  x       hexadecimal integer
  z       complex format (r,r) (D = precision)
  <P>
  Conventions for w (field width) specification:
  <P>
      W =  n      right justify in field of N characters, blank fill
  	-n      left justify in field of N characters, blank fill
  	0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
  <P>
  Escape sequences (e.g. "\n" for newline):
  <P>
  \b      backspace   (not implemented)
       formfeed
  \n      newline (crlf)
  \r      carriage return
  \t      tab
  \"      string delimiter character
  \'      character constant delimiter character
  \\      backslash character
  \nnn    octal value of character
  <P>
  Examples
  <P>
  %s          format a string using as much space as required
  %-10s       left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s        right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
  <P>
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e      print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g      print a real number right justified in general format
  %-12.5g     same as above but left justified
  <P>
  %h          format as nn:nn:nn.n
  %15h        right justify nn:nn:nn.n in field of 15 characters
  %-15h       left justify nn:nn:nn.n in a field of 15 characters
  %12.2h      right justify nn:nn:nn.nn
  %-12.2h     left justify nn:nn:nn.nn
  <P>
  %H          / by 15 and format as nn:nn:nn.n
  %15H        / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H       / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H      / by 15 and right justify nn:nn:nn.nn
  %-12.2H     / by 15 and left justify nn:nn:nn.nn
  <P>
  \n          insert a newline
  </PRE>
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the catalog / file filtering parameters.
  <P>
  <PRE>
  cl&gt; lpar afiltpars
  </PRE>
  <P>
  2. Edit the catalog / file filtering parameters.
  <P>
  <PRE>
  cl&gt; afiltpars
  </PRE>
  <P>
  3. Edit the catalog filtering parameters from the agetcat task.
  <P>
  <PRE>
  cl&gt; epar agetcat
  </PRE>
  <P>
  4. Save the current afiltpars parameter values in a text file called
  afilt1.par.  Use the saved parameter set in the next call to the agetcat 
  task.
  <P>
  <PRE>
  cl&gt; epar afiltpars
  cl&gt; agetcat ... afiltpars=afilt1.par ...
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  agetcat, afiltcat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXPRESSIONS' 'FORMATS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>