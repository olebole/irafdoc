.. _rewind:

rewind — Rewind a device (magtape)
==================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rewind -- rewind a previously allocated device
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rewind device
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>device</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device to be rewound.
  </DD>
  </DL>
  <DL>
  <DT><B>initcache = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='initcache' Line='initcache = yes'>
  <DD>Initialize the magtape device position cache for the device.  This causes
  the magtape i/o system to "<TT>forget</TT>" what it thinks it knows about things
  like the number of files on the tape, the amount of tape used, and so on.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Rewind</I> rewinds the specified device, which is most likely
  a magnetic tape, and which has been previously allocated to the user.
  <P>
  By default <I>rewind</I> will initialize the device position cache.  When
  changing tapes, one should always either rewind or deallocate and reallocate
  the device, to force the magtape system to recompute the number of files
  on the tape and to ensure that the tape is left in a defined position.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Rewind logical tape drive a.
  <P>
  	cl&gt; rewind mta
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  allocate, deallocate, devstatus
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
