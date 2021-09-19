.. _afiltpars:

afiltpars: Default astrometry file filtering parameters
=======================================================

**Package: astcat**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  afiltpars -- edit the catalog filtering parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  afiltpars
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>fsort = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fsort' Line='fsort = ""' -->
  <dd>The field or field expression on which to sort the catalog / file records.
  The sort may be numeric or character. Sort fields may be expressed by name,
  e.g. <tt>"mag1"</tt> or field number, e.g. <tt>"f3"</tt>. Sort expressions must be a combination
  of existing fields, e. g. <tt>"mag2 - mag1"</tt> or <tt>"f4 - f3"</tt>. By default the records
  are not sorted.
  </dd>
  </dl>
  <dl>
  <dt><b>freverse = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='freverse' Line='freverse = no' -->
  <dd>Sort in descending order ?
  </dd>
  </dl>
  <dl>
  <dt><b>fexpr = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fexpr' Line='fexpr = yes' -->
  <dd>The boolean record selection expression. By default all catalog / file records
  are selected, otherwise only records matching the selection expression
  are selected. Selection expressions must be combination of existing fields
  and field expressions, e.g. <tt>"mag1 &lt; 16.0"</tt>, or <tt>"(f4 - f3) &lt; 1.5"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>fields = <tt>"f[*]"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fields' Line='fields = "f[*]"' -->
  <dd>The list of output fields and field expressions. By default the sorted and
  selected records are output as is. Output fields may be field names, e.g.
  <tt>"mag1"</tt>, field numbers e.g. <tt>"f3"</tt>, or field ranges e.g. <tt>"f[1-4]"</tt>. Output field
  expressions must be a combination of existing fields, e.g. <tt>"mag2 - mag1"</tt>,
  or <tt>"f4 - f3"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>fnames = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fnames' Line='fnames = ""' -->
  <dd>The list of new field names separated by commas. By default new fields, e.g.
  fields that are expressions of existing fields are assigned names of the form
  <tt>"f#"</tt> where # is the field sequence number. Field names must be valid tokens,
  i.e. they cannot be expressions or contain embedded blanks.
  </dd>
  </dl>
  <dl>
  <dt><b>fntypes = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fntypes' Line='fntypes = ""' -->
  <dd>The list of new field types separated by commas. By default new fields are
  assigned type real. Permitted field types are <tt>"s"</tt> for string, <tt>"i"</tt> for
  integer, <tt>"r"</tt> for real, or <tt>"d"</tt> for double.
  </dd>
  </dl>
  <dl>
  <dt><b>fnunits = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fnunits' Line='fnunits = ""' -->
  <dd>The list of new field units separated by commas. By default new fields are
  assigned units of INDEF. Units specifications may not contain embedded blanks.
  </dd>
  </dl>
  <dl>
  <dt><b>fnformats = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fnformats' Line='fnformats = ""' -->
  <dd>The list of new field formats. By default string, integer, and floating
  point fields are assigned formats of <tt>"%10s"</tt>, <tt>"%10d"</tt>, and <tt>"%10g"</tt> respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>fosystem = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fosystem' Line='fosystem = ""' -->
  <dd>The output celestial coordinate system. If fosystem is undefined
  it defaults to the catalog celestial coordinate system. Popular options
  are <tt>"icrs"</tt>, <tt>"j2000.0"</tt>, <tt>"b1950.0"</tt>. The full set of options can be examined
  by typing <tt>"help ccsystems"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>fira = <tt>"ra"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fira' Line='fira = "ra"' -->
  <dd>The name of the catalog field containing the right ascension / longitude
  of an object. Most users should leave fira set to <tt>"ra"</tt>. If the user knows
  the number of the right ascension / longitude field the generic field name
  <tt>"f#"</tt>, e.g. <tt>"f1"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>fidec = <tt>"dec"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fidec' Line='fidec = "dec"' -->
  <dd>The name of the catalog field containing the declination / latitude
  of an object. Most users should leave fidec set to <tt>"dec"</tt>. If the user knows
  the number of the declination / latitude field the generic field name <tt>"f#"</tt>,
  e.g. <tt>"f2"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>foraunits = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='foraunits' Line='foraunits = ""' -->
  <dd>The units of fira. Permitted values are <tt>"hours"</tt>, <tt>"degrees"</tt>, and <tt>"radians"</tt>. If
  foraunits is undefined it defaults to the preferred units of the
  output celestial coordinate system fosystem, e.g. hours for equatorial
  coordinate systems and degrees for ecliptic, galactic, and super-galactic
  coordinate systems.
  </dd>
  </dl>
  <dl>
  <dt><b>fodecunits = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fodecunits' Line='fodecunits = ""' -->
  <dd>The units of fidec. Permitted values are <tt>"degrees"</tt> and <tt>"radians"</tt>. If 
  fodecunits is undefined it defaults to the preferred units of the
  output celestial coordinate system fosystem, e.g. degrees for all systems.
  </dd>
  </dl>
  <dl>
  <dt><b>foraformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='foraformat' Line='foraformat = ""' -->
  <dd>The format of fira. If undefined foraformat defaults to the equivalent catalog
  format.
  </dd>
  </dl>
  <dl>
  <dt><b>fodecformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fodecformat' Line='fodecformat = ""' -->
  <dd>The format of fidec. If undefined fodecformat defaults to the equivalent
  catalog format.
  </dd>
  </dl>
  <dl>
  <dt><b>fixp = <tt>"xp"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fixp' Line='fixp = "xp"' -->
  <dd>The name of the catalog field containing the predicted x coordinate
  of an object. Most users should leave fixp set to <tt>"xp"</tt>. If the user knows
  the number of the predicted x coordinate field the generic field name
  <tt>"f#"</tt>, e.g. <tt>"f1"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>fiyp = <tt>"yp"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fiyp' Line='fiyp = "yp"' -->
  <dd>The name of the catalog field containing the predicted y coordinate
  of an object. Most users should leave fiyp set to <tt>"yp"</tt>. If the user knows
  the number of the predicted y coordinate field the generic field name
  <tt>"f#"</tt>, e.g. <tt>"f2"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>fixc = <tt>"xc"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fixc' Line='fixc = "xc"' -->
  <dd>The name of the catalog field containing the centered x coordinate
  of an object. Most users should leave fixc set to <tt>"xc"</tt>. If the user knows
  the number of the centered x coordinate field the generic field name
  <tt>"f#"</tt>, e.g. <tt>"f1"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>fiyc = <tt>"yc"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fiyc' Line='fiyc = "yc"' -->
  <dd>The name of the catalog field containing the centered y coordinate
  of an object. Most users should leave fiyc set to <tt>"yc"</tt>. If the user knows
  the number of the centered y coordinate field the generic field name
  <tt>"f#"</tt>, e.g. <tt>"f2"</tt> can be used.
  </dd>
  </dl>
  <dl>
  <dt><b>foxformat = <tt>"%10.3f"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='foxformat' Line='foxformat = "%10.3f"' -->
  <dd>The format of fixp and fixc. 
  </dd>
  </dl>
  <dl>
  <dt><b>foyformat = <tt>"%10.3f"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='foyformat' Line='foyformat = "%10.3f"' -->
  <dd>The format of fiyp and fiyc.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The catalog / file filtering parameters  are used to filter the results
  of a catalog query before writing the results to disk. Catalog / file filtering
  options include: sorting on a field or field expression,
  selecting and rejecting records by evaluating a boolean expression
  for each record, selecting a subset of the fields for output,
  transforming the coordinates from the catalog / file celestial coordinate
  system to a user specified celestial coordinate system, and computing new
  fields from existing fields.
  </p>
  <p>
  <i>fsort</i> and <i>freverse</i> define the sort field or field expression and
  the sort order. Sort fields may be field names or field numbers, e.g.
  <tt>"mag1"</tt> or <tt>"f3"</tt>. By default the sort order is ascending.
  </p>
  <p>
  Records are selected or rejected based on the value of the boolean expression
  <i>fexpr</i>. By default all catalog / file records are selected. The boolean 
  selection expression must be function of existing catalog fields, e.g.
  the expression <tt>"mag1 &lt;= 16.0"</tt> will select all records for which the mag1
  field is &lt;= 16.0, and the expression <tt>"(f4 - f3) &gt;= 0.0 &amp;&amp; (f4 - f3) &lt;= 1.0"</tt>
  will select all records for which the difference between fields 4 and 3
  is &gt;= 0.0 but &lt;= 1.0.
  </p>
  <p>
  The <i>fields</i> parameter defines the list output fields and field 
  expressions. By default all the
  input fields are output. By setting <i>fields</i> appropriately the user
  can select a subset of the input fields for output, rearrange the order
  of the input fields, and compute new fields. For example setting
  fields to <tt>"f[2-5]"</tt> selects fields 2 to 5 for output; setting fields
  to <tt>"f[2-3],f5,f4"</tt> select fields 2 to 5 but reverses the order of fields
  4 and 5; setting fields to <tt>"f[2-5],f5-f4"</tt> selects fields 2 to 5 and
  adds a new field which is the difference between fields 5 and 4.
  </p>
  <p>
  By default new fields are assigned names of the form <tt>"f#"</tt> where # is the field
  number, a data type of real, units of INDEF, and formats of %10s, %10d, or
  %10g if they are character, integer, or real respectively. Users can define
  names, data types, units, and formats for the new fields by  setting
  the <i>fnames</i>, <i>fntypes</i>, <i>fnunits</i>, and <i>fnformats</i>
  parameters.
  </p>
  <p>
  The coordinate system, units, or format of the output coordinates may
  be changed by setting one or more of the <i>fosystem</i>, <i>foraunits</i>,
  <i>fodecunits</i>, <i>foraformat</i>, <i>fodecformat</i>. By default the
  filtering code expects the input coordinates to be located in fields
  called <tt>"ra"</tt> and <tt>"dec"</tt>. If these fields do not have valid names then
  generic field names of the form <tt>"f#"</tt> can be substituted.
  </p>
  <p>
  The names and format of any newly computed pixel coordinate fields may
  be specified by setting one or more of the <i>fixp</i>, <i>fiyp</i>,
  <i>fixc</i>, <i>fiyc</i>, <i>foxformat</i>, or <i>foyformat</i> parameters.
  By default the filtering code expects the pixel coordinates to be located
  in fields called <tt>"xp"</tt>, <tt>"yp"</tt>, <tt>"xc"</tt>, and <tt>"yc"</tt>. If these fields do not have
  standard names then generic field names of the form <tt>"f#"</tt> can be substituted.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Expressions</h3>
  <!-- BeginSection: 'EXPRESSIONS' -->
  <p>
  The output records are selected on the basis of the input boolean
  expression <i>fexpr</i> whose variables are the field names specified
  in the configuration file or the generic equivalents f#.  If after
  substituting the values associated with a particular record into the
  field name variables the expression evaluates to yes, that record is
  included in the output catalog. Numeric expressions can also be used
  to define the sort expression <i>fsort</i> or to define new fields in
  <i>fields</i>.
  </p>
  <p>
  The supported operators and functions are briefly described below. A detailed
  description of the boolean expression evaluator and its syntax can be found
  in the manual page for the images package hedit task.
  </p>
  <p>
  The following logical operators can be used in the boolean expression. 
  </p>
  <pre>
          equal             ==    not equal               !=
          less than         &lt;     less than or equal      &lt;=
          greater than      &gt;     greater than or equal   &gt;=
          or                ||    and                     &amp;&amp;
          negation          !     pattern match           ?=
          concatenation     //
  </pre>
  <p>
  The pattern match character ?=  takes a
  string expression as its first argument and a pattern as its second argument.
  The result is yes if the pattern is contained in the string expression.
  Patterns are strings which may contain pattern matching meta-characters.
  The meta-characters themselves can be matched by preceding them with the escape
  character.  The meta-characters listed below. 
  </p>
  <pre>
          beginning of string     ^       end of string           $
          one character           ?       zero or more characters *
          white space             #       escape character        \<br>
          ignore case             {       end ignore case         }
          begin character class   [       end character class     ]
          not, in char class      ^       range, in char class    -
  </pre>
  <p>
  The expression may also include arithmetic operators and functions.
  The following arithmetic operators and functions are supported.
  </p>
  <pre>
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
  </pre>
  <!-- EndSection:   'EXPRESSIONS' -->
  <h3>Formats</h3>
  <!-- BeginSection: 'FORMATS' -->
  <p>
  A format  specification has the form <tt>"%w.dCn"</tt>, where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code <tt>"r"</tt> only.  The w and d fields are optional.  The  format
  codes C are as follows:
  </p>
  <pre>
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
  
  Conventions for w (field width) specification:
  
      W =  n      right justify in field of N characters, blank fill
  	-n      left justify in field of N characters, blank fill
  	0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
  
  Escape sequences (e.g. "\n" for newline):
  
  \b      backspace   (not implemented)
       formfeed
  \n      newline (crlf)
  \r      carriage return
  \t      tab
  \"      string delimiter character
  \'      character constant delimiter character
  \\      backslash character
  \nnn    octal value of character
  
  Examples
  
  %s          format a string using as much space as required
  %-10s       left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s        right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
  
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e      print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g      print a real number right justified in general format
  %-12.5g     same as above but left justified
  
  %h          format as nn:nn:nn.n
  %15h        right justify nn:nn:nn.n in field of 15 characters
  %-15h       left justify nn:nn:nn.n in a field of 15 characters
  %12.2h      right justify nn:nn:nn.nn
  %-12.2h     left justify nn:nn:nn.nn
  
  %H          / by 15 and format as nn:nn:nn.n
  %15H        / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H       / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H      / by 15 and right justify nn:nn:nn.nn
  %-12.2H     / by 15 and left justify nn:nn:nn.nn
  
  \n          insert a newline
  </pre>
  <!-- EndSection:   'FORMATS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the catalog / file filtering parameters.
  </p>
  <pre>
  cl&gt; lpar afiltpars
  </pre>
  <p>
  2. Edit the catalog / file filtering parameters.
  </p>
  <pre>
  cl&gt; afiltpars
  </pre>
  <p>
  3. Edit the catalog filtering parameters from the agetcat task.
  </p>
  <pre>
  cl&gt; epar agetcat
  </pre>
  <p>
  4. Save the current afiltpars parameter values in a text file called
  afilt1.par.  Use the saved parameter set in the next call to the agetcat 
  task.
  </p>
  <pre>
  cl&gt; epar afiltpars
  cl&gt; agetcat ... afiltpars=afilt1.par ...
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  agetcat, afiltcat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXPRESSIONS' 'FORMATS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
