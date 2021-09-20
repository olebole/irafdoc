.. _t2d:

t2d: Fast tape to disk copy
===========================

**Package: dataio**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  t2d input ofroot
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Tape file or device name, e.g. <span style="font-family: monospace;">"mta1600[1]"</span> or <span style="font-family: monospace;">"mta"</span>
  </dd>
  </dl>
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>List of tape file numbers or ranges delimited by commas, e.g. <span style="font-family: monospace;">"1-3,5-8"</span>.
  `Files' is requested only if no file number is given in `input'.
  Files will be read in ascending order, regardless of the order of the list.
  Reading will terminate if EOT is reached, thus a list such as <span style="font-family: monospace;">"1-999"</span>
  may be used to read all the files on the tape.
  </dd>
  </dl>
  <dl>
  <dt><b>ofroot</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ofroot' Line='ofroot' -->
  <dd>Root name to give output files.  A three digit sequence number will be appended
  to this root name for each file written if a file list is used.  If the file
  number is specifically given in the 'input' parameter, the output file will
  be named this root without an appended sequence number.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Flag to signal program that it should produce verbose output.  This means
  progress reports.
  </dd>
  </dl>
  <dl>
  <dt><b>errignore = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='errignore' Line='errignore = yes' -->
  <dd>Flag to signal program that tape records that give read errors should be
  considered to have zero length.  If set to 'no', error records are considered
  to be the same length as all the other records on the tape.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  T2d reads files from tape and puts them into disk files.  No formatting is
  performed so the bits and bytes are in the same order on disk as they were
  on tape.  The program uses double buffering and asynchronous i/o to speed
  things up as much as possible.
  </p>
  <p>
  When read errors are encountered one of two things can happen.  Depending
  on the value of the parameter 'errignore', the error record is either
  thrown out or considered valid data.  If 'errignore' is 'no' when an error
  is found, the input buffer is validated to the most recent 'good record'
  length and written to disk.  If 'errignore' is 'yes' when an error is
  found, the input buffer is disposed of for that record.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To read the second image from mta at 1600 bpi, store the image into
  <span style="font-family: monospace;">"image"</span> and see verbose output the command would be:
  </p>
  <pre>
  	cl&gt; t2d mta1600[2] image
  </pre>
  <p>
  2. To read all the files on mtb at the default speed of 1600 bpi and put
  the disk files in root001, root002, root003, etc. and turn off verbose
  output, the command would be:
  </p>
  <pre>
  	cl&gt; t2d mtb root v-
  </pre>
  <p>
  The program will prompt the user and ask for the list of files to be read
  to which the response would be <span style="font-family: monospace;">"1-999"</span>.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  reblock
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
