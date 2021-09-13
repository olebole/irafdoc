quadsplit — Split quadformat data into individual single amplifier images
=========================================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>quadsplit (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>quadsplit (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>quadsplit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  quadsplit -- Split quadformat data into single amplifier images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  quadsplit input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Image name of <I>quadformat</I> image to be split.  This task does not
  allow a list of input names.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output root name to which the AMPLIST amplifier identifiers will be
  appended to form the split images.  If no output name is given then
  the input name is used as the root name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clobber">clobber = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber = yes'>
  <DD>Clobber any existing images?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Images in "<TT>quadformat</TT>" (see help topic <B>quadformat</B>) are separated
  into images containing data from only one amplifier.  The output images
  have a common root name and then an extension given by the amplifier
  labels in the AMPLIST keyword.  The output root name may be specified
  or default to the input name.
  <P>
  In addition to producing the individual images keywords, are added that
  are understood by the standard <B>ccdproc</B> task for single amplifier
  CCD reductions.
  <P>
  The task <B>quadjoin</B> may be used to rejoin images that were split
  by this task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To spit an image:
  <P>
  <PRE>
      qu&gt; quadsplit quad0072
      qu&gt; dir quad0072*
      quad0072.11.imh     quad0072.21.imh     quad0072.imh        
      quad0072.12.imh     quad0072.22.imh     
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, quadjoin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>