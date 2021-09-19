.. _daotest:

daotest: Run basic tests on the daophot package tasks
=====================================================

**Package: daophot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  daotest -- run basic tests on the daophot package tasks
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  daotest imname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>imname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imname' Line='imname' -->
  <dd>The root name of the output test images. The input test image is stored in
  fits format in the DAOPHOT package test directory. If the image already exists
  DAOTEST will exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>daologfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='daologfile' Line='daologfile = ""' -->
  <dd>The name of the output log file. By default all the output image header
  listings and photometry file output is logged in a file
  called <i>"imname.log"</i>. If the log file already exists DAOTEST will
  exit with a warning message.
  </dd>
  </dl>
  <dl>
  <dt><b>daoplotfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='daoplotfile' Line='daoplotfile = ""' -->
  <dd>The name of the output plot file. By default all the graphics output is
  logged in a file called <i>"imname.plot"</i>. If the plot file already exists
  DAOTEST will exit with a warning message.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  DAOTEST is a simple script which exercises each of the major tasks in the
  DAOPHOT package in turn. At startup DAOTEST reads a small fits image stored
  in the DAOPHOT test subdirectory and creates the image <i>imname</i> in
  the user's working directory. DAOTEST initializes the DAOPHOT package by
  returning
  all the parameters to their default state, runs each of the DAOPHOT
  tasks in non-interactive mode, spools the text output to the file
  <i>daologfile</i>, the graphics output from the PSF task to the plot
  metacode file <i>applotfile</i>, and the image output from PSF, SUBSTAR
  and ADDSTAR to <i>imname.psf.1</i>, <i>imname.sub.1</i>, and <i>imname.add.1</i>
  respectively.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Check to see that all the DAOPHOT tasks are functioning correctly.
  </p>
  <pre>
  	da&gt; daophot
  
  	... load the daophot package
  
  	da&gt; daotest testim
  
  	... run the test script
  
  	da&gt; lprint testim.log
  
  	... print the text output
  
  	da&gt; gkidir testim.plot
  
  	... list the contents of the plot file
  
  	da&gt; gkiextract testim.plot 1-N | stdplot
  
  	... send the plots to the plotter
  
  	da&gt; display testim 1
  
  	... display the original image
  
  	da&gt; surface testim.psf.1
  
  	... make a surface plot of the psf look-up table
  
  	da&gt; display testim.sub.1 1
  
  	... display the image with all the stars fitted by ALLSTAR
  	    subtracted out
  
  	da&gt; display testim.add.1 1
  
  	... display the image  containing three additional artificial
  	    stars added by the ADDSTAR routine
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
  
