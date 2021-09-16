.. _logout:

logout — Log out of the CL
==========================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  logout -- log out of the CL
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  logout
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Logout</I> causes the CL to shut itself down, regardless of how many
  packages may currently be active.  The only way to shut the CL down without
  killing it is to use <I>logout</I>; <I>bye</I> is not allowed to shut the
  CL down, since it would be too easy to enter it by accident (and it takes
  a while to log back in).
  <P>
  An error message will be printed if one attempts to log out of the CL while
  a device is still allocated.  The device should be deallocated and the
  <I>logout</I> repeated, else type <I>logout</I> several times and you will
  be permitted to logout with the device still allocated.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  1. Logout of the CL.
  <P>
  	cl&gt; logo
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  deallocate, bye
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  >
  
