.. _mktags:

mktags: Tag all procedure declarations in a set of files
========================================================

**Package: softools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mktags -- tag all procedure declarations in a set of files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mktags
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files = <tt>"*.x"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files = "*.x"' -->
  <dd>The files to be tagged, e.g., <tt>"*.x"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>listing = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='listing' Line='listing = no' -->
  <dd>If this switch is enabled a sorted list of all procedures declared in the
  set of files will be printed on the standard output, giving the procedure
  name, line and file number, and procedure declaration on each output line.
  </dd>
  </dl>
  <dl>
  <dt><b>tags = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tags' Line='tags = yes' -->
  <dd>If this switch is enabled a <tt>"tags"</tt> file will be written in the current
  directory for use with the VI editor.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The named files are scanned for procedure declarations.  Each such declaration
  found is buffered internally.  When all files have been scanned the internal
  tag database is sorted and the output files are generated.  Two types of
  output are provided:
  </p>
  <dl>
  <dt><b></b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line=' ' -->
  <dd><dl>
  <dt><b>[1]</b></dt>
  <!-- Sec='DESCRIPTION' Level=1 Label='' Line='[1]' -->
  <dd>A summary of all procedures defined in the given set of files may be printed
  on the standard output.  This output may be used as a printed index to manually
  find procedures in the given file set.
  </dd>
  </dl>
  <dl>
  <dt><b>[2]</b></dt>
  <!-- Sec='DESCRIPTION' Level=1 Label='' Line='[2]' -->
  <dd>A <tt>"tags"</tt> format database file (a text file) may be written.  This file is
  read by the VI editor when a command of the form <tt>":ta tag"</tt> is entered.
  This command is used to edit procedures regardless of the file in which they
  reside.  For example, to edit procedure <tt>"maxmin"</tt>, enter command <tt>":ta maxmin"</tt>
  when in VI.
  </dd>
  </dl>
  </dd>
  </dl>
  <p>
  By default the operation of <i>mktags</i> is to silently update the tags
  database.  If a printed listing is desired the <i>listing</i> switch must
  be enabled.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  A fixed amount of storage is allocated internally and overflow will occur if
  there are too many tags (procedures) or if there is too much text (the string
  buffer will overflow).
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  -->
  
