.. _invertfit:

invertfit — Compute the standard indices by inverting the fit
=============================================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  invertfit -- evaluate the fit by inverting the system of equations defined
  in the configuration file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  invertfit observations config parameters calib
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>observations</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observations' Line='observations'>
  <DD>The list of files containing the observations.
  <I>Observations</I> are multi-column text files, whose columns are delimited
  by whitespace, and whose first column is reserved for an object id.
  All observations files in the list must have the same format.
  </DD>
  </DL>
  <DL>
  <DT><B>config</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='config' Line='config'>
  <DD>The configuration file. <I>Config</I> is a text file which specifies the
  format of the <I>observations</I> and <I>catalog</I> files, and defines the
  form of the transformation equations to be inverted.
  More information can be obtained about the format of this file
  by typing "<TT>help mkconfig</TT>" and "<TT>help config</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>parameters</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters'>
  <DD>The name of the file containing the fit produced by the FITPARAMS task.
  <I>Parameters</I> is a text file 
  containing the fitted parameter values for each
  equation and other information about the quality of the
  fit. Records in <I>parameters</I> are assigned a name equal to the label
  of the fitted equation. If more than one record in <I>parameters</I> has
  the same name then the last record is used by INVERTFIT to do the inversion.
  </DD>
  </DL>
  <DL>
  <DT><B>calib</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calib' Line='calib'>
  <DD>The name of the output file. <I>Calib</I> is a text file containing
  the name of the fitted object in the first column,
  followed by the values of the <I>print</I> variables if any,
  followed by the fitted value of each catalog variable, error in the
  catalog variable (if <I>errors</I> is not
  "<TT>undefined</TT>"), and residual of the fit (if catalog matching is enabled).
  </DD>
  </DL>
  <DL>
  <DT><B>catalogs = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs = ""'>
  <DD>The list of files containing the catalog data.
  <I>Catalogs</I> are multi-column text files, whose columns are delimited
  by whitespace, and whose first column is always reserved for an object id.
  All catalog files in the list must have the same format.
  If <I>catalogs</I> is "<TT></TT>", then no id matching with the observations files
  is done, and the residuals of the fit cannot be computed.
  </DD>
  </DL>
  <DL>
  <DT><B>errors = "<TT>obserrors</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errors' Line='errors = "obserrors"'>
  <DD>The algorithm used to compute formal errors for each object fit. The choices
  are:
  <DL>
  <DT><B>undefined</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='undefined' Line='undefined'>
  <DD>No errors are computed and no error values are output.
  </DD>
  </DL>
  <DL>
  <DT><B>obserrors</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='obserrors' Line='obserrors'>
  <DD>The error in each fitted value is computed by summing in quadrature
  the contribution to the total error made by each individual error in the
  observations files variables. If no error columns are defined for the
  observations files, the error is assigned the value INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B>equations</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equations' Line='equations'>
  <DD>The error in each fitted value is computed by summing in quadrature
  the contribution to the total error made by each error 
  equation associated with a transformation equation.
  If no error equation is defined for any of the transformation
  equations, then the error is assumed to be INDEF.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>objects = "<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objects' Line='objects = "all"'>
  <DD>The type of objects to output to <I>calib</I>. The choices are:
  <DL>
  <DT><B>all   </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='all' Line='all   '>
  <DD>Both program and standard objects are output.
  </DD>
  </DL>
  <DL>
  <DT><B>program = yes</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='program' Line='program = yes'>
  <DD>Only program objects are output.
  </DD>
  </DL>
  <DL>
  <DT><B>standard = yes</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='standard' Line='standard = yes'>
  <DD>Only standard objects are output.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>print = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print' Line='print = ""'>
  <DD>Additional variables to be printed in the output file. These variables are
  printed immediately after the object id, and may be any of the
  catalog variables, observations variables, or the set equation variables
  defined in <I>config</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>format = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = ""'>
  <DD>An SPP style format string to be used for formatting the output data, in
  place of the default format. SPP format
  strings are described in detail in the formats section.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append the output to <I>calib</I> instead of creating a new file. If the
  file already exists and <I>append</I> is "<TT>no</TT>" INVERTFIT will abort.
  </DD>
  </DL>
  <DL>
  <DT><B>catdir = "<TT>)_.catdir</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdir' Line='catdir = ")_.catdir"'>
  <DD>The directory containing the supported standard star catalogs.
  The default parameter value  redirects <I>catdir</I>
  to a package parameter of the same name. A list of standard
  catalogs may be obtained by printing the file "<TT>photcal$catalogs/README</TT>".
  Alternatively the user may create their own standard star catalogs 
  and standard star catalog directory.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  INVERTFIT computes magnitudes and colors for the standard or
  program stars in <I>observations</I> by inverting the system of
  transformation equations defined in <I>config</I>, using the
  parameter values in the file <I>parameters</I> produced by the FITPARAMS
  task, and writes the fitted values to the output file <I>calib</I>.
  If <I>append</I> is "<TT>yes</TT>" output may be appended to an existing file.
  <P>
  INVERTFIT computes the values of the catalog variables for the program
  stars by inverting the system of transformation equations defined in
  <I>config</I>. IT IS THE RESPONSIBILITY OF THE USER TO ENSURE THAT
  THE SYSTEM OF EQUATIONS IS ACTUALLY INVERTIBLE.
  Two minimum conditions must be met. First, the number of
  transformation equations must be greater than or equal to the number of
  catalog variables to be fit, and second, all the catalog variables must
  be on the right-hand side of the transformation equations.
  INVERTFIT will test for both of these conditions, issue a warning, and
  terminate execution if either of these conditions are not met.
  <P>
  Below are two sets of transformation equations.
  The first set
  can be inverted by INVERTFIT, the second set cannot and must be
  evaluated by EVALFIT. In both cases the catalog variables to be fit
  are V and BV, and the observed quantities are mv, mb, Xv, and Xb.
  <P>
  <PRE>
      System 1:    mv = v0 + V + v1 * Xv + v2 * BV
  		 mb = b0 + V + BV + b1 * Xb + b2 * BV
  <P>
      System 2:    V = v0 + mv + v1 * (Xv + Xb) / 2. + v2 * (mb - mv)
  		 BV = b0 + b1 * (Xv + Xb) / 2.0 + b2 * (mb - mv) 
  </PRE>
  <P>
  It is possible though not recommended, to use set equation variables as
  unknowns in the transformation
  equations, provided that the total number of unknowns on the right-hand
  side of the equations remains less than or equal to the number of transformation
  equations. Set equations containing catalog variables must not be used
  in the left-hand side of the transformation equations. An example of a set
  of transformation equations which use a set equation variable is shown
  below. Note that there still are only two independent variables V and BV and
  that the output file <I>calib</I> will contain V and BV only.
  <P>
  <PRE>
      System 1:    set B = V + BV
      		 mv = v0 + V + v1 * Xv + v2 * BV
  		 mb = b0 + B + b1 * Xb + b2 * BV
  </PRE>
  <P>
  Some systems of equations are invertible but do not have a UNIQUE solution.
  A sample of such a system is shown below.
  There are quadratic terms in BV, implying that this set of
  equations probably has two solutions, both of which may be
  be mathematically correct, but only one of which is physically meaningful.
  INVERTFIT does not test for this condition and may converge to either solution.
  <P>
  <PRE>
      System 1: mv = v0 + V + v1 * BV + v2 * BV ** 2
  	      mb = b0 + V + BV + b1 * BV + b2 * BV ** 2
  </PRE>
   
  <P>
  Formal errors for the fit may
  be computed by,  1) setting <I>errors</I> to "<TT>obserrors</TT>" and using the
  error columns defined in the observations section of <I>config</I>
  to estimate the errors or 2) setting <I>errors</I> to "<TT>equations</TT>" and
  using the error equations defined in <I>config</I> to estimate the errors.
  <P>
  If the user wishes to match the objects in <I>observations</I> with those
  in <I>catalogs</I> in order for example, to compute the residuals of the fit,
  <I>catalogs</I> must be defined. Similarly if <I>objects</I> is "<TT>program</TT>"
  or "<TT>standard</TT>", <I>catalogs</I> must be defined in order to enable
  id matching.
  <P>
  Legal <I>catalog</I> and <I>observations</I> files are multi-column text
  files whose columns are delimited by whitespace.
  The first column of a catalog file is <I>always</I> reserved for an object id.
  The first column of an observations file is reserved for an
  object id which can be
  used to match the observational data with the catalog data.
  All other columns may contain any quantity which can be
  expressed as an integer or real number.  Sexagesimal format numbers
  (hh:mm:ss) are interpreted internally as real numbers. The constant
  INDEF can be used to represent data that is missing or undefined.
  Double precision and complex data are
  not supported. Lines beginning with "<TT>#</TT>" are treated as comment lines.
  <P>
  By default INVERTFIT prints out the id,
  followed by the variables listed in the <I>print</I>
  parameter, followed by the fit value, estimated
  error (if <I>errors</I> is "<TT>undefined</TT>", and residual of the fit (for any
  standard star observations that can be matched with the catalog values)
  for each fitted catalog variable.
  The user can format the output by setting the <I>format</I> parameter to an SPP
  style string. SPP format strings are described in detail below.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Formats</H3>
  <! BeginSection: 'FORMATS'>
  <UL>
  A format specification has the form "<TT>%w.dCn</TT>", where w is the field width,
  d is the number of decimal places or the number of digits of precision,
  C is the format code, and n is radix character for format code "<TT>r</TT>" only.
  The w and d fields are optional.  The format codes C are as follows:
  <P>
  <PRE>
  b	boolean (YES or NO)
  c	single character (c or '\c' or '\0nnn')
  d	decimal integer
  e	exponential format (D specifies the precision)
  f	fixed format (D specifies the number of decimal places)
  g	general format (D specifies the precision)
  h	hms format (hh:mm:ss.ss, D = no. decimal places)
  m	minutes, seconds (or hours, minutes) (mm:ss.ss)
  o	octal integer
  rN	convert integer in any radix N
  s	string (D field specifies max chars to print)
  t	advance To column given as field W
  u	unsigned decimal integer 
  w	output the number of spaces given by field W
  x	hexadecimal integer
  z	complex format (r,r) (D = precision)
  <P>
  <P>
  Conventions for w (field width) specification:
  <P>
      W =  n	right justify in field of N characters, blank fill
  	-n	left justify in field of N characters, blank fill
  	0n	zero fill at left (only if right justified)
  absent, 0	use as much space as needed (D field sets precision)
  <P>
  <P>
  Escape sequences (e.g. "\n" for newline):
  <P>
  \b	backspace   (<B>not implemented</B>)
  formfeed
  \n	newline (crlf)
  \r	carriage return
  \t	tab
  \"	string delimiter character
  \'	character constant delimiter character
  \\	backslash character
  \nnn	octal value of character
  <P>
  Examples
  <P>
  %s          format a string using as much space as required
  %-10s	    left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s	    right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
  <P>
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e	    print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g	    print a real number right justified in general format
  %-12.5g     same as above but left justified
  <P>
  \n          insert a newline
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Evaluate the fit for a list of program stars in m92. Use the errors
  in the observed quantities to estimate the errors.
  <P>
  <PRE>
  	ph&gt; invertfit m92.obs m92.cfg m92.fit m92.cal
  </PRE>
  <P>
  2. Repeat the fit computed above but include the variables xu and yu which
  are the positions of the objects in the u frame in the output.
  <P>
  <PRE>
  	ph&gt; invertfit m92.obs m92.cfg m92.fit m92.cal print="xu,yu"
  </PRE>
  <P>
  3. Repeat the fit computed in 1 but format the output. The user has
  determined that the output will have 7 columns containing the object
  id, V, error(V), resid(V), BV, error(BV), and resid(BV).
  <P>
  <PRE>
  	ph&gt; invertfit m92.obs  m92.cfg m92.fit m92.cal\<BR>
    	    format="%-10.10s %7.3f %6.3f %6.3f %7.3f %6.3f %6.3f\n"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkconfig,chkconfig,fitparams,evalfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'SEE ALSO'  >
  
