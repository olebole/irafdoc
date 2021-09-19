.. _aptest:

aptest: Run basic tests on the apphot package tasks
===================================================

**Package: apphot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  aptest -- run basic tests on the apphot package tasks
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  aptest imname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>imname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imname' Line='imname' -->
  <dd>The name of the output test image. The actual test image is stored in fits
  format in the APPHOT package subdirectory test. If the image already exists
  APTEST will exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>aplogfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='aplogfile' Line='aplogfile = ""' -->
  <dd>The name of the output log file. By default all the text output is logged
  in a file called <i>"imname.log"</i>. If the log file already exists APTEST will
  exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>applotfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='applotfile' Line='applotfile = ""' -->
  <dd>The name of the output log file. By default all the plot output is logged in
  a file called <i>"imname.plot"</i>. If the plot file already exists APTEST will
  exit with a warning message.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  APTEST is a simple script which exercises each of the tasks in the APPHOT
  package in turn. At startup APTEST reads a small fits image stored in the
  APPHOT test subdirectory and creates the image <i>imname</i> in the user's
  working directory. APTEST initializes the APPHOT package by returning
  all the parameters to their default state, runs each of the APPHOT
  tasks in non-interactive mode, spools the text output to the file
  <i>aplogfile</i>, and spools the plot output from the RADPROF task to the plot
  metacode file <i>applotfile</i>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Check to see that all the APPHOT tasks are functioning correctly.
  </p>
  <pre>
  	ap&gt; apphot
  
  	... load the apphot package
  
  	ap&gt; aptest testim
  
  	... run the test script
  
  	ap&gt; lprint testim.log
  
  	... print the text output
  
  	ap&gt; gkidir testim.plot
  
  	... list the contents of the plot file
  
  	ap&gt; gkiextract testim.plot 1-N | stdplot
  
  	... send the plots to the plotter
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
