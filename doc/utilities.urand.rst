urand — Uniform random number generator
=======================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>urand (Mar84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>urand (Mar84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>urand</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  urand -- uniform random number generator
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  urand nlines ncols
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_nlines">nlines</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines'>
  <DD>The number of lines of output to be generated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols'>
  <DD>The number of random numbers per output line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ndigits">ndigits = 4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ndigits' Line='ndigits = 4'>
  <DD>Number of digits of precision in each random number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale_factor">scale_factor = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale_factor' Line='scale_factor = 1.0'>
  <DD>Factor by which the numbers are to be scaled (multiplied).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_seed">seed = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Seed for the random number generator.  If the value is "<TT>INDEF</TT>" then
  the clock time (integer seconds since 1980) is used as the seed
  value giving different random numbers for different executions.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The system random number generator is called to generate a sequence of
  random numbers in list form.  By default, the random numbers will
  be uniformly distributed over the range 0 to 1.  The number of lines
  of output, number of columns (random numbers) per line, and number of
  significant digits in each number may all be set by the caller.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Generate a sequence of 100 random numbers and graph them on the graphics
  terminal in point plot mode.  Autoscaling is turned off so that the plot
  will be scaled to the rand 0-1 (the <B>graph</B> defaults) in both axes.
  <P>
  	cl&gt; urand 100 2 | graph po+ xa- ya-
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>