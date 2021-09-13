.. _deallocate:

deallocate — Deallocate a previously allocated device
=====================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  deallocate -- deallocate a device
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  deallocate device
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>device</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device to be deallocated.
  </DD>
  </DL>
  <DL>
  <DT><B>rewind = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rewind' Line='rewind = yes'>
  <DD>Rewind the device before deallocating?
  Ignored for devices other than magtape.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Deallocate a previously allocated device.  The CL will print an error
  message if one attempts to logout while devices are still allocated,
  but if <I>logout</I> is typed several times you will be allowed to logout
  with the devices still allocated.  The CL does not automatically
  deallocate devices upon logout.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Deallocate logical magtape drive B.
  <P>
  	cl&gt; dealloc mtb
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  allocate, devstatus, file dev$devices, dev$tapecap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
