.. _quadscale:

quadscale: Scale sections by gain factors
=========================================

**Package: quadred**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  quadscale input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Input image in <b>quadformat</b> to be scaled.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output scaled image in <b>quadformat</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='gain11' Line='gain11 = 1., gain12 = 1., gain21 = 1., gain22 = 1.' -->
  <dd>Gain factors for each quadrant.
  </dd>
  </dl>
  <dl>
  <dt><b>operation = <span style="font-family: monospace;">"multiply"</span> (multiply|divide)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='operation' Line='operation = "multiply" (multiply|divide)' -->
  <dd>The operation to apply with the gains.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task multiplies or divides by gain factors for each amplifier in
  <b>quadformat</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To multiply by different gain factors.
  </p>
  <pre>
      qu&gt; quadscale quad0072 test gain11=1.2 gain12=1.3 gain21=1.4
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
