.. _protect:

protect: Protect a file from deletion
=====================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  protect -- protect files from deletion
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  protect files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>A template specifying the file or files to be protected.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Protect</i> asserts protection from deletion for the specified files.
  A protected file can be deleted only by first <tt>"unprotecting"</tt> it.
  File protection is preserved when a file is copied or renamed,
  even when copied or renamed to a remote network node,
  but may be lost when a file is backed up on tape and later restored
  (depending upon what utility one uses).  Note that imagefiles are
  automatically protected to prevent accidental deletion of the header
  file, leaving a <tt>"zombie"</tt> pixel file somewhere on disk.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Protect the file <tt>"paper.ms"</tt> from deletion, accidental or otherwise.
  </p>
  <p>
  	cl&gt; protect paper.ms
  </p>
  <p>
  2. Protect all the <tt>".ms"</tt> files from deletion.
  </p>
  <p>
  	cl&gt; protect *.ms
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  unprotect, delete
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
