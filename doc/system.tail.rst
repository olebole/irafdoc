.. _tail:

tail: Print the last few lines of a file
========================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tail -- print the last few lines of the specified files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tail files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>A template specifying the files to be listed.
  </dd>
  </dl>
  <dl>
  <dt><b>nlines = 12</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 12' -->
  <dd>The number of lines to be printed.  If negative, the number
  of lines to be skipped, counting from the beginning of the file.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  For each file in the input file list, <i>tail</i> copies the last <i>nlines</i>
  of the file to the standard output.  If there is more than one file in the
  input file list, as one line header is printed before each file.
  If <tt>"nlines"</tt> is negative, then abs(nlines) lines are skipped, and the rest
  of the file is printed, i.e., the tail of the file is still printed, but
  the offset is measured from the beginning of the file rather than the end.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Prints the last 12 lines of each help file in the current directory.
  </p>
  <p>
  	cl&gt; tail *.hlp
  </p>
  <p>
  2. Print the last line of each help file.
  </p>
  <p>
  	cl&gt; tail *.hlp nl=1
  </p>
  <p>
  3. Prints the third through fifth lines of <tt>"file"</tt>.  The same thing
  might be done (at least conceptually) by <tt>"head file,nlines=5"</tt>
  piped into <tt>"tail ,nlines=3"</tt>.  However, <i>tail</i> does not work on STDIN.
  </p>
  <pre>
  	cl&gt; tail file nl=-2 | head nl=3
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  <i>Tail</i> does not presently work on standard input, and therefore cannot
  be used in pipes.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  head
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
