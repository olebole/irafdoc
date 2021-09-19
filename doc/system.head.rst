.. _head:

head: Print the first few lines of a text file
==============================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  head -- print the first few lines of the specified files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  head files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>The list of files to be dealt with, quite possibly given as
  a template, such a <tt>"image*"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>nlines = 12</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 12' -->
  <dd>The number of lines to be printed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Head</i> prints, on the standard output, the first <i>nlines</i> of each
  file that matches the given file list.  If the file list has more than one
  name in it, a short header precedes each listing.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the first 12 lines of each help file in the current directory.
  </p>
  <p>
  	cl&gt; head *.hlp
  </p>
  <p>
  2. Print the first line of each help file.
  </p>
  <p>
  	cl&gt; head *.hlp nl=1
  </p>
  <p>
  3. Print the most recently defined <i>set</i> environment definitions.
  </p>
  <p>
  	cl&gt; set | head
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  tail, page
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
