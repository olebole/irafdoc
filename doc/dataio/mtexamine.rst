.. _mtexamine:

mtexamine: Examine the structure of a magnetic tape
===================================================

**Package: dataio**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mtexamine tape_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>tape_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tape_file' Line='tape_file' -->
  <dd>Tape or disk file, e.g. <span style="font-family: monospace;">"mta1600[2]"</span>, <span style="font-family: monospace;">"mta1600"</span> or <span style="font-family: monospace;">"data"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>file_list = <span style="font-family: monospace;">"1-999"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list = "1-999"' -->
  <dd>List of tape file numbers or ranges delimited by commas, e.g. <span style="font-family: monospace;">"1-3,5-8"</span>.
  File_list is used only if no file number is given in tape_file.
  Files will be read in ascending order, regardless of the order of the list.
  Reading will terminate if EOT is reached, thus a list such as <span style="font-family: monospace;">"1-999"</span>
  may be used to read all the files on the tape. File_list is ignored is input
  is a single disk file.
  </dd>
  </dl>
  <dl>
  <dt><b>dump_records = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dump_records' Line='dump_records = no' -->
  <dd>Dump selected records?
  </dd>
  </dl>
  <dl>
  <dt><b>rec_list = <span style="font-family: monospace;">"1-999"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rec_list' Line='rec_list = "1-999"' -->
  <dd>List of tape record numbers or ranges to be dumped delimited by whitespace
  or commas e.g <span style="font-family: monospace;">"1-3,4"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>swapbytes = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='swapbytes' Line='swapbytes = no' -->
  <dd>Swap bytes?
  </dd>
  </dl>
  <dl>
  <dt><b>byte_chunk = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='byte_chunk' Line='byte_chunk = 1' -->
  <dd>The number of bytes which are considered as one output element.
  The maximum number of bytes permitted in byte_chunk is the number of
  bytes in a long integer on the host machine.
  </dd>
  </dl>
  <dl>
  <dt><b>output_format = <span style="font-family: monospace;">"o"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output_format' Line='output_format = "o"' -->
  <dd>Permitted types are character(c), octal(o), hexadecimal (x), decimal (d)
  or unsigned decimal (u).  Character dumps are only permitted for byte_chunk = 1.
  Unless decimal format is specified, the data are dumped as
  unsigned integers.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  By default mtexamine determines the record structure of all files
  on a magnetic tape or a single disk file.
  Selected files can be dumped by setting the file_list parameter.
  Selected records can be dumped by setting the dump_record switch
  and entering a record list. The user can select the byte chunk
  and the output format for the dump.
  </p>
  <p>
  Mtexamine can also be used to dump a single disk file. However the concept
  of a block is not well defined for disk files. Mtexamine defines a block
  to be one IRAF file io block which is usually some multiple of the machine
  block size.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Determine the record structure of a magnetic tape and send the result to
  the file tapedump.
  </p>
  <pre>
  	cl&gt; mtexamine mtb1600 &gt; tapedump
  </pre>
  <p>
  2. Dump the third tape file in octal bytes on the standard output.
  </p>
  <pre>
  	cl&gt; mtexamine mtb1600[3] du+
  </pre>
  <p>
  3. Dump the contents of the fifth record of the third tape file in ASCII
  characters on the standard output.
  </p>
  <pre>
  	cl&gt; mtexamine mtb1600[3] du+ re=5 ou=c
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The IRAF magtape i/o routines do not permit data beyond a double EOF
  to be accessed. Therefore mtexamine cannot be used to examine tapes with
  embedded double EOFs.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  rewind, allocate
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
