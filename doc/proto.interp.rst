interp — Interpolate for a value in a table of X,Y pairs
========================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>interp (Jan85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>interp (Jan85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>interp</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  interp -- compute an interpolated value from a table of x,y pairs
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  interp tbl_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_tbl_file">tbl_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tbl_file' Line='tbl_file'>
  <DD>Text file containing X,Y pairs comprising the table.
  The pairs must be in either ascending or descending order.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_curve_gen">curve_gen = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='curve_gen' Line='curve_gen = no'>
  <DD>If set to no, x-values are read from the file(s) specified by the parameter
  "<TT>input</TT>". If set to yes, the parameters x1, x2, and dx are used to create
  a list of new x,y pairs interpolated at x1, x1+dx, ... x2.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_input">input = STDIN</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input = STDIN'>
  <DD>File(s) containing x-values for the interpolation
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_int_mode">int_mode = 'linear'</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='int_mode' Line='int_mode = 'linear''>
  <DD>The interpolation mode may be either 'linear' or 'spline'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x1">x1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1'>
  <DD>The starting x-value for generating a series of new x,y pairs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x2">x2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2'>
  <DD>The ending x-value of the generated series of pairs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dx">dx</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dx' Line='dx'>
  <DD>The difference by which the x-values are incremented during the
  series generation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The pairs of X,Y values are read from the tbl_file. There must be
  at least 1 pair in the file. The table is then used to interpolate
  or extrapolate new y-values for given x-values. The x-values may come
  from a file including STDIN (if curve_gen=no), or they may be
  internally generated (if curve_gen=yes) to produce a finely sampled
  version of the table. This may be useful for plotting a smooth curve
  through a series of points.
  <P>
  The table X,Y values must be in a monotonic order, either ascending
  or descending. No restriction is made on spacing.
  <P>
  If only one point is present in the table, all returned interpolated
  values will have the value at that point. If only two points are
  present, linear interpolation (or extrapolation) will be used.
  If additional points are present, an obscure but reliable algorithm
  is used to interpolate (or extrapolate).
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. The following command reads the X,Y table from file testdata and waits for
     x-values from the terminal.
  <P>
  <PRE>
      cl&gt; interp testdata STDIN
  </PRE>
  <P>
  <P>
  2. The following command generates points to plot (by piping to graph) in the
     range from x=10 to x=20 at intervals of 0.1 (10.0, 10.1 ... 19.9, 20.0).
  <P>
  <PRE>
      cl&gt; interp testdata curve_gen=yes x1=10 x2=20 dx=.1 | graph
  </PRE>
  <P>
  3. The curve will be displayed and the original points from the table
     may be overlaid by:
  <P>
  <PRE>
      cl&gt; graph testdata pointmode=yes append=yes
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If a blank (null) table filename is entered, a floating divide error
  occurs.
  <P>
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
  </BODY>
  </HTML>