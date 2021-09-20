.. _blink:

blink: Blink two frames
=======================

**Package: iis**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  blink -- Blink frames in the image display
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  blink frame1 frame2 [frame3 [frame4]]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>frame1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame1' Line='frame1' -->
  <dd>First frame in blink sequence.
  </dd>
  </dl>
  <dl>
  <dt><b>frame2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame2' Line='frame2' -->
  <dd>Second frame in blink sequence.
  </dd>
  </dl>
  <dl>
  <dt><b>frame3</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame3' Line='frame3' -->
  <dd>Third frame in blink sequence.
  </dd>
  </dl>
  <dl>
  <dt><b>frame4</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame4' Line='frame4' -->
  <dd>Fourth frame in blink sequence.
  </dd>
  </dl>
  <dl>
  <dt><b>rate = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rate' Line='rate = 1.' -->
  <dd>Blink rate in seconds per frame.  May be any fraction of a second.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Two or more frames are alternately displayed on the image display monitor
  (<span style="font-family: monospace;">"stdimage"</span>) at a specified rate per frame.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To blink two frames:
  </p>
  <p>
  	cl&gt; blink 1 2
  </p>
  <p>
  To blink three frames at a rate of 2 seconds per frame:
  </p>
  <p>
  	cl&gt; blink 3 1 2 rate=2
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The blink rate is measured in
  software and, therefore, will not be exactly even in a time sharing
  environment.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cv
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
