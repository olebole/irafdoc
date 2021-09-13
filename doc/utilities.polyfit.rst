polyfit — Fit polynomial to list of X,Y data
============================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>polyfit (Nov87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>polyfit (Nov87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>polyfit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  polyfit -- fit a polynomial to sets of data
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  polyfit filelist order
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_"><B>filelist</B></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='\fBfilelist\fR'>
  <DD>File containing X,Y, SIGMAY triples to be fit. May be STDIN, or a list
  of file names. Note that the third list quantity is only required if
  <I>weighting</I> = instrumental.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><B>order</B></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='\fBorder\fR'>
  <DD>The order of the polynomial fit. (e.g. a parabolic fit has order 2)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = uniform'>
  <DD>The type of weighting for the fit. The choices are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>No weighting.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_instrumental">instrumental</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='instrumental' Line='instrumental'>
  <DD>The weight of each point is equal to 1. / SIGMAY ** 2.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_statistical">statistical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='statistical' Line='statistical'>
  <DD>The weight of each point is equal to 1. / Y.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><B>verbose</B> = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='\fBverbose\fR = no'>
  <DD>If <B>verbose</B> = yes, additional information about the fit is printed on
  the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><B>listdata</B> = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='\fBlistdata\fR = no'>
  <DD>If <B>listdata</B> = yes, the only output will be the calculated values for the
  X,Y pairs. This is useful as input to <I>graph</I>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A polynomial weighted fit of specified order is fit to the X,Y, SIGMAY data
  triples
  read from the input file, files, or STDIN. The resulting coefficients
  of the polynomial are printed on the first line of the standard output.
  The uncertainty in each coefficient is printed on the next line.
  These are listed as:
  <P>
  <BR>
  a0 a1 a2 a3 ...
  <BR>
  s0 s1 s2 s3 ...
  <P>
  <BR>
  where the polynomial has the form:
  <P>
  <BR>
  y = a0 + a1*x + a2*x**2 + a3*x**3 + ...
  <P>
  <BR>
  and the coefficients have uncertainties ("<TT>sigmas</TT>") s0 - sN.
  <P>
  If verbose is set to yes, the following additional information is
  listed: the resulting reduced chi-square, f-test, correlation coefficient,
  standard deviation of residuals, and number of items in the list.
  Also a tabular listing of each data element, X,Y, SIGMAY and the independent
  variable, Yc, as calculated according to the fit, is printed.
  <P>
  If listdata is set to yes, the only output which will appear will
  be the listing of X,Yc,Y, SIGMAY. This provides a list suitable as input to
  GRAPH or any other list oriented utility. Setting listdata to yes
  overrides the verbose option.
  <P>
  The routine REGRES from the library of routines written by Bevington is used 
  for the fit; see <B>Data Reduction and Error Analysis</B>, by Bevington.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  	cl&gt; polyfit STDIN 2
  <BR>
  	cl&gt; polyfit datafile 4 verbose+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The maximum number of data elements is currently limited to 1000
  X,Y,SIGMAY triples.  Also the system must be overdetermined.  That is, the
  number of data elements must exceed the order by at least 2.
  <P>
  Beware of data elements having large dynamic range.  The limitation
  of the machine exponent range can produce overflow and underflow
  arithmetic exceptions.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  curfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>