.. _split:

split: Split a large file into smaller segments
===============================================

**Package: utilities**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  split input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The name of the input file (only a single file can be processed).
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The root name of the output files.
  </dd>
  </dl>
  <dl>
  <dt><b>nlines = 1000</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 1000' -->
  <dd>The maximum number of lines per output segment file, if the input file
  is a text file.
  </dd>
  </dl>
  <dl>
  <dt><b>nbytes = 16384</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nbytes' Line='nbytes = 16384' -->
  <dd>The maximum number of bytes per output segment file, if the input file
  is a binary file.
  </dd>
  </dl>
  <dl>
  <dt><b>maxfiles = 999</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='maxfiles' Line='maxfiles = 999' -->
  <dd>Maximum number of output files.  Used to determine the amount of zero
  padding needed for the filename extensions.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print the name and size of each output file as it is generated.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>split</i> task is used to break large files up into smaller segments,
  e.g., when it is necessary to deal with an unmanageably large file.
  Lacking any knowledge of the file structure, the segments are broken on
  arbitrarily located but equally spaced boundaries.  The segments may
  subsequently be reassembled into larger segments of the original file with
  <i>concatenate</i> or <i>copy</i> (with output redirection), or <i>split</i> may
  be applied again to break a large segment up into smaller segments without
  losing any information.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Split a large text file into segments, each of which is the default size.
  </p>
  <p>
  	cl&gt; split textfile seg
  </p>
  <p>
  2. Split a large <i>tar</i> format archive file (10240 byte records) up into
  a series of smaller files, each of which contains 10 records from the input
  tar file.
  </p>
  <p>
  	cl&gt; split big.arc seg nb=(10240*10)
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  very fast
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  concatenate, copy
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  -->
  
