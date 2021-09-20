.. _concatenate:

concatenate: Concatenate a list of files
========================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  concatenate -- connect files together into one big file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  concatenate files [output_file]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>The list of input files.  The standard input, STDIN, may be specified to
  interactively enter a few lines of text rather than read from a disk file.
  All input files should be of the same type (binary or text).
  </dd>
  </dl>
  <dl>
  <dt><b>output_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output_file' Line='output_file' -->
  <dd>The name of the output file.  If no file is explicitly specified the
  standard output (STDOUT) is used.
  </dd>
  </dl>
  <dl>
  <dt><b>out_type = in_type</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = in_type' -->
  <dd>The output file type is forced if this parameter is defined as <span style="font-family: monospace;">"binary"</span>
  or <span style="font-family: monospace;">"text"</span>.  If <span style="font-family: monospace;">"out_type"</span> does not begin with a <span style="font-family: monospace;">"b"</span> (or <span style="font-family: monospace;">"B"</span>), or a
  <span style="font-family: monospace;">"t"</span> (<span style="font-family: monospace;">"T"</span>), then the output type is either <span style="font-family: monospace;">"text"</span>, if the output file is
  the standard output, or is determined from the type of the first input file.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>If set to <span style="font-family: monospace;">"yes"</span>, <span style="font-family: monospace;">"files"</span> are appended to <span style="font-family: monospace;">"output_file"</span>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each file in the input file list is appended to the output file.
  If <span style="font-family: monospace;">"output_file"</span> is not the standard output, and if output redirection (<span style="font-family: monospace;">"&gt;"</span>)
  was not specified on the command line, the resulting stream of data is placed
  in a file.  The input can be STDIN, which makes for an easy way to enter a
  few lines of text into a file (but <i>type</i> is usually more convenient).
  If entering data via the standard input, type the end of file character,
  e.g., &lt;ctrl/z&gt;, to terminate the input sequence.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Write out file1, followed by file2, to the terminal screen.  Note that
  there must be no space after the comma.
  </p>
  <pre>
  	cl&gt; concatenate file1,file2
  </pre>
  <p>
  2. Write out files file1 and file2 into the new file <span style="font-family: monospace;">"outfile"</span>.
  </p>
  <pre>
  	cl&gt; concatenate file1,file2 outfile
  </pre>
  <p>
  3. Copy what you type (up to the end-of-file character) into the file junk.
  </p>
  <pre>
  	cl&gt; concatenate STDIN junk
  </pre>
  <p>
  4. Write out the contents of each of the files whose names are given in <span style="font-family: monospace;">"list"</span>,
  one per line, and append this data to <span style="font-family: monospace;">"junk"</span>.
  </p>
  <pre>
  	cl&gt; concatenate @list junk append+
  </pre>
  <p>
  5. Concatenation is also possible using <i>type</i>, e.g., the following
  command will append the contents of <span style="font-family: monospace;">"file"</span> to the file <span style="font-family: monospace;">"outfile"</span>, which will
  be created if it does not already exist.
  </p>
  <p>
  	cl&gt; type file &gt;&gt; outfile
  </p>
  <p>
  The redirect-append operator <span style="font-family: monospace;">"&gt;&gt;"</span> may be used to append the output of any
  task to a file.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Notes</h3>
  <!-- BeginSection: 'NOTES' -->
  <p>
  All input files should be of the same type, either all <span style="font-family: monospace;">"text"</span> or all
  <span style="font-family: monospace;">"binary"</span>.
  </p>
  <!-- EndSection:   'NOTES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  copy, type
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  -->
  
