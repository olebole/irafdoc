.. _sgidecode:

sgidecode: Decode an SGI format metacode file
=============================================

**Package: plot**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  sgidecode input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The input SGI metacode files.
  </dd>
  </dl>
  <dl>
  <dt><b>generic = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no' -->
  <dd>Ignore remaining parameters?
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print metacode in a verbose format?
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
  Task <i>sgidecode</i> is a debugging tool used to decode SGI metacode
  files.  The plotting instructions are decoded and printed in readable
  form on the standard output.  The input metacode can be read from one
  or more files or redirected from the standard input.
  </p>
  <p>
  Coordinates are printed in NDC units (0-1) by default.  When <b>gkiunits</b>
  = yes, coordinates are printed in gki units (0-32767).  Parameter
  <b>verbose</b> is currently not implemented.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Decode the metacode in file <span style="font-family: monospace;">"home$vdm.sgi"</span>.
  </p>
  <p>
      cl&gt; sgidecode home$vdm.sgi
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  gkidecode sgikern
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
