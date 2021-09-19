.. _count:

count: Count the number of lines, words, characters in a text file
==================================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  count -- determine number of lines, words and characters in a file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  count files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>A template specifying the files to be examined.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  For each file, count determines the number of lines, words, and
  characters in the file.  A word is defined as a sequence of characters
  delimited by one or more blanks or tabs, or by the end of a line.
  If <i>count</i> is run on more than one file, each output line is identified
  by the file name, and a final output line gives the total number
  of lines, words, and characters in all files.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Count the number of lines, words and characters in all files in the
  current directory with the extensions <tt>".x"</tt> and <tt>".h"</tt>.
  </p>
  <p>
  	cl&gt; count *.[xh]
  </p>
  <p>
  2. Count the number of .x files in the current directory.
  </p>
  <p>
  	cl&gt; dir *.x op=1 | count
  </p>
  <p>
  3. Count the number of <i>set</i> environment definitions.
  </p>
  <p>
  	cl&gt; set | count
  </p>
  <p>
  4. Count the number of references to the READ function in all .x files in
  the current directory.
  </p>
  <p>
  	cl&gt; match <tt>"read#("</tt> *.x | count
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  directory
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
