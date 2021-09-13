.. _chkconfig:

chkconfig — Check the configuration file for grammar and syntax errors
======================================================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  chkconfig -- Check the grammar and syntax of the configuration file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  chkconfig config
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>config</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='config' Line='config'>
  <DD>The name of the configuration file to be checked. <I>Config</I> is the
  text file specifying both the format of the input files, and the form of
  transformation equations.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print detailed diagnostic information on the standard output ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CHKCONFIG parses the configuration file <I>config</I> line by line,
  searching for syntax and/or semantic errors.  Its primary function is to aid
  the user in setting up a complete and correct set of transformation
  equations to be fit.  CHKCONFIG is run automatically by the task MKCONFIG,
  but can also be run stand-alone at any time.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Check the configuration file for grammar and syntax errors.
  <P>
  <PRE>
  ph&gt; chk config
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkconfig,fitparams
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
