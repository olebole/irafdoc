.. _txtbin:

txtbin — Convert an IRAF text file to a binary file
===================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  txtbin -- convert text files to binary files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  txtbin text_file binary_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>text_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file'>
  <DD>Input file name or template, e.g. "<TT>abc</TT>" or "<TT>abc.*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>binary_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file'>
  <DD>Output file name. If multiple input files the file_number will be
  added to the output file name.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>yes</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = "yes"'>
  <DD>Print messages about files processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a text file on disk to a binary file on disk.
  <P>
  	cl&gt; txtbin text_file binary_file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bintxt
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  >
  
