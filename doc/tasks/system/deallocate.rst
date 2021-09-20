.. _deallocate:

deallocate: Deallocate a previously allocated device
====================================================

**Package: system**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  deallocate device
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>device</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device' -->
  <dd>The device to be deallocated.
  </dd>
  </dl>
  <dl>
  <dt><b>rewind = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rewind' Line='rewind = yes' -->
  <dd>Rewind the device before deallocating?
  Ignored for devices other than magtape.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Deallocate a previously allocated device.  The CL will print an error
  message if one attempts to logout while devices are still allocated,
  but if <i>logout</i> is typed several times you will be allowed to logout
  with the devices still allocated.  The CL does not automatically
  deallocate devices upon logout.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Deallocate logical magtape drive B.
  </p>
  <p>
  	cl&gt; dealloc mtb
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  allocate, devstatus, file dev$devices, dev$tapecap
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
