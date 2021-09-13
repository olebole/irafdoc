.. _detab:

detab — Replace tabs with tabs and blanks
=========================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  detab -- remove tab characters from a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  detab files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>Template specifying files to be processed e.g. "<TT>file1</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>tablist = "<TT>9 +8</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"'>
  <DD>String containing a list of tabstops separated by blanks or commas.
  Alternatively a two element string of the form m +n will set
  tabstops every n columns beginning in column m.  A null string will
  default to "<TT>9 +8</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Remove the tabs from file "<TT>cubspl.f</TT>", using the default tab stops.
  <P>
  <PRE>
  	cl&gt; detab cubspl.f &gt; temp
  	cl&gt; delete cubspl.f
  	cl&gt; rename temp cubspl.f
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
