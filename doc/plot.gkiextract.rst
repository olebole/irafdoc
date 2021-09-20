.. _gkiextract:

gkiextract: Extract individual frames from metacode file
========================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  gkiextract -- extract individual frames from a GKI metacode file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  gkiextract input frames
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The metacode source file or files.
  </dd>
  </dl>
  <dl>
  <dt><b>frames</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frames' Line='frames' -->
  <dd>List of frames to be extracted from each metacode file.
  </dd>
  </dl>
  <dl>
  <dt><b>verify = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no' -->
  <dd>Verify each frame before extraction?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <b>gkiextract</b> will extract individual frames from a metacode file, 
  writing a binary metacode output stream which can be piped to a kernel
  for plotting or redirected to produce a new metacode file.  
  Parameter <i>frames</i> specifies a list of frames to be
  extracted from each input file.  If <i>verify</i>  = yes,
  a <b>gkidir</b> style line will be printed for each specified frame 
  and the user will be queried whether or not to extract the frame.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Extract frames 1, 3 and 5 from metacode file <span style="font-family: monospace;">"mc_file"</span> and
  plot them on the device <span style="font-family: monospace;">"vup"</span>:
  </p>
  <p>
      cl&gt; gkiextract mc_file 1,3,5 | stdplot dev=vup
  </p>
  <p>
  2. Print a directory of the first 99 frames in <span style="font-family: monospace;">"mc_file"</span>, extract
  those files requested by the user and write them to file <span style="font-family: monospace;">"new_mc_file"</span>.
  </p>
  <p>
      cl&gt; gkiextract mc_file 1-99 ver+ &gt; new_mc_file
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  A maximum of 8192 plots in a single metacode file may be processed.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  gkidir
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
