.. _airmass:

airmass — Compute the airmass at a given elevation above the horizon
====================================================================

**Package: astutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  airmass -- compute the airmass at a given elevation above horizon
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  airmass elevation
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>elevation</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='elevation' Line='elevation'>
  <DD>Elevation above horizon in either degrees or radians.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = 750.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 750.0'>
  <DD>Scale factor of the Earth's atmosphere.
  </DD>
  </DL>
  <DL>
  <DT><B>radians = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radians' Line='radians = no'>
  <DD>Input elevation in radians instead of degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>airmass</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass'>
  <DD>On output, contains the computed airmass.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Compute the airmass at an elevation of 30 degrees above the horizon
  <P>
  <PRE>
  	cl&gt; airmass 30
  	airmass 1.996 at an elevation of 30. degrees (0.5236 radians)
  	above horizon
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
