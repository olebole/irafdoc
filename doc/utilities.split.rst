.. _split:

split — Split a large file into smaller segments
================================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  split -- split a large file into smaller segments
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  split input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The name of the input file (only a single file can be processed).
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The root name of the output files.
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = 1000</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 1000'>
  <DD>The maximum number of lines per output segment file, if the input file
  is a text file.
  </DD>
  </DL>
  <DL>
  <DT><B>nbytes = 16384</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbytes' Line='nbytes = 16384'>
  <DD>The maximum number of bytes per output segment file, if the input file
  is a binary file.
  </DD>
  </DL>
  <DL>
  <DT><B>maxfiles = 999</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfiles' Line='maxfiles = 999'>
  <DD>Maximum number of output files.  Used to determine the amount of zero
  padding needed for the filename extensions.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the name and size of each output file as it is generated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>split</I> task is used to break large files up into smaller segments,
  e.g., when it is necessary to deal with an unmanageably large file.
  Lacking any knowledge of the file structure, the segments are broken on
  arbitrarily located but equally spaced boundaries.  The segments may
  subsequently be reassembled into larger segments of the original file with
  <I>concatenate</I> or <I>copy</I> (with output redirection), or <I>split</I> may
  be applied again to break a large segment up into smaller segments without
  losing any information.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Split a large text file into segments, each of which is the default size.
  <P>
  	cl&gt; split textfile seg
  <P>
  2. Split a large <I>tar</I> format archive file (10240 byte records) up into
  a series of smaller files, each of which contains 10 records from the input
  tar file.
  <P>
  	cl&gt; split big.arc seg nb=(10240*10)
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  very fast
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  concatenate, copy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
