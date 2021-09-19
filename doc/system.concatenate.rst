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
  <dd>The output file type is forced if this parameter is defined as <tt>"binary"</tt>
  or <tt>"text"</tt>.  If <tt>"out_type"</tt> does not begin with a <tt>"b"</tt> (or <tt>"B"</tt>), or a
  <tt>"t"</tt> (<tt>"T"</tt>), then the output type is either <tt>"text"</tt>, if the output file is
  the standard output, or is determined from the type of the first input file.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>If set to <tt>"yes"</tt>, <tt>"files"</tt> are appended to <tt>"output_file"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each file in the input file list is appended to the output file.
  If <tt>"output_file"</tt> is not the standard output, and if output redirection (<tt>"&gt;"</tt>)
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
  2. Write out files file1 and file2 into the new file <tt>"outfile"</tt>.
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
  4. Write out the contents of each of the files whose names are given in <tt>"list"</tt>,
  one per line, and append this data to <tt>"junk"</tt>.
  </p>
  <pre>
  	cl&gt; concatenate @list junk append+
  </pre>
  <p>
  5. Concatenation is also possible using <i>type</i>, e.g., the following
  command will append the contents of <tt>"file"</tt> to the file <tt>"outfile"</tt>, which will
  be created if it does not already exist.
  </p>
  <p>
  	cl&gt; type file &gt;&gt; outfile
  </p>
  <p>
  The redirect-append operator <tt>"&gt;&gt;"</tt> may be used to append the output of any
  task to a file.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Notes</h3>
  <!-- BeginSection: 'NOTES' -->
  <p>
  All input files should be of the same type, either all <tt>"text"</tt> or all
  <tt>"binary"</tt>.
  </p>
  <!-- EndSection:   'NOTES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  copy, type
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  -->
  
