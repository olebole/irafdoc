ccget — Extract objects from a text file catalog
================================================

**Package: imcoords**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ccget (Oct00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imcoords</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ccget (Oct00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ccget</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ccget -- extract objects in a user specified field from a text file catalog
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ccget input output lngcenter latcenter lngwidth latwidth
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input text file catalog(s). The text file columns must be
  delimited by whitespace and all the input catalogs must have the same format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output catalogs containing the extracted objects. The number of
  output catalogs must be one or equal to the number of input catalogs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngcenter">lngcenter, latcenter</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngcenter' Line='lngcenter, latcenter'>
  <DD>The center of the field containing the objects to be extracted. Lngcenter and
  latcenter are assumed to be in the coordinate system specified by
  <I>fcsystem</I>, e.g. ra and dec for equatorial systems, galactic longitude and
  latitude for galactic systems, etc. and in the units specified by
  <I>fclngunits</I> and <I>latunits</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngwidth">lngwidth, latwidth</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngwidth' Line='lngwidth, latwidth'>
  <DD>The width of the user specified field in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fcsystem">fcsystem = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fcsystem' Line='fcsystem = ""'>
  <DD>The celestial coordinate system of the field center. If undefined fcsystem
  defaults to the catalog celestial coordinate system specified by
  <I>catsystem</I>. The two systems of
  most interest to users are "<TT>j2000</TT>" and "<TT>b1950</TT>". The full set of options is:
  <P>
  <DL>
  <DT><B><A NAME="l_equinox">equinox [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equinox' Line='equinox [epoch]'>
  <DD>The equatorial mean place post-IAU 1976 (FK5) system if equinox is a
  Julian epoch, e.g. J2000.0 or 2000.0, or the equatorial mean place
  pre-IAU 1976 system (FK4) if equinox is a Besselian epoch, e.g. B1950.0
  or 1950.0. Julian equinoxes are prefixed by a J or j, Besselian equinoxes
  by a B or b. Equinoxes without the J / j or B / b prefix are treated as
  Besselian epochs if they are &lt; 1984.0, Julian epochs if they are &gt;= 1984.0.
  Epoch is the epoch of the observation and may be a Julian
  epoch, a Besselian epoch, or a Julian date. Julian epochs
  are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to the epoch type of
  equinox if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fk5">fk5 [equinox] [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fk5' Line='fk5 [equinox] [epoch]'>
  <DD>The equatorial mean place post-IAU 1976 (FK5) system where equinox is
  a Julian or Besselian epoch e.g. J2000.0  or B1980.0.
  Equinoxes without the J / j or B / b prefix are treated as Julian epochs.
  The default value of equinox is J2000.0.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fk4">fk4 [equinox] [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fk4' Line='fk4 [equinox] [epoch]'>
  <DD>The equatorial mean place pre-IAU 1976 (FK4) system where equinox is a
  Besselian or Julian epoch e.g. B1950.0  or J2000.0,
  and epoch is the Besselian epoch, the Julian epoch, or the Julian date of the
  observation.
  Equinoxes without the J / j or B / b prefix are treated
  as Besselian epochs. The default value of equinox is B1950.0. Epoch
  is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_noefk4">noefk4 [equinox] [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='noefk4' Line='noefk4 [equinox] [epoch]'>
  <DD>The equatorial mean place pre-IAU 1976 (FK4) system but without the E-terms
  where equinox is a Besselian or Julian epoch e.g. B1950.0 or J2000.0,
  and epoch is the Besselian epoch, the Julian epoch, or the Julian date of the
  observation.
  Equinoxes without the J / j or B / b prefix are treated
  as Besselian epochs. The default value of equinox is B1950.0.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian day.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apparent">apparent epoch</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='apparent' Line='apparent epoch'>
  <DD>The equatorial geocentric apparent place post-IAU 1976 system where
  epoch is the epoch of observation.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ecliptic">ecliptic epoch</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ecliptic' Line='ecliptic epoch'>
  <DD>The ecliptic coordinate system where epoch is the epoch of observation.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch values &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian day.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_galactic">galactic [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='galactic' Line='galactic [epoch]'>
  <DD>The IAU 1958 galactic coordinate system.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date. The default value of epoch is B1950.0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_supergalactic">supergalactic [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='supergalactic' Line='supergalactic [epoch]'>
  <DD>The deVaucouleurs supergalactic coordinate system.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date. The default value of epoch is B1950.0.
  </DD>
  </DL>
  <P>
  In all the above cases fields in [] are optional with the defaults as
  described. The epoch field for the fk5, galactic, and supergalactic
  coordinate systems is only used if the input coordinates are in the
  equatorial fk4, noefk4, or fk5 systems and proper motions are supplied.
  Since ccget does not currently support proper motions these fields are
  not required.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_fclngunits">fclngunits = "<TT></TT>", fclatunits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fclngunits' Line='fclngunits = "", fclatunits = ""'>
  <DD>The units of the field center coordinates. The options are "<TT>hours</TT>", "<TT>degrees</TT>",
  and "<TT>radians</TT>" for the ra / longitude coordinate and "<TT>degrees</TT>" and "<TT>radians</TT>"
  for the dec / latitude coordinates. If fclngunits and fclatunits are undefined
  they default to the preferred units for the given system, e.g. "<TT>hours</TT>" and
  degrees"<TT> for equatorial systems and </TT>"degrees"<TT> and </TT>"degrees"<TT> for ecliptic,
  galactic, and supergalactic systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_colaliases">colaliases = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colaliases' Line='colaliases = ""'>
  <DD>The list of input catalog column aliases separated by commas. By default the
  catalog columns are </TT>"c1"<TT>, </TT>"c2"<TT>, </TT>"c10"<TT>, etc. If colaliases is defined then
  the aliases are assigned to the columns in order. For example if colaliases
  is </TT>"id,ra,dec,v,bv"<TT> then columns c1, c2, c3, c4, c5 will be assigned
  the names id, ra, dec, v, and bv and any remaining columns in the input catalog
  file will be assigned default names beginning with c6.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngcolumn">lngcolumn = </TT>"c2"<TT>, latcolumn = </TT>"c3"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngcolumn' Line='lngcolumn = "c2", latcolumn = "c3"'>
  <DD>The input catalog columns containing the coordinates of catalog objects.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catsystem">catsystem = </TT>"j2000"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catsystem' Line='catsystem = "j2000"'>
  <DD>The celestial coordinate system of the input catalog(s). The two systems of
  most interest to users are </TT>"j2000"<TT> and </TT>"b1950"<TT>. The full set of options is
  described in the <I>fcsystem</I> parameter section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catlngunits">catlngunits = "<TT></TT>", catlatunits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catlngunits' Line='catlngunits = "", catlatunits = ""'>
  <DD>The units of the catalog coordinates. The options are "<TT>hours</TT>", "<TT>degrees</TT>",
  and "<TT>radians</TT>" for the ra / longitude coordinate and "<TT>degrees</TT>" and "<TT>radians</TT>"
  for the dec / latitude coordinates. If catlngunits and catlatunits are undefined
  they default to the preferred units for the catalog system, e.g. "<TT>hours</TT>" and
  degrees"<TT> for equatorial systems and </TT>"degrees"<TT> and </TT>"degrees"<TT> for ecliptic,
  galactic, and supergalactic systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outsystem">outsystem = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outsystem' Line='outsystem = ""'>
  <DD>The celestial coordinate system of the output coordinates. If undefined
  outsystem defaults to the celestial coordinate system of the catalog.
  The two systems of most interest to users are </TT>"j2000"<TT> and </TT>"b1950"<TT>. The
  full set of options is described under the <I>fcsystem</I> parameter
  section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_olngunits">olngunits = "<TT></TT>", olatunits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='olngunits' Line='olngunits = "", olatunits = ""'>
  <DD>The units of the output coordinates. The options are "<TT>hours</TT>", "<TT>degrees</TT>",
  and "<TT>radians</TT>" for the ra / longitude coordinate and "<TT>degrees</TT>" and "<TT>radians</TT>"
  for the dec / latitude coordinates. If olngunits and olatunits are undefined
  they default to the preferred units for outsystem, e.g. "<TT>hours</TT>" and degrees"<TT> for
  equatorial systems and </TT>"degrees"<TT> and </TT>"degrees"<TT> for ecliptic, galactic, and
  supergalactic systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_olngformat">olngformat = </TT>""<TT>, olatformat=</TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='olngformat' Line='olngformat = "", olatformat=""'>
  <DD>The output ra / longitude and dec / latitude formats if the output
  celestial coordinate system is different from the catalog celestial
  coordinate system. The defaults are </TT>"  %010.1h"<TT> for hours, </TT>"  %9h"<TT> for degrees
  and </TT>"  %9.7g"<TT> for radians.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exprs">exprs = </TT>"c[*]"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exprs' Line='exprs = "c[*]"'>
  <DD>The list of output columns and column expressions separated by commas.
  By default the entire record for the extracted object is output exactly
  as it is. The output columns can be individual columns e.g. c1 or c5
  or column ranges, e.g. c[1-10] or c[2-4]. Column expressions are
  expressions of the catalog columns, e.g c4 + c5.  Columns and column
  expression are output in the order in which they appear in exprs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_formats">formats = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='formats' Line='formats = ""'>
  <DD>An optional list of column formats separated by commas. Column formats must
  be placeholders, e.g. the letter f for existing columns which are not
  reformatted (with the possible exception of the coordinate columns).
  Column expression formats may be any regular formatting expression.
  For example if <I>exprs</I> is "<TT>c[1-3],c4+c5,c5+c7</TT>", then formats might be
  "<TT>f,%7.3f,%7.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages on the standard output about actions taken by the task.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Ccget extracts objects in a user specified field from the input catalogs
  <I>input</I> and writes the extracted records to the output
  catalogs <I>output</I>.
  <P>
  The user field is specified by the parameters <I>lngcenter</I>, <I>latcenter</I>,
  <I>lngwidth</I>, and <I>latwidth</I>, where the field center is entered in
  the celestial coordinate system specified by <I>fcsystem</I> and the
  units are specified by <I>fclngunits</I> and <I>fclatunits</I>. If fcsystem
  is undefined it defaults to the value of the catalog coordinate system
  <I>catsystem</I>.
  <P>
  The input catalogs must be text files containing 2 or more columns separated
  by whitespace. By default these columns are assigned names of the form
  c1, c2, ..., cn. Legal columns names must have the form described
  in the following column names section. Users may assign their own names
  to the columns by setting
  the <I>colaliases</I> parameter. The input catalog columns <I>lngcolumn</I> and
  <I>latcolumn</I> must contain the ra / longitude and dec / latitude coordinates
  of the catalog objects respectively. The parameters <I>catsystem</I>,
  <I>catlngunits</I>, and <I>catlatunits</I> specify the coordinate system
  of the input catalog and its coordinate units respectively.
  <P>
  At task startup the user field center is transformed from the coordinate
  system defined by <I>fcsystem</I> to the catalog coordinate system
  <I>catsystem</I> and the ra / longitude and dec / latitude limits of the
  user field are computed. As each input catalog record is read, the catalog
  coordinates are decoded and tested against these limits. If the 
  object is inside the user field then the column and column
  expressions specified by <I>exprs</I> are extracted from the input catalogs
  and written to the output catalogs.
  <P>
  If the output celestial coordinate system <I>outsystem</I> is
  different from <I>catsystem</I>, then the catalog coordinates are transformed
  and to the output coordinates system, and written to the output catalog
  in the units specified
  by <I>olngunits</I> and <I>olatunits</I>, with the formats specified by
  <I>olngformat</I> and <I>olatformat</I>. Existing columns are written to
  the output catalog in the same
  format they have in the input catalog. Column expressions are written
  using the formats specified by <I>formats</I> or the builtin defaults
  of %5b, %10d, %10g, or %s for boolean, integer, floating point, or
  string columns  respectively.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_column_names">COLUMN NAMES</A></H2>
  <! BeginSection: 'COLUMN NAMES'>
  <UL>
  <P>
  By default column names are of the form c1, c2, ..., cN. However users can
  also define their own column names, which must have the following syntax
  <P>
  <PRE>
  	{a-zA-Z}[{a-zA-Z0-9._$}]*
  </PRE>
  <P>
  where [] indicates optional, {} indicates a class, - indicates an ascii
  range of characters, and * indicates zero or more occurrences. In words
  a column name must begin with an alphabetic character and be followed
  by any combination of alphabetic, digit, or <TT>'.'</TT>, <TT>'_'</TT>, and <TT>'$'</TT> characters.
  The ccget task imposes a 19 character limit on the columns names so it is
  best to keep them short.
  <P>
  </UL>
  <! EndSection:   'COLUMN NAMES'>
  <H2><A NAME="s_column_expressions">COLUMN EXPRESSIONS</A></H2>
  <! BeginSection: 'COLUMN EXPRESSIONS'>
  <UL>
  <P>
  Expressions must consist of operands and operators. The operands may be
  column names, numeric constants, functions, and quoted string constants.
  Values given as sexagesimal strings are automatically converted to
  decimal numbers. The operators are arithmetic, logical, and string.
  <P>
  The following operators are supported:
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
  </PRE>
  <P>
  The following intrinsic functions are supported:
  <P>
      
  <PRE>
              abs     atan2   deg     log     min     real    sqrt
              acos    bool    double  log10   mod     short   str
              asin    cos     exp     long    nint    sin     tan
              atan    cosh    int     max     rad     sinh    tanh
  </PRE>
  <P>
      
  </UL>
  <! EndSection:   'COLUMN EXPRESSIONS'>
  <H2><A NAME="s_column_formats">COLUMN FORMATS</A></H2>
  <! BeginSection: 'COLUMN FORMATS'>
  <UL>
  <P>
  A  format  specification has the form "<TT>%w.dCn</TT>", where w is the field
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
  <P>
  Conventions for w (field width) specification:
  <P>
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
  <P>
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
  <! EndSection:   'COLUMN FORMATS'>
  <H2><A NAME="s_some_builtin_catalog_formats">SOME BUILTIN CATALOG FORMATS</A></H2>
  <! BeginSection: 'SOME BUILTIN CATALOG FORMATS'>
  <UL>
  <P>
  The nlandolt.dat catalog in noao$photcal/catalogs/ has the following format.
  <P>
  <PRE>
  # Column     Quantity 
  <P>
         1           id
         2           ra
         3          dec
         4            v
         5          b-v
         6          u-b
         7          v-r
         8          r-i
         9          v-i
        10            n   
        11            m 
        12       err(v)
        13     err(b-v)
        14     err(u-b)
        15     err(v-r)
        16     err(r-i)
        17     err(v-i)
  </PRE>
  <P>
  where the coordinates are in j2000, the errors are all mean errors of the mean,
  and n and m are the number of observations and number of independent nights
  of observations respectively.
  <P>
  </UL>
  <! EndSection:   'SOME BUILTIN CATALOG FORMATS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  The catalog references are
  <P>
  <PRE>
  nlandolt.dat - Landolt, A.U. 1992, A.J. 104, 340
  </PRE>
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Example 1. Extract all Landolt standard stars within a 1 degree field
  surrounding the position ra = 3:55:00 dec = 0:00:00 (J2000).
  <P>
  <PRE>
  cl&gt; ccget nlandolt.dat output 03:55:00.0 0:00:00 1.0 1.0
  </PRE>
  <P>
  Example 2. Repeat example 1 but output the coordinates in the b1950
  celestial coordinate system.
  <P>
  <PRE>
  cl&gt; ccget nlandolt.dat output 03:55:00.0 0:00:00 1.0 1.0 \<BR>
  outsystem=b1950
  </PRE>
  <P>
  Example 3. Repeat example 1 but extract only the id, ra, dec, v, 
  and b-v fields from the Landolt catalog.  Note that since these
  columns are the first five in the catalog they can be specified
  as a range.
  <P>
  <PRE>
  cl&gt; ccget nlandolt.dat output 03:55:00.0 0:00:00 1.0 1.0 \<BR>
  exprs="c[1-5]"
  </PRE>
  <P>
  Example 4. Repeat example 1 but extract the id, ra, dec, b and
  b-r colors. Note that b and b-r are not columns in the input catalog
  but may be computed from them. Note also that formats should be
  specified to give the desired spacing, although defaults will be
  supplied.
  <P>
  <PRE>
  cl&gt; ccget nlandolt.dat output 03:55:00.0 0:00:00 1.0 1.0 \<BR>
  exprs="c[1-3],c4+c5,c5+c7" formats="%7.3f,%7.3f
  </PRE>
  <P>
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
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'COLUMN NAMES' 'COLUMN EXPRESSIONS' 'COLUMN FORMATS' 'SOME BUILTIN CATALOG FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>