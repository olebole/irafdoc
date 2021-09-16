.. _quadscale:

quadscale — Scale sections by gain factors
==========================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  quadscale -- Scale amplifier sections by separate gains
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  quadscale input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image in <B>quadformat</B> to be scaled.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output scaled image in <B>quadformat</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain11' Line='gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.'>
  <DD>Gain factors for each quadrant.
  </DD>
  </DL>
  <DL>
  <DT><B>operation = "<TT>multiply</TT>" (multiply|divide)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='operation' Line='operation = "multiply" (multiply|divide)'>
  <DD>The operation to apply with the gains.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task multiplies or divides by gain factors for each amplifier in
  <B>quadformat</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
