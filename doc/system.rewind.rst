rewind — Rewind a device (magtape)
==================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rewind (Apr92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rewind (Apr92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rewind</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rewind -- rewind a previously allocated device
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rewind device
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_device">device</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device to be rewound.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_initcache">initcache = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='initcache' Line='initcache = yes'>
  <DD>Initialize the magtape device position cache for the device.  This causes
  the magtape i/o system to "<TT>forget</TT>" what it thinks it knows about things
  like the number of files on the tape, the amount of tape used, and so on.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Rewind logical tape drive a.
  <P>
  	cl&gt; rewind mta
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  allocate, deallocate, devstatus
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>