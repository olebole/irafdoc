.. _printf:

printf — Formatted print to the standard output
===============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  print  -- print to the standard output
  fprint -- print to a parameter
  printf -- formatted print to the standard output
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  print  expr [expr ...]
  fprint param expr [expr ...]
  printf format [arg ...]
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>Any expression, the string value of which is to be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>param</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='param' Line='param'>
  <DD>The <I>fprint</I> call will deposit the output string in the value field of 
  this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>format</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format'>
  <DD>A C-like format specification string containing plain characters, which 
  are simply copied into the output string, and conversion specifications,
  each of which causes conversion and printing of zero or more <I>args</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>arg    </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='arg' Line='arg    '>
  <DD>Any expression, variable, parameter value or constant to be used in the
  <I>format</I> string's conversion specifications.  One arg is required for
  each conversion specification.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>print</I> and <I>fprint</I> commands format a line of text and write
  it to either the standard output or in the case of <I>fprint</I>,
  the p_value field of the named parameter.  The output is free format although
  spaces may be specifically inserted (as quoted string constants) to make the
  output easier to read.  One space is automatically inserted after each
  numeric argument; this can be defeated by coercing the argument to a string
  with the <I>str</I> intrinsic function.  A newline is automatically output
  at the end of the output line.  I/O redirection may be used with <I>print</I>
  or <I>printf</I> to write to a file or through a pipe to another task.
  <P>
  The <I>printf</I> command allows more control over the output format and can
  convert arguments for printing as another type.  The <I>format</I> string
  contains plain text characters and format specifications as well as
  escape sequences for printing tabs, newlines, etc. Unlike the other
  two commands, spaces and newlines must be explicitly given in the format
  string.  
  <P>
  A format specification has the form "<TT>%[W][.D]Cn</TT>", where W is  the  field
  width,  D is the number of decimal places or the number of digits of
  precision, C is the format  code,  and  N  is  radix  character  for
  format  code "<TT>r</TT>" only.  The W and D fields are optional.  The format
  codes C are as follows:
  <P>
  <PRE>
         b    boolean (YES or NO)
         c    single character (c or '\c' or '\0nnn')
         d    decimal integer
         e    exponential format (D specifies the precision)
         f    fixed format (D specifies the number of decimal places)
         g    general format (D specifies the precision)
         h    hms format (hh:mm:ss.ss, D = no. decimal places)
         m    minutes, seconds (or hours, minutes) (mm:ss.ss)
         o    octal integer
         rN   convert integer in any radix N
         s    string (D field specifies max chars to print)
         t    advance To column given as field W
         u    unsigned decimal integer 
         w    output the number of spaces given by field W
         x    hexadecimal integer
         z    complex format (r,r) (D = precision)
  </PRE>
  <P>
  Conventions for W (field width) specification:
  <P>
  <PRE>
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
      absent, 0   use as much space as needed (D field sets precision)
  </PRE>
  <P>
  Escape sequences (e.g. "<TT>\n</TT>" for newline):
  <PRE>
               formfeed
          \n      newline (crlf)
          \r      carriage return
          \t      tab
          \"      string delimiter character
          \'      character constant delimiter character
          \\      backslash character
          \nnn    octal value of character
  </PRE>
  <P>
  Compute mode (a parenthesized argument list) is recommended for this task
  to avoid surprises.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the name of the current terminal.
  <P>
  	cl&gt; print ("<TT>terminal = </TT>", envget ("<TT>terminal</TT>"))
  <P>
  2. Output a blank line on the standard output, e.g., in a script.
  <P>
  	print ("<TT></TT>")
  <P>
  3. Format a command and send it to the host system.  In this example,
  "<TT>fname</TT>" is a string valued parameter.
  <P>
  	cl&gt; print ("<TT>!ls -l </TT>", fname) | cl
  <P>
  4. Write to a file.
  <P>
  <PRE>
  	for (x=1.;  x &lt; 1E5;  x *= 10) 
  	    print ("the sqrt of ", x, "is ", sqrt(x), &gt;&gt; "output")
  </PRE>
  <P>
  5. Print a formatted string.
  <P>
  <PRE>
  	cl&gt; printf ("pi = %.6f\n", 2*atan2(1.0,0.0))
  	pi = 3.141593
  	cl&gt; printf ("RA = %h  DEC = %m\nExptime = %8.2f\n",ra,dec,etime)
  	RA = 18:32:33.5 DEC = 23:45.2	Exptime =     1.57
  </PRE>
  <P>
  6. Print to a parameter.  Note that <I>fprint</I> allows you to create a 
  formatted string, whereas the scan() example requires a struct parameter.
  <P>
  <PRE>
  	cl&gt; x = 3.14159
  	cl&gt; fprint (s1, "pi = ", x)
  	cl&gt; = s1
  	pi = 3.14159
  <P>
  	     or 
  <P>
  	cl&gt; printf ("pi = %g\n", x) | scan (line)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The <I>fprint</I> task is not very useful since the same thing can be
  accomplished by string concatenation and assignment.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  scan, scanf, fscan, fscanf, strings
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
