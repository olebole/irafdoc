asthedit — Astronomical header editor
=====================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>asthedit (Jan96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>asthedit (Jan96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>asthedit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  asthedit -- astronomical header editor
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  asthedit images commands
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be used.  The image header keywords are used in this task
  as variables which are read, modified, created, or deleted.  If the images
  do not have write permission or the <I>update</I> parameter is "<TT>no</TT>" then the
  image headers will not be modified.  If no images are specified then this
  task can be used as a calculator (though see <B>astcalc</B>).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_commands">commands</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='commands' Line='commands'>
  <DD>A file of commands using the simple syntax given in the DESCRIPTION.  If no
  file name is given then the commands are read interactively from the
  standard input with a prompt given by the <I>prompt</I> parameter.  The
  command input ends with either EOF or "<TT>quit</TT>".  If a list of images and/or a
  table is specified the commands are repeated for each image or until the
  end of the table is reached.  Comments beginning with <TT>'#'</TT>, blank lines, and
  escaped newlines are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_table">table = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table = ""'>
  <DD>Optional text file containing columns of values.  The table consists of
  one or more lines of whitespace separated columns of values.  Note that a
  string with whitespace needs to be quoted.  One line of the table is
  scanned for each image.  There must be at lest as many fields as are
  defined by the column names.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_colnames">colnames = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colnames' Line='colnames = ""'>
  <DD>List of whitespace separated column names.  These are the names referenced
  in the command file by $&lt;name&gt;.  The leading <TT>'$'</TT> is not included in the
  column name specification.  There may be fewer columns than the number of
  columns in the table.  Dummy names must be used if some columns occur
  before a column to be referenced.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_prompt">prompt = "<TT>asthedit&gt; </TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='prompt' Line='prompt = "asthedit&gt; "'>
  <DD>When no command file is specified the input commands are read from the
  standard input (the terminal) and the value of the <I>prompt</I> string is
  printed as a prompt.  Note that if the input command file is specified as
  "<TT>STDIN</TT>" there will be no prompt even though commands will also be read from
  the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the image headers?  If no then any new, modified, or deleted
  keywords will not be recorded in the image headers.  This allows using the
  task only for computing and printing quantities.  Also this allows
  accessing read-only images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print each keyword added or modified?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_oldstyle">oldstyle = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldstyle' Line='oldstyle = no'>
  <DD>Use the old style syntax of this task from versions prior to V2.11.  This
  parameter allows backward compatibility for command files previously
  developed.  Some aspects of the new syntax are still available.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Asthedit</B> evaluates expressions using image header keywords, column
  names from a text table, CL parameters, internal variables, constants, and
  functions to create or modify image header keywords.  This task is
  particularly useful for adding keywords from a table and deriving keywords
  used by IRAF tasks which are not present in the images.  It differs from
  <B>hedit</B> in that it includes astronomical functions, operates from a
  command file which may perform many edits, and references columns from a
  text table.  The command file may be omitted in which case commands may be
  entered interactively for the first image and then the same commands will
  be repeated for any subsequent images.
  <P>
  This task may be used interactively or with input from a command file
  (<I>commands</I>).  If no command file is specified a prompt (<I>prompt</I>)
  is printed and commands are entered interactively.  The input is terminated
  with either the end-of-file character (EOF) or the command "<TT>quit</TT>".  Input
  command files simply contain the same input in a file and end with the end
  of the file or "<TT>quit</TT>".  The input commands, either those entered
  interactively or from a file, are repeated for each image in the image list
  and until the end of the input text table is reached, whichever comes
  first.  Generally this task is used on one or more images but if no
  image is specified the commands are executed just once and task behaves
  like an calculator.
  <P>
  The command input consists of statements with each statement on a
  line by itself.  However long statements may be broken up with
  escaped newlines using the back-slash as the escape character;
  i.e. \&lt;newline&gt;.  Comments beginning with <TT>'#'</TT>, blank lines,
  and whitespace are ignored.
  <P>
  There are three types of statements: assignment, expressions, and
  conditional.  Each statement is on a line by itself though long statements
  may be broken up with escaped newlines (\&lt;newline&gt;).  Assignment statements
  have an image header keyword name (or variable name beginning with $), an
  equal sign (but see the <I>oldstyle</I> parameter), and an expression.
  Expression statements consist of only the expression with the value of the
  expression being ignored.  Expression statements are generally used with
  certain functions.  Conditional statements are blocks of if-endif and
  if-else-endif with assignment and expression statements between the
  if-else-endif statements.  These may not be nested.
  <P>
  In earlier versions of this task there were only assignment statements
  and these did not use an equal sign; i.e. all statements consisted
  of an image header keyword and an expression separated by whitespace
  except that a keyword name by itself indicates deletion of a keyword.
  In order to interpret old command files the <I>oldstyle</I> parameter
  may be set to yes.  This will insert an equal sign internally.  It
  also only allows a subset of statements to not begin with a keyword
  or variable.  These are if, else, endif, print, printf, and quit.
  Note that with the old style syntax one may still include an equal
  sign.  It is recommended that the old style syntax not be used because
  of the greater flexibility in the new syntax.
  <P>
  An image header keyword name is an arbitrary identifier which must begin
  with an alphabetic character or <TT>'$'</TT> followed by an alphabetic character and
  may use alphabetic characters, digits, or the characters <TT>'_'</TT>, <TT>'$'</TT>, or <TT>'.'</TT>.
  Keyword names are case insensitive.  Because some additional characters are
  allowed in the FITS definition of keyword names, such names may be
  referenced with the special <TT>'@'</TT> operator described below.
  <P>
  One may also use internal variables which have the same identifier rules
  but begin with <TT>'$'</TT>.  Note that these variables are case sensitive (as are
  function names).  There are a few special predefined variables: "<TT>$I</TT>"
  contains the current image name, "<TT>$D</TT>" contains the current local date (in
  old FITS DD/MM/YY format), "<TT>$T</TT>" contains the current local time, "<TT>$GMD</TT>"
  contains the current Greenwich meridian date (in FITS YYYY-MM-DD format),
  "<TT>$GMT</TT>" contains the current Greenwich meridian time, and "<TT>$GMDT</TT>" contains
  the current date and time in FITS YYYY-MM-DDTHH:MM:SS format.
  <P>
  Before the commands are interpreted for each image a line of a text
  file may be read.  This occurs when a file is specified by the
  <I>table</I> parameter.  The line is scanned and the values of each
  column are stored in the variable names specified by the <I>colnames</I>
  parameter.  The values may be referenced in expressions by the
  specified column name preceded with <TT>'$'</TT>.  Note that additional lines
  may be scanned with the "<TT>fscan</TT>" function.  The user is then responsible
  for the table containing the correct sequence of lines when there
  are multiple images.
  <P>
  In <B>asthedit</B> identifiers are image header keywords and lines
  for the table file are read automatically.  A related task is <B>astcalc</B>.
  In this task all variables are maintained internally and input and output
  are performed explicitly by functions.  There are functions to read,
  write, and delete image header keywords from a list of images.
  <P>
  STATEMENTS
  <P>
  The following gives a more formal description of the statement syntax
  and the special words "<TT>if</TT>", "<TT>else</TT>", "<TT>endif</TT>", and "<TT>quit</TT>".
  <P>
  <PRE>
  	&lt;keyword&gt;
          &lt;keyword&gt; = &lt;expression&gt;
  	$&lt;variable&gt; = &lt;expression&gt; 
          &lt;expression&gt;
          if (&lt;expression&gt;)
              &lt;statements&gt;
          endif
          if (&lt;expression&gt;)
              &lt;statements&gt;
          else
              &lt;statements&gt;
          endif
          quit
  </PRE>
  <P>
  The result of the expression in the "<TT>if</TT>" statement is normally a logical
  value.  However, a numeric value of 0 is false while any other value is
  true and any string beginning with either "<TT>y</TT>" or "<TT>Y</TT>" is true with
  any other value being false; i.e. string values of yes and no may be used.
  <P>
  The old style syntax allows the following statements.
  <P>
  <PRE>
  	&lt;keyword&gt;
          &lt;keyword&gt;     &lt;expression&gt;
  	$&lt;variable&gt;   &lt;expression&gt; 
          &lt;keyword&gt; = &lt;expression&gt;
  	$&lt;variable&gt; = &lt;expression&gt; 
          print (...)
          printf (...)
          if (&lt;expression&gt;)
              &lt;statements&gt;
          endif
          if (&lt;expression&gt;)
              &lt;statements&gt;
          else
              &lt;statements&gt;
          endif
          quit
  </PRE>
  <P>
  Old style command files would only use the first two statements.
  <P>
  KEYWORD NAMES AND VARIABLES
  <P>
  Keyword names and variables may formally be defined as:
  <P>
  <PRE>
          [$]{a-zA-Z}[{a-zA-Z0-9._$}]*
  </PRE>
  <P>
  where [] indicate optional, {} indicates a class, - indicates an ASCII
  range of characters, and * indicates zero or more occurrences.  In words, a
  keyword must begin with an alphabetic character, a variable or text file
  column name begins with <TT>'$'</TT> and an alphabetic character, and both may be
  followed by any combinations of alphabetic, digit, or <TT>'.'</TT>, <TT>'_'</TT>, and <TT>'$'</TT>
  characters.
  <P>
  There are a few predefined variables which may be referenced in
  expressions.
  <P>
  <PRE>
          $I      The name of the current image (if used)
          $D      The current date in the DD/MM/YY format
          $T      The current (local) time as a sexagesimal string
  </PRE>
  <P>
  The date and time are set once at the beginning of execution.
  <P>
  Though not recommended it is possible to use any set of characters
  for a variable provided the variable is referenced as @"<TT>&lt;name&gt;</TT>".
  For example one could use @"<TT>date-obs</TT>" to include the character <TT>'-'</TT>.
  This option is primarily used for FITS keywords that use <TT>'-'</TT> as
  a hyphen character and must be escaped from interpretation as the
  an arithmetic subtraction operator.
  <P>
  EXPRESSIONS
  <P>
  Expressions consist of operands and operators.  The operands may be any
  image header keyword, previously defined variable, column name, quoted
  string constants, numeric constants, and functions.  Values given as
  sexagesimal strings are automatically converted to decimal numbers.  The
  operators are arithmetic, logical, and string.  The expression syntax is
  equivalent to that used in the CL and SPP languages.
  <P>
  Additional information may be found in the help for <B>hedit</B> except that
  all unquoted nonnumeric strings are considered to be keywords or variables
   and so the <TT>'('</TT>, <TT>')'</TT> operators are not used.  The "<TT>field</TT>" references are
  not needed so the references "<TT>.</TT>" and  "<TT>$</TT>" are not used and are not legal
  variable names in this task.
  <P>
  operators:
  <P>
  The following operators are recognized in expressions.  With the exception
  of the operators "<TT>?</TT>", "<TT>?=</TT>", and "<TT>@</TT>", the operator set is equivalent to that
  available in the CL and SPP languages.
  <P>
  <P>
  <PRE>
          +  -  *  /              arithmetic operators
          **                      exponentiation
          //                      string concatenation
          !  -                    boolean not, unary negation
          &lt;  &lt;= &gt;  &gt;=             order comparison (works for strings)
          == != &amp;&amp; ||             equals, not equals, and, or
          ?=                      string equals pattern
          ? :                     conditional expression
          @                       reference a variable
  </PRE>
  <P>
  <P>
  The operators "<TT>==</TT>", "<TT>&amp;&amp;</TT>", and "<TT>||</TT>" may be abbreviated as "<TT>=</TT>", "<TT>&amp;</TT>", and "<TT>|</TT>"
  if desired.  The ?= operator performs pattern matching upon strings.
  The @ operator is required to reference keywords with
  one of the operator characters.  This is most like to be used as:
  <P>
          @"<TT>date-obs</TT>"
  <P>
  A point to be aware of is that in the ?: conditional expression both
  possible result values are evaluated though the result of the expression
  is only one of them.  This means that one should not use this to
  call I/O functions that one wants to be executed only if a certain
  condition holds.
  <P>
  intrinsic functions:
  <P>
  A number of standard intrinsic functions are recognized within expressions.
  The set of functions currently supported is shown below.
  <P>
  <P>
  <PRE>
  	abs     atan2   deg     log     min     real    sqrt
  	acos    bool    double  log10   mod     short   str
  	asin    cos     exp     long    nint    sin     tan
  	atan    cosh    int     max     rad     sinh    tanh
  </PRE>
  <P>
  <P>
  The trigonometric functions operate in units of radians.
  The <I>min</I> and <I>max</I> functions may have any number of arguments up
  to a maximum of sixteen or so (configurable).  The arguments need not all
  be of the same datatype.
  <P>
  A function call may take either of the following forms:
  <P>
  <PRE>
          &lt;identifier&gt; <TT>'('</TT> arglist <TT>')'</TT>
  or
          &lt;string_expr&gt; <TT>'('</TT> arglist <TT>')'</TT>
  </PRE>
  <P>
  The first form is the conventional form found in all programming languages.
  The second permits the generation of function names by string valued
  expressions and might be useful on rare occasions.
  <P>
  special functions:
  <P>
  In addition to the above intrinsic functions there are a number of
  astronomical functions. More will be added in time.  These are:
  <P>
  <PRE>
       sexstr - convert a number to a sexagesimal string (xx:mm:ss.ss)
        epoch - compute an epoch given a date and time
       julday - compute a Julian day given a date and time
          mst - compute a mean sidereal time given a date, time, and longitude
   ra_precess - precess ra from one epoch to another
  dec_precess - precess dec from one epoch to another
      airmass - compute airmass given ra, dec, sidereal time, and latitude
     eairmass - compute effective airmass given
  		ra, dec, sidereal time, exposure time, and latitude
        obsdb - get parameters from the observatory database
  </PRE>
  <P>
  <DL>
  <DT><B><A NAME="l_sexstr">sexstr (number), sexstr (number, digits)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='sexstr' Line='sexstr (number), sexstr (number, digits)'>
  <DD>Convert a number to a sexagesimal string in the format X:MM:SS.SS.  There
  is an optional second argument (the default is 0) which is the number of
  decimal digits in the seconds field.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epoch">epoch (date[, ut])</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='epoch' Line='epoch (date[, ut])'>
  <DD>Compute an epoch given a date and time.  The date is a string in the
  format DD/MM/YY, YYYY-MM-DD, or YYYY-MM-DDTHH:MM:SS.
  Typically this argument will be the standard FITS
  keyword DATE-OBS.  Because of possible confusion of the hyphen with
  subtraction this keyword would be specified as @"<TT>date-obs</TT>".  The time
  argument is optional.  If it is not given the time from the date
  string will be used and if absent a time of 0h is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_julday">julday (date[, ut])</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='julday' Line='julday (date[, ut])'>
  <DD>Compute a Julian day given a date and time.  The date and time are
  specified as described previously.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mst">mst (date[, ut], longitude)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='mst' Line='mst (date[, ut], longitude)'>
  <DD>Compute a mean sidereal time given a date, time, and longitude in degrees.  The
  date and (optional) time are specified as described previously.  The longitude
  may be given as a constant or using the observatory database function
  as shown in the examples.  The returned value is a sexagesimal
  string with two decimals in the seconds.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_precess">precess (ra, dec, epoch1, epoch2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='precess' Line='precess (ra, dec, epoch1, epoch2)'>
  <DD>Precess coordinates from one epoch to another.  The ra is the
  right ascension in hours, the dec in the declination in degrees,
  and the epochs are in years.  This function returns a formatted string with
  the precessed right ascension, declination, and epoch.  Numerical
  values for the right ascension and declination are obtained with the
  functions ra_precess and dec_precess.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra_precess">ra_precess (ra, dec, epoch1, epoch2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='ra_precess' Line='ra_precess (ra, dec, epoch1, epoch2)'>
  <DD>Precess a right ascension from one epoch to another.  The ra is the
  input right ascension in hours, the dec is the declination in degrees,
  and the epochs are in years.  Because a function can return only one
  value there is a second function to return the precessed declination.
  The returned value is a sexagesimal string with two decimals in the seconds.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec_precess">dec_precess (ra1, dec1, epoch1, epoch2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='dec_precess' Line='dec_precess (ra1, dec1, epoch1, epoch2)'>
  <DD>Precess a declination from one epoch to another.  The ra is the
  input right ascension in hours, the dec is the declination in degrees,
  and the epochs are in years.  Because a function can return only one
  value there is a second function to return the precessed right ascension.
  The returned value is a sexagesimal string with two decimals in the seconds.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_arcsep">arcsep (ra1, dec1, ra2, dec2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='arcsep' Line='arcsep (ra1, dec1, ra2, dec2)'>
  <DD>Compute the separation between two spherical coordinates.  The parameters
  ra1 and ra2 are coordinates in hours (right ascension, longitude, etc.)
  and the dec1 and dec2 parameters are coordinates in degrees (declination,
  latitude, etc.).  The computed value is returned in seconds of arc.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass (ra, dec, st, latitude)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='airmass' Line='airmass (ra, dec, st, latitude)'>
  <DD>Compute an airmass given right ascension in hours, declination in
  degrees, sidereal time in hours, and latitude in degrees.  The latitude
  is often specified using the observatory database function as shown
  in the examples.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_eairmass">eairmass (ra, dec, st, exptime, latitude)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='eairmass' Line='eairmass (ra, dec, st, exptime, latitude)'>
  <DD>Compute an "<TT>effective</TT>" airmass given right ascension in hours, declination
  in degrees, beginning sidereal time in hours, exposure time in seconds, and
  latitude in degrees.  The The latitude is often specified using the
  observatory database function as shown in the examples.  The effective
  airmass is based on a Simpson's rule weighting of the beginning, middle,
  and ending airmass (with no provision for paused exposure).  The weights
  are:
  <P>
  <PRE>
      effective = beginning + 4 * middle + ending
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obsdb">obsdb (observatory, parameter)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='obsdb' Line='obsdb (observatory, parameter)'>
  <DD>Return a value from the observatory database.  The observatory parameter is
  a observatory identification string as defined in the database.  Often this
  is the value stored in the OBSERVAT keyword.  Another special value is
  "<TT>observatory</TT>" which then follows a name resolution scheme.  The observatory
  database mechanism is described by the help topic <B>observatory</B>.  The
  parameter is a string given the quantity desired.  Typically this would be
  "<TT>longitude</TT>" or "<TT>latitude</TT>" but there are other possible parameters.
  </DD>
  </DL>
  <P>
  input/output functions:
  <P>
  There are special functions for formatting, printing, error aborts,
  reading, writing, and deleting image header keywords, reading a text file,
  and reading and writing CL parameters.  Note that in <B>asthedit</B>
  one would not normally use the image input/output functions or
  the text file scanning function since any keyword reference reads or
  writes to the image header and one line of the text file is scanned
  automatically for each image.
  <P>
  <PRE>
       print  - print a set of arguments with default format
       printf - print a set arguments with specified format
       format - format a string
       error  - print an error message and abort
       clget  - get a value from a CL parameter
       clput  - put a value to a CL parameter
       scan   - scan a string and parse into keywords or variables
       fscan  - scan a line of a text file
       imget  - get the value of an image header keyword
       imput  - put (add or modify) the value of an image header keyword
       imdel  - delete an image header keyword
  </PRE>
  <P>
  <DL>
  <DT><B><A NAME="l_print">print ([argument, ...])</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='print' Line='print ([argument, ...])'>
  <DD>Print the arguments with default formats based on the type of value ending
  with a newline.  There may be zero or more arguments.  With zero arguments
  only a newline will be printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_printf">printf (fmt [, argument, ...])</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='printf' Line='printf (fmt [, argument, ...])'>
  <DD>Print a list of arguments using the formatting syntax described later.
  Parameters to be formatted are given by the % fields and the values are
  passed as further arguments in the order in which they are referenced.
  There is no automatic newline so the format must include "<TT>\n</TT>" to
  produce newlines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_error">error (message)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='error' Line='error (message)'>
  <DD>Print the "<TT>message</TT>", which can be any string variable such as might
  be produced by "<TT>format</TT>", and abort the task.  This is useful in
  conjunction with the conditional operator to abort if a variable
  takes an inappropriate value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clget">clget (parameter)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='clget' Line='clget (parameter)'>
  <DD>Get the value of a CL parameter.  The argument must be a string.  The
  function value is the value of the parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clput">clput (parameter, value)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='clput' Line='clput (parameter, value)'>
  <DD>Put a value into a CL parameter.  The parameter argument must be a
  string and the value can be anything.  The function returns a string
  of the form "<TT>clput: parameter = value</TT>" where parameter and value are
  the actual values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scan">scan (string, var, ...)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='scan' Line='scan (string, var, ...)'>
  <DD>Parse a string of whitespace separated words into a list of
  keywords or variables.  The number of variables assigned is
  the returned value of the function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fscan">fscan (var, ...)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='fscan' Line='fscan (var, ...)'>
  <DD>Scan a line of a text file into a list of keywords or variables.  The arguments
  are zero or more variable names to which to assign the values of
  the whitespace separated fields.  The number of variables assigned
  is the returned value of the function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imget">imget (parameter)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='imget' Line='imget (parameter)'>
  <DD>Get the value of an image header keyword from the current image.  The
  argument must be a string.  The function value is the value of the keyword.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imput">imput (parameter, value)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='imput' Line='imput (parameter, value)'>
  <DD>Put a value into an image header keyword for the current image.  The
  parameter argument must be a string and the value can be anything.  If the
  keyword exists it will be modified and if it does not exist it will be
  added.  The function returns a string of the form "<TT>imput: parameter =
  value</TT>" for new keywords or "<TT>imput: parameter = old_value -&gt; value</TT>" for
  modified keywords where parameter and value are the actual values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imdel">imdel (parameter)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='imdel' Line='imdel (parameter)'>
  <DD>Delete an image header keyword.  The parameter argument must be a string.
  The returned values are the strings "<TT>imdel: parameter not found</TT>"
  or "<TT>imdel: parameter = value (DELETED)</TT>" where parameter is the parameter
  name and value is the old value.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_formats">FORMATS</A></H2>
  <! BeginSection: 'FORMATS'>
  <UL>
  A  format  specification has the form "<TT>%w.dCn</TT>", where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code "<TT>r</TT>" only.  The w and d fields are optional.  The  format
  codes C are as follows:
      
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
  <P>
  %h	    format as nn:nn:nn.n
  %15h	    right justify nn:nn:nn.n in field of 15 characters
  %-15h	    left justify nn:nn:nn.n in a field of 15 characters
  %12.2h	    right justify nn:nn:nn.nn
  %-12.2h	    left justify nn:nn:nn.nn
      
  %H	    / by 15 and format as nn:nn:nn.n
  %15H	    / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H	    / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H	    / by 15 and right justify nn:nn:nn.nn
  %-12.2H	    / by 15 and left justify nn:nn:nn.nn
  <P>
  \n          insert a newline
  </PRE>
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The following command file exercises the astronomical functions:
  <P>
  <PRE>
      cl&gt; type cmds
      observat = "kpno"
      time = sexstr (1.2345)
      epoch = epoch (@'date-obs', ut)
      jd = julday (@'date-obs', ut)
      mst = mst (@'date-obs', ut, obsdb (observat, "longitude"))
      rap = ra_precess (ra, dec, epoch, 1950)
      dap = dec_precess (ra, dec, epoch, 1950)
      airmass =  airmass (ra, dec, mst, obsdb (observat, "latitude"))
      airmass
      airmass = " "
      airmass = eairmass (ra, dec, mst, itime, obsdb (observat, "latitude"))
      cl&gt; imhead obj001 l+
          ...
  	DATE-OBS= '05/04/87'            /  DATE DD/MM/YY
  	RA      = '13:29:24.00'         /  RIGHT ASCENSION
  	DEC     = '47:15:34.00'         /  DECLINATION
  	UT      = ' 9:27:27.00'         /  UNIVERSAL TIME
  	ITIME   =                  600  /  REQUESTED INTEGRATION TIME (SECS)
          ...
      cl&gt; asthedit obj001 cmds table="" verbose+
      obj001:
        $I = pix
        $D = 22/01/96
        $T = 19:14:41
        observat = kpno
        time = 1:14:04
        epoch = 1987.257752395672
        jd = 2446890.894062519
        mst = 14:53:39.81
        rap = 13:27:49.84
        dap = 47:27:05.72
        airmass = 1.079684154511483
        airmass = 1.07968415451148 -&gt; DELETED
        airmass =  
        airmass =  -&gt; 1.08519059292424
  </PRE>
  <P>
  Note the use of the keyword deletion and syntax for adding an empty
  value.
  <P>
  2.  The following command file shows computing a mid-ut and using a table
  of values.
  <P>
  <PRE>
      cl&gt; type cmds
      midut = sexstr ($ut + $itime/3600./2.)
      imagetyp = $imagetyp
      cl&gt; type table
      object	9:27:27		600
      comp	9:48:00		10
      object	9:49:00		600
      flat	12:00:00	2
      cl&gt; asthedit obj* cmds table=table colnames="imagetyp ut itime" verbose+
      obj001.imh:
        $I = obj001.imh
        $D = 22/01/96
        $T = 20:38:39
        midut = 9:32:27
        imagetyp = object
      obj002.imh:
        $I = obj002.imh
        midut = 9:48:05
        imagetyp = comp
      ...
  </PRE>
  <P>
  3.  The following example computes quantities used by some NOAO tasks from
  a minimal ESO/IHAP header.
  <P>
  <PRE>
      cl&gt; type eso.dat
      observat = "eso"
      ut = sexstr ((@'tm-start'+0.1) / 3600.)
      utend = sexstr ((@'tm-end'+0.1) / 3600.)
      epoch = epoch (@'date-obs', ut)
      st = mst (@'date-obs', ut, obsdb (observat, "longitude"))
      exptime = (utend&gt;ut)?(utend-ut)*3600.:(utend+24-ut)*3600.
      ra = sexstr (@'postn-ra' / 15)
      dec = sexstr (@'postn-dec')
      airmass = airmass (ra, dec, st, obsdb (observat, "latitude"))
      imagetyp =  $imagetyp
      filter = $filter
      cl&gt; type table.dat
      object	V
      as&gt; imhead eso
          ....
  	DATE-OBS= '12/12/92'            / Date this data created dd/mm/yy
  	TM-START=             84854.    / '23:34:14' measurement start time
  	TM-END  =             84974.    / '23:36:14' measurement end time (U
  	TIME-SID=                 1.    / '00:00:01' sidereal start time
  	POSTN-RA=           354.0709    / '23:36:17' tel. position right-asc
  	POSTN-DE=           6.556945    /'+06:33:25' tel. position declinati
          ....
      as&gt; asthedit eso eso.dat table=table.dat col="imagetyp filter" verbose+
      eso:
        $I = eso
        $D = 23/01/96
        $T = 09:02:55
        observat = eso
        ut = 23:34:14
        utend = 23:36:14
        epoch = 1992.948616307863
        st = 0:18:56.76
        exptime = 120.000000000006
        ra = 23:36:17
        dec = 6:33:25
        airmass = 1.255875187126549
        imagetyp = object
        filter = V
      as&gt; imhead eso
  	...
  	DATE-OBS= '12/12/92'            / Date this data created dd/mm/yy
  	TM-START=             84854.    / '23:34:14' measurement start time
  	TM-END  =             84974.    / '23:36:14' measurement end time (U
  	TIME-SID=                 1.    / '00:00:01' sidereal start time
  	POSTN-RA=           354.0709    / '23:36:17' tel. position right-asc
  	POSTN-DE=           6.556945    /'+06:33:25' tel. position declinati
  	OBSERVAT= 'eso     '
  	UT      = '23:34:14'
  	UTEND   = '23:36:14'
  	EPOCH   =     1992.94861630786
  	ST      = '0:18:56.76'
  	EXPTIME =     120.000000000006
  	RA      = '23:36:17'
  	DEC     = '6:33:25 '
  	AIRMASS =     1.25587518712655
  	IMAGETYP= 'object  '
  	FILTER  = 'V       '
  	...
  </PRE>
  <P>
  The 0.1 in the UT calculation are to account for round-off.
  Note the use of the conditional expression for the exposure time.
  <P>
  4.  The following example is for a case where there was no telescope
  information but there is date and time information.  This example is
  relevant to data from the Kitt Peak Schmidt telescope circa 1993.
  A table is prepared with the RA, Dec, and Epoch of each observation
  and all other information is derived from the date, ut, and observatory
  database. 
  <P>
  <PRE>
      cl&gt; type table.dat
      12:45:32  +49:34:12   1950
      13:12:02  -01:12:05   1950
      cl&gt; type cmds.hast
      epoch   = epoch (@'date-obs', ut)
      ra      = ra_precess ($ra, $dec, $epoch, epoch)
      dec     = dec_precess ($ra, $dec, $epoch, epoch)
      st      = mst (@'date-obs', ut, obsdb (observat, "longitude"))
      airmass = eairmass (ra, dec, st, exptime, obsdb (observat, "latitude"))
      midut   = sexstr (ut + exptime/3600./2.)
      cl&gt; asthedit *.imh cmds.hast table=table.dat colnames="ra dec epoch" ver+
      sbs0119.imh:
        $I = sbs0119.imh
        $D = 23/01/96
        $T = 10:38:32
        epoch = 1987.257752395672
        ra = 12:47:14.84
        dec = 49:22:00.39
        st = 14:53:39.81
        airmass = 1.154765212092646
        midut = 9:32:27
      sbs0120.imh:
        $I = sbs0120.imh
        epoch = 1987.257752395672
        ra = 13:13:56.90
        dec = -1:23:54.30
        st = 14:53:39.81
        airmass = 1.336016291162518
        midut = 9:32:27
  </PRE>
  <P>
  Note the use of the table and image header epochs in the precession.
  <P>
  5.  The following example shows the use of the printf function,
  and a null image name, and interactive command input.
  <P>
  <PRE>
      cl&gt; asthedit "" ""
      astcalc&gt; ra = 12:20:30
      astcalc&gt; dec = 45:00:10
      astcalc&gt; ep1 = 1950
      astcalc&gt; ep2 = 2000
      astcalc&gt; ra1 = ra_precess (ra, dec, ep1, ep2)
      astcalc&gt; printf ("ra=%h dec=%h\n", ra1, dec_precess (ra, dec, ep1, ep2))
      ra=12:22:57.4 dec=44:43:32.25
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ASTHEDIT">ASTHEDIT V2.11.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='ASTHEDIT' Line='ASTHEDIT V2.11.2'>
  <DD>Y2K update:  The epoch, julday, and mst functions now take either the old
  or new FITS style date strings.  The time argument is optional and if
  it is not specified the time from the date string is used and if neither
  time is present a value of 0h is used.  New internal variables $GMD,
  $GMT, and $GMDT for the current time Greenwich time are defined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ASTHEDIT">ASTHEDIT V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='ASTHEDIT' Line='ASTHEDIT V2.11'>
  <DD>There are new astronomical functions and input/output functions.
  <P>
  The command syntax may now use "<TT>=</TT>" as a delimiter as well as the whitespace.
  <P>
  A new parameter "<TT>update</TT>" allows protecting images and accessing read-only
  images for the purpose of calculating and printing quantities.
  <P>
  The special variable name "<TT>$I</TT>" has the value of the image name, $D
  the current date, and $T the current time.
  <P>
  The case of no image name creates and deletes a temporary image so the
  task can be used purely as a calculator (but see <B>astcalc</B>).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  astcalc, hedit, hfix, mkheader, setairmass, setjd, asttimes, precess,
  observatory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>