.. _tee:

tee: Tee the standard output into a file
========================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tee -- tee the standard output to a file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tee file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file' Line='file' -->
  <dd>The name of the output file.
  </dd>
  </dl>
  <dl>
  <dt><b>out_type = <tt>"text"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = "text"' -->
  <dd>The type of output file to be created, either <tt>"text"</tt> or <tt>"binary"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>If set, append to an existing file, otherwise create a new file.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Tee</i> copies its input to both the standard output and the named file.
  Its primary use is in pipes where one wants to capture some intermediate output.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The results of the <i>set</i> command are captured in the file <tt>"temp"</tt>,
  and are also passed on to the <tt>"match"</tt> command.  The result is
  a <tt>"temp"</tt> file of perhaps 100 lines, with the output to the screen
  only around 5 lines.
  </p>
  <p>
  	cl&gt; set | tee temp | match tty
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Since the processes in an IRAF pipe execute serially rather than concurrently,
  the teed output will not appear until all tasks to the left have completed.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
