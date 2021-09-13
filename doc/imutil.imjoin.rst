imjoin — Join images along a given dimension
============================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imjoin (Jan97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imjoin (Jan97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imjoin</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imjoin -- join images along a specified axis
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imjoin input output join_dimension 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be joined. The input images must have the
  same dimensionality and the same size along all dimensions but the join
  dimension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output combined image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_join_dimension">join_dimension</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='join_dimension' Line='join_dimension'>
  <DD>The image dimension along which the input images will be joined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pixtype">pixtype = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = ""'>
  <DD>The output image pixel type. The options are in order of increasing
  precedence "<TT>s</TT>" (short), "<TT>u</TT>" (unsigned short), "<TT>i</TT>" (integer),
  "<TT>l</TT>" (long integer), "<TT>r</TT>" (real), "<TT>d</TT>" (double), and "<TT>x</TT>" (complex).
  If the output image pixel type is not specified, it defaults to highest
  precedence input image datatype.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMJOIN creates a single output image <I>output</I>  by joining a list of input
  images <I>input</I> along a specified dimension <I>join_dimension</I>. IMJOIN
  can be used to create a single long 1-dimensional image from a list of shorter
  1-dimensional images, or to piece together a set of 3-dimensional images into
  larger 3-dimensional images along either the x, y, or z directions. The input
  images must all have the same number of dimensions and the same size along
  all dimensions by the join dimension. The output image inherits the
  world coordinates system if any of the first input image.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1.  Join a list of 1-dimensional spectra into a single long output spectrum.
  <P>
      cl&gt; imjoin @inlist output 1
  <P>
  2.  Join three datacubes along the z direction.
  <P>
      cl&gt; imjoin c1,c2,c3 c123 3
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  On some systems there are limitations on the number of input images that
  can be joined in a single execution of IMJOIN.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstack, imslice, imtile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>