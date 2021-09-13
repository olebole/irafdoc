.. _t2d:

t2d — Fast tape to disk copy
============================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  t2d -- copy files from tape to disk quickly
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  t2d input ofroot
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Tape file or device name, e.g. "<TT>mta1600[1]</TT>" or "<TT>mta</TT>"
  </DD>
  </DL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>List of tape file numbers or ranges delimited by commas, e.g. "<TT>1-3,5-8</TT>".
  `Files' is requested only if no file number is given in `input'.
  Files will be read in ascending order, regardless of the order of the list.
  Reading will terminate if EOT is reached, thus a list such as "<TT>1-999</TT>"
  may be used to read all the files on the tape.
  </DD>
  </DL>
  <DL>
  <DT><B>ofroot</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ofroot' Line='ofroot'>
  <DD>Root name to give output files.  A three digit sequence number will be appended
  to this root name for each file written if a file list is used.  If the file
  number is specifically given in the 'input' parameter, the output file will
  be named this root without an appended sequence number.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Flag to signal program that it should produce verbose output.  This means
  progress reports.
  </DD>
  </DL>
  <DL>
  <DT><B>errignore = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errignore' Line='errignore = yes'>
  <DD>Flag to signal program that tape records that give read errors should be
  considered to have zero length.  If set to 'no', error records are considered
  to be the same length as all the other records on the tape.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  T2d reads files from tape and puts them into disk files.  No formatting is
  performed so the bits and bytes are in the same order on disk as they were
  on tape.  The program uses double buffering and asynchronous i/o to speed
  things up as much as possible.
  <P>
  When read errors are encountered one of two things can happen.  Depending
  on the value of the parameter 'errignore', the error record is either
  thrown out or considered valid data.  If 'errignore' is 'no' when an error
  is found, the input buffer is validated to the most recent 'good record'
  length and written to disk.  If 'errignore' is 'yes' when an error is
  found, the input buffer is disposed of for that record.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To read the second image from mta at 1600 bpi, store the image into
  "<TT>image</TT>" and see verbose output the command would be:
  <P>
  <PRE>
  	cl&gt; t2d mta1600[2] image
  </PRE>
  <P>
  2. To read all the files on mtb at the default speed of 1600 bpi and put
  the disk files in root001, root002, root003, etc. and turn off verbose
  output, the command would be:
  <P>
  <PRE>
  	cl&gt; t2d mtb root v-
  </PRE>
  <P>
  The program will prompt the user and ask for the list of files to be read
  to which the response would be "<TT>1-999</TT>".
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  reblock
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
