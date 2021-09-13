.. _aptest:

aptest — Run basic tests on the apphot package tasks
====================================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aptest -- run basic tests on the apphot package tasks
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aptest imname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>imname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imname' Line='imname'>
  <DD>The name of the output test image. The actual test image is stored in fits
  format in the APPHOT package subdirectory test. If the image already exists
  APTEST will exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>aplogfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aplogfile' Line='aplogfile = ""'>
  <DD>The name of the output log file. By default all the text output is logged
  in a file called <I>"imname.log"</I>. If the log file already exists APTEST will
  exit with a warning message.
  </DD>
  </DL>
  <DL>
  <DT><B>applotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='applotfile' Line='applotfile = ""'>
  <DD>The name of the output log file. By default all the plot output is logged in
  a file called <I>"imname.plot"</I>. If the plot file already exists APTEST will
  exit with a warning message.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  APTEST is a simple script which exercises each of the tasks in the APPHOT
  package in turn. At startup APTEST reads a small fits image stored in the
  APPHOT test subdirectory and creates the image <I>imname</I> in the user's
  working directory. APTEST initializes the APPHOT package by returning
  all the parameters to their default state, runs each of the APPHOT
  tasks in non-interactive mode, spools the text output to the file
  <I>aplogfile</I>, and spools the plot output from the RADPROF task to the plot
  metacode file <I>applotfile</I>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Check to see that all the APPHOT tasks are functioning correctly.
  <P>
  <PRE>
  	ap&gt; apphot
  <P>
  	... load the apphot package
  <P>
  	ap&gt; aptest testim
  <P>
  	... run the test script
  <P>
  	ap&gt; lprint testim.log
  <P>
  	... print the text output
  <P>
  	ap&gt; gkidir testim.plot
  <P>
  	... list the contents of the plot file
  <P>
  	ap&gt; gkiextract testim.plot 1-N | stdplot
  <P>
  	... send the plots to the plotter
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
  
