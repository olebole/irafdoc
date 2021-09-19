.. _entab:

entab: Replace blanks with tabs and blanks
==========================================

**Package: utilities**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  entab -- replaces blanks by tabs and blanks
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  entab files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>Template specifying the files to be processed, e.g. <tt>"file"</tt> or <tt>"file*"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>tablist = <tt>"9 +8"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"' -->
  <dd>String containing a list of tabstops separated by blanks or commas.
  A two element string of the form <tt>"m +n"</tt> will set
  tabstops in every n columns beginning in column m.
  A null string defaults to <tt>"9 +8"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  Convert the file <tt>"prog.c"</tt>, written using full tabstop indents, to
  an equivalent file with an initial indent of one full tabstop, 
  with 4 space indents thereafter.
  </p>
  <pre>
  	cl&gt; detab prog.c tab='9 +4' | entab &gt; temp
  	cl&gt; delete prog.c
  	cl&gt; rename temp prog.c
  </pre>
  
  <!-- EndSection:    'EXAMPLE' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  -->
  
