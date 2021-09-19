.. _pttest:

pttest: Run basic tests on the ptoolsx package tasks
====================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pttest -- run basic tests on the ptools package tasks
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pttest rootname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>rootname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rootname' Line='rootname' -->
  <dd>The root name of the output test files. The actual test files are stored in
  in the PTOOLS package test directory. If the test files already exist
  PTTEST will exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>ptlogfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ptlogfile' Line='ptlogfile = ""' -->
  <dd>The name of the output log file. By default all the output is logged in a file
  called <i>rootname.log"</i>. If the log file already exists PTTEST will
  exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>ptplotfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ptplotfile' Line='ptplotfile = ""' -->
  <dd>The name of the output plot file. By default all the graphics output is
  logged in a file called <i>rootname.plot"</i>. If the plot file already exists
  PTTEST will exit with a warning message.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  PTTEST is a simple script which exercises each of the major tasks in the
  PTOOLS package in turn. At startup PTTEST reads a small set of text files
  stored in the PTOOLS test subdirectory and creates copies of them in
  the user's working directory. PTTEST initializes the PTTOLS package by
  returning
  all the parameters to their default state, runs each of the PTOOLS
  tasks in non-interactive mode, spools the text output to the file
  <i>ptlogfile</i>, and the graphics output from the PEXAMINE task to the plot
  metacode file <i>ptplotfile</i>.
  </p>
  <p>
  Some of PTOOLS tasks which PTTEST attempts to test are in the STSDAS TABLES
  package. If this package is not available a warning message will appear 
  on the screen and this part of the PTTEST script will be skipped.
  The TABLES external addon package is available from ST. 
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Check to see that all the PTOOLS tasks are functioning correctly.
  </p>
  <pre>
  	da&gt; ptools
  
  	... load the ptools package
  
  	da&gt; pttest testit
  
  	... run the test script
  
  	da&gt; lprint testit.log
  
  	... print the text output
  
  	da&gt; gkidir testit.plot
  
  	... list the contents of the plot file
  
  	da&gt; gkiextract testit.plot 1-N | stdplot
  
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
  <p>
  tables
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
