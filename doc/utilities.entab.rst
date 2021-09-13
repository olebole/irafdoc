.. _entab:

entab — Replace blanks with tabs and blanks
===========================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  entab -- replaces blanks by tabs and blanks
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  entab files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>Template specifying the files to be processed, e.g. "<TT>file</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>tablist = "<TT>9 +8</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"'>
  <DD>String containing a list of tabstops separated by blanks or commas.
  A two element string of the form "<TT>m +n</TT>" will set
  tabstops in every n columns beginning in column m.
  A null string defaults to "<TT>9 +8</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Convert the file "<TT>prog.c</TT>", written using full tabstop indents, to
  an equivalent file with an initial indent of one full tabstop, 
  with 4 space indents thereafter.
  <P>
  <PRE>
  	cl&gt; detab prog.c tab='9 +4' | entab &gt; temp
  	cl&gt; delete prog.c
  	cl&gt; rename temp prog.c
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
