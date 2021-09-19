.. _allocate:

allocate: Allocate a device, i.e., magtape drive mta, mtb, ...
==============================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  allocate -- allocate a device
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  allocate device
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>device</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device' -->
  <dd>The device to be allocated.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <b>Allocate</b> allocates a device for exclusive access by one user, and
  readies the device for i/o by some other program.  A list of the devices
  available on the local system is maintained in the file <b>dev$tapecap</b>
  which needs to be configured by the site manager before it can be used.
  The status of given device may be obtained by calling <i>devstatus</i>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print a list of the allocatable devices.  The logical device names are
  given at the left in the output text; ignore the information to the right.
  <b>Note</b>: The dev$devices file should be configured by the site manager
  when new tape devices are installed.  Beginning with V2.9 it is used for
  informational purposes only.
  </p>
  <pre>
  	cl&gt; type dev$devices
  	mta ...
  	mtb ...
  	mtc ...
  	iis ...
  </pre>
  <p>
  2. Allocate a tape drive after checking its status.
  </p>
  <pre>
  	cl&gt; devstatus mtb
  	device mtb is not currently allocated
  	cl&gt;
  	cl&gt; allocate mtb
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  deallocate, devstatus
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
