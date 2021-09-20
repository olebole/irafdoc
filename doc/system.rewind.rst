.. _rewind:

rewind: Rewind a device (magtape)
=================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rewind -- rewind a previously allocated device
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rewind device
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>device</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device' -->
  <dd>The device to be rewound.
  </dd>
  </dl>
  <dl>
  <dt><b>initcache = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='initcache' Line='initcache = yes' -->
  <dd>Initialize the magtape device position cache for the device.  This causes
  the magtape i/o system to <span style="font-family: monospace;">"forget"</span> what it thinks it knows about things
  like the number of files on the tape, the amount of tape used, and so on.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Rewind</i> rewinds the specified device, which is most likely
  a magnetic tape, and which has been previously allocated to the user.
  </p>
  <p>
  By default <i>rewind</i> will initialize the device position cache.  When
  changing tapes, one should always either rewind or deallocate and reallocate
  the device, to force the magtape system to recompute the number of files
  on the tape and to ensure that the tape is left in a defined position.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Rewind logical tape drive a.
  </p>
  <p>
  	cl&gt; rewind mta
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  allocate, deallocate, devstatus
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
