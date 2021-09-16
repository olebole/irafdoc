.. _gflush:

gflush — Flush any buffered graphics output
===========================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gflush -- flush any buffered graphics output
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gflush
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  None.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Output to graphics plotter devices is normally buffered and then disposed
  of to the plotter as a larger job, to increase the efficiency of the
  graphics system.  The <I>gflush</I> task disposes of any buffered graphics
  output and also initializes the graphics subsystem.  The cursor mode frame
  buffer is cleared, any connected graphics subkernels are disconnected,
  and the memory and file descriptors used by the graphics subsystem are
  freed.  A <I>gflush</I> occurs automatically upon logout from the CL.
  <P>
  The number of frames (plots) the graphics system will buffer for a device
  is controlled by the MF (multi-frame) parameter in the <I>graphcap</I> entry
  for the device.  When the multi-frame count is reached the buffered output
  is automatically disposed of to the device.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Flush any graphics output and initialize the graphics system.
  <P>
  	cl&gt; gflush
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cursor, stdplot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
