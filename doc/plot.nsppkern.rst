nsppkern — Plot metacode on a NSPP (NCAR) plotter device
========================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>nsppkern (Apr89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>nsppkern (Apr89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>nsppkern</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  nsppkern -- draw metacode on an NSPP interfaced plotter device
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  nsppkern input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>nsppdefault</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "nsppdefault"'>
  <DD>The NSPP interfaced plotting device output is to be directed to.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_generic">generic = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored when <B>generic</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_debug">debug = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no'>
  <DD>If <B>debug</B> = yes, the graphics instructions are decoded and printed
  during processing.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, the elements of polylines, cell arrays, etc. will
  be printed in debug mode.
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
  Task <I>nsppkern</I> translates metacode and draws it on a plotting
  device.
  Input is GKI metacode, which can be read from one or more binary
  files or redirected from the standard input.
  <P>
  If <B>debug</B> is set to yes, the plotting instructions are printed in
  readable form during processing.
  If <B>verbose</B> = yes, elements of polyline and cell array calls are
  printed in addition to the default debug output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract the fourth frame from metacode file "<TT>oned.mc</TT>" and plot it.
  <P>
      cl&gt; gkiextract oned.mc 4 | nsppkern
  <P>
  2. Plot metacode frame "<TT>contour.demo</TT>" in debug mode, so the plotting
  instructions can be read as they are processed.
  <P>
      cl&gt; nsppkern contour.demo debug+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  stdgraph, sgikern, calcomp
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>