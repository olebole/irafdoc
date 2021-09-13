.. _evalfit:

evalfit — Compute the standard indices by evaluating the fit
============================================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  evalfit -- evaluate the fit
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  evalfit observations config parameters calib
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
  <DD>The configuration file. <I>Config</I> is a text file which
  specifies the format of the <I>observations</I> and <I>catalog</I> files, and
  defines the form of the transformation equations to be evaluated.
  More information can be obtained about this file by typing
  "<TT>help mkconfig</TT>" and "<TT>help config</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>parameters</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters'>
  <DD>The name of the file produced by the FITPARAMS task.
  <I>Parameters</I> is a text file 
  containing the fitted parameter values for each
  equation and other information about the quality of the
  fit. Records in <I>parameters</I> are assigned a name equal to the label
  of fitted equation. If more than one record in <I>parameters</I> has
  the same name then the last record of that name is used by EVALFIT to 
  evaluate the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>calib</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calib' Line='calib'>
  <DD>The name of the output file. <I>Calib</I> is a text file
  containing the name of the fitted object in the first column,
  followed by the <I>print</I>
  variables if any, followed by the fitted value, error of the fit (if
  <I>errors</I> is not "<TT>undefined</TT>"), and residual of the
  fit (if catalog matching is enabled) for each equation.
  </DD>
  </DL>
  <DL>
  <DT><B>catalogs</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs'>
  <DD>The list of files containing the catalog data.
  <I>Catalogs</I> are multi-column text files, whose columns are delimited
  by whitespace, and whose first column is reserved for an object id.
  All catalog files in the list must have the same format.
  If <I>catalogs</I> = "<TT></TT>", then no id matching with the observations
  files is done.
  </DD>
  </DL>
  <DL>
  <DT><B>errors = "<TT>undefined</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errors' Line='errors = "undefined"'>
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
  observations file variables. If no error columns are defined for the
  observations files the error is assumed to be INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B>equations</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equations' Line='equations'>
  <DD>The error in each fitted value is computed by evaluating the error
  equations associated with each transformation equation. If no error equation
  is defined then the error is assumed to be INDEF.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>objects = "<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objects' Line='objects = "all"'>
  <DD>The type of objects to output to <I>calib</I>. The choices are:
  <DL>
  <DT><B>all</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='all' Line='all'>
  <DD>Both program and standard stars are output.
  </DD>
  </DL>
  <DL>
  <DT><B>program = yes</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='program' Line='program = yes'>
  <DD>Only program stars are output.
  </DD>
  </DL>
  <DL>
  <DT><B>standard = yes</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='standard' Line='standard = yes'>
  <DD>Only standard stars are output.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>print = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print' Line='print = ""'>
  <DD>Additional variables to be printed in the output file. These variables are
  printed immediately after the id, and may be any of the
  catalog variables, observations variables, or the set equation variables
  defined in <I>config</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>format = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = ""'>
  <DD>An SPP style format string to apply to the output data, in place of the
  default format.  SPP format strings
  are described in detail in the formats section.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append the output to <I>calib</I> instead of creating a new file. If the
  file already exists and <I>append</I> is "<TT>no</TT>" EVALFIT will abort.
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
  EVALFIT evaluates the transformation  equations
  for the program and/or standard objects in <I>observations</I>, using
  the transformation equations defined in <I>config</I>,
  the fitted parameter values in the file <I>parameters</I> produced by the
  FITPARAMS
  task, and writes the output to the file <I>calib</I>. If <I>append</I> is "<TT>yes</TT>"
  output may be appended to an existing file.
  <P>
  EVALFIT computes the values of the catalog variables for the program
  stars by inserting the observations variables directly into the
  transformation equations. EVALFIT can evaluate any number of transformation
  equations, but if there are any standard catalog variables in the right-hand
  side of the transformation equation, EVALFIT will assign INDEF to the fitted
  for that equation.
  <P>
  Below are two sets of transformation equations. The first set can be evaluated
  with EVALFIT, the second set cannot and must be inverted with INVERTFIT.
  In both cases the catalog variables to be fit are V and BV, and
  the observed quantities are mv, mb, Xv, and Xb.
  <P>
  <PRE>
      System 1:    V = v0 + mv + v1 * (Xv + Xb) / 2. + v2 * (mb - mv)
  		 BV = b0 + b1 * (Xv + Xb) / 2. + b2 * (mb - mv)
  <P>
      System 2:    mv = v0 + V + v1 * Xv + v2 * BV
  		 mb = b0 + V + BV + b1 * Xb + b2 * BV
  </PRE>
  <P>
  <P>
  Formal errors for each fit may
  be computed by,  1) setting <I>errors</I> to "<TT>obserrors</TT>" and using the
  error columns defined in the observations section of <I>config</I>
  to estimate the errors or 2) evaluating the error equations defined in
  <I>config</I>.
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
  used to match the observational data with the corresponding catalog data.
  All other columns may contain any quantity which can be
  expressed as an integer or real number.  Sexagesimal format numbers
  (hh:mm:ss) are interpreted internally as real numbers. The constant
  INDEF can be used to represent data that is missing or undefined.
  Double precision and complex data are
  not supported. Lines beginning with "<TT>#</TT>" are treated as comment lines.
  <P>
  By default EVALFIT prints out the object id,
  followed by the variables listed in the <I>print</I>
  parameter, followed by the fit value, estimated
  error (if <I>errors</I> is not "<TT>undefined</TT>"), and residual of the fit
  (for any standard star observations that can be matched with the
  catalog values) for each fitted equation. The user can format the output
  by setting the <I>format</I> parameter to an SPP style string. 
  SPP format strings are described in detail below.
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
  <P>
  Note that deferred value fields are <B>not implemented</B> in EVALFIT.
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
  	ph&gt; evalfit m92.obs m92.cfg m92.fit m92.cal
  </PRE>
  <P>
  2. Repeat the fit computed above but include the variables xu and yu which
  are the positions of the objects in the u frame in the output.
  <P>
  <PRE>
  	ph&gt; evalfit m92.obs m92.cfg m92.fit m92.cal print="xu,yu"
  </PRE>
  <P>
  3. Repeat the fit computed above but format the output. The user has
  determined that the output will have 5 columns containing the object id,
  xu, yu, fit value and fit error respectively.
  <P>
  <PRE>
  	ph&gt; evalfit m92.obs m92.cfg m92.fit m92.cal print="xu,yu"\<BR>
  	    format="%-10.10s  %-7.2f  %-7.2f  %-7.3f  %-6.3f\n"
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkconfig,chkconfig,fitparams,invertfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'SEE ALSO'  >
  
