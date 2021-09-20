.. _logout:

logout: Log out of the CL
=========================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  logout
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Logout</i> causes the CL to shut itself down, regardless of how many
  packages may currently be active.  The only way to shut the CL down without
  killing it is to use <i>logout</i>; <i>bye</i> is not allowed to shut the
  CL down, since it would be too easy to enter it by accident (and it takes
  a while to log back in).
  </p>
  <p>
  An error message will be printed if one attempts to log out of the CL while
  a device is still allocated.  The device should be deallocated and the
  <i>logout</i> repeated, else type <i>logout</i> several times and you will
  be permitted to logout with the device still allocated.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  1. Logout of the CL.
  </p>
  <p>
  	cl&gt; logo
  </p>
  <!-- EndSection:   'EXAMPLE' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  deallocate, bye
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  -->
  
