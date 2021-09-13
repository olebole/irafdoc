quadjoin — Rejoin single amplifier images produced by quadsplit
===============================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>quadjoin (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>quadjoin (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>quadjoin</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  quadjoin -- Split quadformat data into single amplifier images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  quadjoin input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Root name of images to be joined.  Extensions based on the AMPLIST
  keyword are applied to the root name.  This task does not
  allow a list of input root names.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output image name.  If one is not given then the input root name is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_delete">delete = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>Delete subimages on completion?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Images in split "<TT>quadformat</TT>" (see help topic <B>quadformat</B> and
  <B>quadsplit</B>) are rejoined into "<TT>quadformat</TT>".  The input images
  have a common root name and then an extension given by the amplifier
  labels in the AMPLIST keyword are added.  The output name may be specified
  or the input root name may be used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To join a split set of images:
  <P>
  <PRE>
      qu&gt; dir quad0072*
      quad0072.11.imh     quad0072.21.imh
      quad0072.12.imh     quad0072.22.imh     
      qu&gt; quadjoin quad0072 delete+
      qu&gt; dir quad0072*
      quad0072.imh
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, quadsplit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>