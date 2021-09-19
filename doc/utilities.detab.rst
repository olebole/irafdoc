.. _detab:

detab: Replace tabs with tabs and blanks
========================================

**Package: utilities**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  detab -- remove tab characters from a file or files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  detab files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>Template specifying files to be processed e.g. <tt>"file1"</tt> or <tt>"file*"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>tablist = <tt>"9 +8"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"' -->
  <dd>String containing a list of tabstops separated by blanks or commas.
  Alternatively a two element string of the form m +n will set
  tabstops every n columns beginning in column m.  A null string will
  default to <tt>"9 +8"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  Remove the tabs from file <tt>"cubspl.f"</tt>, using the default tab stops.
  </p>
  <pre>
  	cl&gt; detab cubspl.f &gt; temp
  	cl&gt; delete cubspl.f
  	cl&gt; rename temp cubspl.f
  </pre>
  
  <!-- EndSection:    'EXAMPLE' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  -->
  
