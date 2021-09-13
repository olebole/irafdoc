.. _pttest:

pttest — Run basic tests on the ptoolsx package tasks
=====================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pttest -- run basic tests on the ptools package tasks
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pttest rootname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>rootname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rootname' Line='rootname'>
  <DD>The root name of the output test files. The actual test files are stored in
  in the PTOOLS package test directory. If the test files already exist
  PTTEST will exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>ptlogfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ptlogfile' Line='ptlogfile = ""'>
  <DD>The name of the output log file. By default all the output is logged in a file
  called <I>rootname.log"</I>. If the log file already exists PTTEST will
  exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>ptplotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ptplotfile' Line='ptplotfile = ""'>
  <DD>The name of the output plot file. By default all the graphics output is
  logged in a file called <I>rootname.plot"</I>. If the plot file already exists
  PTTEST will exit with a warning message.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PTTEST is a simple script which exercises each of the major tasks in the
  PTOOLS package in turn. At startup PTTEST reads a small set of text files
  stored in the PTOOLS test subdirectory and creates copies of them in
  the user's working directory. PTTEST initializes the PTTOLS package by
  returning
  all the parameters to their default state, runs each of the PTOOLS
  tasks in non-interactive mode, spools the text output to the file
  <I>ptlogfile</I>, and the graphics output from the PEXAMINE task to the plot
  metacode file <I>ptplotfile</I>.
  <P>
  Some of PTOOLS tasks which PTTEST attempts to test are in the STSDAS TABLES
  package. If this package is not available a warning message will appear 
  on the screen and this part of the PTTEST script will be skipped.
  The TABLES external addon package is available from ST. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Check to see that all the PTOOLS tasks are functioning correctly.
  <PRE>
  	da&gt; ptools
  <P>
  	... load the ptools package
  <P>
  	da&gt; pttest testit
  <P>
  	... run the test script
  <P>
  	da&gt; lprint testit.log
  <P>
  	... print the text output
  <P>
  	da&gt; gkidir testit.plot
  <P>
  	... list the contents of the plot file
  <P>
  	da&gt; gkiextract testit.plot 1-N | stdplot
  <P>
  	... send the plots to the plotter
  <P>
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
  tables
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
