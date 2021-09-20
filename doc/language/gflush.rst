.. _gflush:

gflush: Flush any buffered graphics output
==========================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  gflush
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  None.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Output to graphics plotter devices is normally buffered and then disposed
  of to the plotter as a larger job, to increase the efficiency of the
  graphics system.  The <i>gflush</i> task disposes of any buffered graphics
  output and also initializes the graphics subsystem.  The cursor mode frame
  buffer is cleared, any connected graphics subkernels are disconnected,
  and the memory and file descriptors used by the graphics subsystem are
  freed.  A <i>gflush</i> occurs automatically upon logout from the CL.
  </p>
  <p>
  The number of frames (plots) the graphics system will buffer for a device
  is controlled by the MF (multi-frame) parameter in the <i>graphcap</i> entry
  for the device.  When the multi-frame count is reached the buffered output
  is automatically disposed of to the device.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Flush any graphics output and initialize the graphics system.
  </p>
  <p>
  	cl&gt; gflush
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cursor, stdplot
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
