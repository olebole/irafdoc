quadscale — Scale sections by gain factors
==========================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>quadscale (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>quadscale (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>quadscale</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  quadscale -- Scale amplifier sections by separate gains
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  quadscale input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image in <B>quadformat</B> to be scaled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output scaled image in <B>quadformat</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gain11">gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain11' Line='gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.'>
  <DD>Gain factors for each quadrant.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_operation">operation = "<TT>multiply</TT>" (multiply|divide)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='operation' Line='operation = "multiply" (multiply|divide)'>
  <DD>The operation to apply with the gains.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task multiplies or divides by gain factors for each amplifier in
  <B>quadformat</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. To multiply by different gain factors.
  <P>
  <PRE>
      qu&gt; quadscale quad0072 test gain11=1.2 gain12=1.3 gain21=1.4
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>