.. _bintxt:

bintxt — Convert a binary file to an IRAF text file
===================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  bintxt -- Convert binary files containing only text to text files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bintxt binary_file text_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>binary_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file'>
  <DD>Input file name or template,  e.g. "<TT>file1</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>text_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file'>
  <DD>The output file name.  If multiple input files the filenumber will
  be concatenated onto the output file name.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages of actions performed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a binary file on disk to a text file on disk.
  <P>
  	cl&gt; bintxt binary_file text_file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  txtbin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  >
  
