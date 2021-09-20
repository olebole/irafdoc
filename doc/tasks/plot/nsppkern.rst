.. _nsppkern:

nsppkern: Plot metacode on a NSPP (NCAR) plotter device
=======================================================

**Package: plot**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  nsppkern input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input metacode files.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <span style="font-family: monospace;">"nsppdefault"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "nsppdefault"' -->
  <dd>The NSPP interfaced plotting device output is to be directed to.
  </dd>
  </dl>
  <dl>
  <dt><b>generic = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no' -->
  <dd>The remaining parameters are ignored when <b>generic</b> = yes.
  </dd>
  </dl>
  <dl>
  <dt><b>debug = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no' -->
  <dd>If <b>debug</b> = yes, the graphics instructions are decoded and printed
  during processing.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If <b>verbose</b> = yes, the elements of polylines, cell arrays, etc. will
  be printed in debug mode.
  </dd>
  </dl>
  <dl>
  <dt><b>gkiunits = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no' -->
  <dd>By default, coordinates are printed in NDC rather than GKI units.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>nsppkern</i> translates metacode and draws it on a plotting
  device.
  Input is GKI metacode, which can be read from one or more binary
  files or redirected from the standard input.
  </p>
  <p>
  If <b>debug</b> is set to yes, the plotting instructions are printed in
  readable form during processing.
  If <b>verbose</b> = yes, elements of polyline and cell array calls are
  printed in addition to the default debug output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Extract the fourth frame from metacode file <span style="font-family: monospace;">"oned.mc"</span> and plot it.
  </p>
  <p>
      cl&gt; gkiextract oned.mc 4 | nsppkern
  </p>
  <p>
  2. Plot metacode frame <span style="font-family: monospace;">"contour.demo"</span> in debug mode, so the plotting
  instructions can be read as they are processed.
  </p>
  <p>
      cl&gt; nsppkern contour.demo debug+
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  stdgraph, sgikern, calcomp
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
