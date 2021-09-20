.. _bintxt:

bintxt: Convert a binary file to an IRAF text file
==================================================

**Package: dataio**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  bintxt binary_file text_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>binary_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file' -->
  <dd>Input file name or template,  e.g. <span style="font-family: monospace;">"file1"</span> or <span style="font-family: monospace;">"file*"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>text_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file' -->
  <dd>The output file name.  If multiple input files the filenumber will
  be concatenated onto the output file name.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages of actions performed?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Convert a binary file on disk to a text file on disk.
  </p>
  <p>
  	cl&gt; bintxt binary_file text_file
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  txtbin
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  -->
  
