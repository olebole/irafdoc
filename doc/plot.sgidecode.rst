sgidecode — Decode an SGI format metacode file
==============================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>sgidecode (Jun86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>sgidecode (Jun86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>sgidecode</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  sgidecode -- decode simple graphics interface (SGI) metacode files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  sgidecode input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input SGI metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_generic">generic = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>Ignore remaining parameters?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print metacode in a verbose format?
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
  Task <I>sgidecode</I> is a debugging tool used to decode SGI metacode
  files.  The plotting instructions are decoded and printed in readable
  form on the standard output.  The input metacode can be read from one
  or more files or redirected from the standard input.
  <P>
  Coordinates are printed in NDC units (0-1) by default.  When <B>gkiunits</B>
  = yes, coordinates are printed in gki units (0-32767).  Parameter
  <B>verbose</B> is currently not implemented.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Decode the metacode in file "<TT>home$vdm.sgi</TT>".
  <P>
      cl&gt; sgidecode home$vdm.sgi
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkidecode sgikern
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>