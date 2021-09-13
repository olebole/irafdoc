.. _blink:

blink — Blink two frames
========================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  blink -- Blink frames in the image display
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  blink frame1 frame2 [frame3 [frame4]]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>frame1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame1' Line='frame1'>
  <DD>First frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B>frame2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame2' Line='frame2'>
  <DD>Second frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B>frame3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame3' Line='frame3'>
  <DD>Third frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B>frame4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame4' Line='frame4'>
  <DD>Fourth frame in blink sequence.
  </DD>
  </DL>
  <DL>
  <DT><B>rate = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rate' Line='rate = 1.'>
  <DD>Blink rate in seconds per frame.  May be any fraction of a second.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Two or more frames are alternately displayed on the image display monitor
  ("<TT>stdimage</TT>") at a specified rate per frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The blink rate is measured in
  software and, therefore, will not be exactly even in a time sharing
  environment.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
