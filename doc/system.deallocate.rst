deallocate — Deallocate a previously allocated device
=====================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>deallocate (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>deallocate (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>deallocate</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  deallocate -- deallocate a device
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  deallocate device
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_device">device</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device to be deallocated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rewind">rewind = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rewind' Line='rewind = yes'>
  <DD>Rewind the device before deallocating?
  Ignored for devices other than magtape.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Deallocate a previously allocated device.  The CL will print an error
  message if one attempts to logout while devices are still allocated,
  but if <I>logout</I> is typed several times you will be allowed to logout
  with the devices still allocated.  The CL does not automatically
  deallocate devices upon logout.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Deallocate logical magtape drive B.
  <P>
  	cl&gt; dealloc mtb
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  allocate, devstatus, file dev$devices, dev$tapecap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>