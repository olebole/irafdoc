.. _protect:

protect — Protect a file from deletion
======================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  protect -- protect files from deletion
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  protect files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the file or files to be protected.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Protect</I> asserts protection from deletion for the specified files.
  A protected file can be deleted only by first "<TT>unprotecting</TT>" it.
  File protection is preserved when a file is copied or renamed,
  even when copied or renamed to a remote network node,
  but may be lost when a file is backed up on tape and later restored
  (depending upon what utility one uses).  Note that imagefiles are
  automatically protected to prevent accidental deletion of the header
  file, leaving a "<TT>zombie</TT>" pixel file somewhere on disk.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Protect the file "<TT>paper.ms</TT>" from deletion, accidental or otherwise.
  <P>
  	cl&gt; protect paper.ms
  <P>
  2. Protect all the "<TT>.ms</TT>" files from deletion.
  <P>
  	cl&gt; protect *.ms
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  unprotect, delete
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
