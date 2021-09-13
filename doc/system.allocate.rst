.. _allocate:

allocate — Allocate a device, i.e., magtape drive mta, mtb, ...
===============================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  allocate -- allocate a device
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  allocate device
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>device</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device to be allocated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Allocate</B> allocates a device for exclusive access by one user, and
  readies the device for i/o by some other program.  A list of the devices
  available on the local system is maintained in the file <B>dev$tapecap</B>
  which needs to be configured by the site manager before it can be used.
  The status of given device may be obtained by calling <I>devstatus</I>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print a list of the allocatable devices.  The logical device names are
  given at the left in the output text; ignore the information to the right.
  <B>Note</B>: The dev$devices file should be configured by the site manager
  when new tape devices are installed.  Beginning with V2.9 it is used for
  informational purposes only.
  <PRE>
  <PRE>
  	cl&gt; type dev$devices
  	mta ...
  	mtb ...
  	mtc ...
  	iis ...
  </PRE>
  </PRE>
  <P>
  <P>
  2. Allocate a tape drive after checking its status.
  <P>
  <PRE>
  <PRE>
  	cl&gt; devstatus mtb
  	device mtb is not currently allocated
  	cl&gt;
  	cl&gt; allocate mtb
  </PRE>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  deallocate, devstatus
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
