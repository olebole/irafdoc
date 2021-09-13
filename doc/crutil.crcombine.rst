crcombine — Combine multiple exposures to eliminate cosmic rays
===============================================================

**Package: crutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>crcombine (Apr98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.crutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>crcombine (Apr98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>crcombine</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  crcombine -- combine multiple exposures to eliminate cosmic rays
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  crcombine input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  See parameters for <B>imcombine</B>.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is a version of <B>imcombine</B>.  See the help for that task
  for a description of the parameters and algorithms.
  <P>
  For the purpose of removing cosmic rays the most useful options
  are the "<TT>crreject</TT>" algorithm and/or combining with a median.  Many other
  options may work as well.  The best use of this task depends on the
  number of images available.  If there are more than a few images the
  images should be combined with an "<TT>average</TT>" and using a rejection
  algorithm.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To combine two images using the gain and read noise parameters in
  the image header:
  <P>
  <PRE>
      cl&gt; crcombine obj012,obj013 abc gain=gain rdnoise=rdnoise 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>