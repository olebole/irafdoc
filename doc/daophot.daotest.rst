.. _daotest:

daotest — Run basic tests on the daophot package tasks
======================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  daotest -- run basic tests on the daophot package tasks
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  daotest imname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>imname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imname' Line='imname'>
  <DD>The root name of the output test images. The input test image is stored in
  fits format in the DAOPHOT package test directory. If the image already exists
  DAOTEST will exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>daologfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daologfile' Line='daologfile = ""'>
  <DD>The name of the output log file. By default all the output image header
  listings and photometry file output is logged in a file
  called <I>"imname.log"</I>. If the log file already exists DAOTEST will
  exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>daoplotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daoplotfile' Line='daoplotfile = ""'>
  <DD>The name of the output plot file. By default all the graphics output is
  logged in a file called <I>"imname.plot"</I>. If the plot file already exists
  DAOTEST will exit with a warning message.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  DAOTEST is a simple script which exercises each of the major tasks in the
  DAOPHOT package in turn. At startup DAOTEST reads a small fits image stored
  in the DAOPHOT test subdirectory and creates the image <I>imname</I> in
  the user's working directory. DAOTEST initializes the DAOPHOT package by
  returning
  all the parameters to their default state, runs each of the DAOPHOT
  tasks in non-interactive mode, spools the text output to the file
  <I>daologfile</I>, the graphics output from the PSF task to the plot
  metacode file <I>applotfile</I>, and the image output from PSF, SUBSTAR
  and ADDSTAR to <I>imname.psf.1</I>, <I>imname.sub.1</I>, and <I>imname.add.1</I>
  respectively.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Check to see that all the DAOPHOT tasks are functioning correctly.
  <PRE>
  	da&gt; daophot
  <P>
  	... load the daophot package
  <P>
  	da&gt; daotest testim
  <P>
  	... run the test script
  <P>
  	da&gt; lprint testim.log
  <P>
  	... print the text output
  <P>
  	da&gt; gkidir testim.plot
  <P>
  	... list the contents of the plot file
  <P>
  	da&gt; gkiextract testim.plot 1-N | stdplot
  <P>
  	... send the plots to the plotter
  <P>
  	da&gt; display testim 1
  <P>
  	... display the original image
  <P>
  	da&gt; surface testim.psf.1
  <P>
  	... make a surface plot of the psf look-up table
  <P>
  	da&gt; display testim.sub.1 1
  <P>
  	... display the image with all the stars fitted by ALLSTAR
  	    subtracted out
  <P>
  	da&gt; display testim.add.1 1
  <P>
  	... display the image  containing three additional artificial
  	    stars added by the ADDSTAR routine
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
