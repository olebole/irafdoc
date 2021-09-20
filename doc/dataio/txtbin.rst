.. _txtbin:

txtbin: Convert an IRAF text file to a binary file
==================================================

**Package: dataio**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txtbin text_file binary_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>text_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file' -->
  <dd>Input file name or template, e.g. <span style="font-family: monospace;">"abc"</span> or <span style="font-family: monospace;">"abc.*"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>binary_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file' -->
  <dd>Output file name. If multiple input files the file_number will be
  added to the output file name.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = <span style="font-family: monospace;">"yes"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = "yes"' -->
  <dd>Print messages about files processed?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Convert a text file on disk to a binary file on disk.
  </p>
  <p>
  	cl&gt; txtbin text_file binary_file
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  bintxt
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  -->
  
