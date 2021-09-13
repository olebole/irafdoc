gkidecode — Decode metacode on the standard output
==================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gkidecode (Jan85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gkidecode (Jan85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gkidecode</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gkidecode -- decode one or more GKI metacode files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gkidecode input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input metacode, which can be read from a list of files or
  redirected from the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_generic">generic = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored when <B>generic</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, the elements of polylines, cell arrays, etc. will
  be printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gkiunits">gkiunits = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no'>
  <DD>By default, coordinates are printed in NDC rather than GKI units.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>gkidecode</B> is a debugging tool used to decode GKI metacode
  files.  The plotting instructions are decoded and printed in readable 
  form on the standard output.  The input metacode can be read from one
  or more files or redirected from the standard input.
  <P>
  If <B>verbose</B> = yes, elements of polyline and cell array calls are
  printed in addition to the default output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Decode the metacode instructions in file crtpict.mc in verbose mode.
  <P>
      cl&gt; gkidecode crtpict.mc verbose+
  <P>
  2. Print a shorter listing of the same file on the versatec.
  <P>
      cl&gt; gkidecode crtpict.mc | lprint dev=ver
  <P>
  3. Decode the third frame in metacode file "<TT>oned.mc</TT>".
  <P>
      cl&gt; gkiextract oned.mc 3 | gkidecode
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  stdgraph stdplot 
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>