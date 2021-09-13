blink — Blink two frames
========================

**Package: iis**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>blink (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv.iis</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>blink (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>blink</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  blink -- Blink frames in the image display
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  blink frame1 frame2 [frame3 [frame4]]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_frame1">frame1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame1' Line='frame1'>
  <DD>First frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame2">frame2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame2' Line='frame2'>
  <DD>Second frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame3">frame3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame3' Line='frame3'>
  <DD>Third frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame4">frame4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame4' Line='frame4'>
  <DD>Fourth frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rate">rate = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rate' Line='rate = 1.'>
  <DD>Blink rate in seconds per frame.  May be any fraction of a second.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Two or more frames are alternately displayed on the image display monitor
  ("<TT>stdimage</TT>") at a specified rate per frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To blink two frames:
  <P>
  	cl&gt; blink 1 2
  <P>
  To blink three frames at a rate of 2 seconds per frame:
  <P>
  	cl&gt; blink 3 1 2 rate=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The blink rate is measured in
  software and, therefore, will not be exactly even in a time sharing
  environment.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>