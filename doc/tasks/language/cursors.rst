.. _cursors:

cursors: Graphics and image display cursors
===========================================

**Package: language**

.. raw:: html

  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Despite the fact that the CL has graphics and image cursor access capabilities,
  there is no guarantee that one can access the cursor on a particular device.
  A <i>graphcap</i> entry for the device is also required, as is a graphics kernel
  if the device is not a conventional graphics terminal (e.g., an image display).
  If all of these pieces are not in place, the system will abort the cursor
  read, complaining that it cannot find a termcap or graphcap entry for the
  device, or that it cannot open a connected subprocess (the subkernel).
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  The GIO Reference Manual
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'Introduction' 'Overview' 'Invoking Cursor Mode' 'Cursor Mode Help' 'Cursor Mode Commands and Options' 'Advanced Usage' 'The Frame Buffer' 'Filling and Writing the Frame Buffer' 'Moving the Cursor and Modifying the Display Area' 'Reporting and Marking the Cursor Position' 'Annotating Plots' 'Hardcopy Snapshots' 'Alternate Cursor Input' 'Examining the Status of the Graphics System' 'Initializing the Graphics System' 'BUGS' 'SEE ALSO'  -->
  
